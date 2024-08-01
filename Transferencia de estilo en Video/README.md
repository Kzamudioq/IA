@Kzamudioq ¿Qué te parece el repositorio? ¡Está chido! :+1:

<h1 align="center">
  <p align="center">🍌 Transferencia de estilo en video 🐒</p>
</h1>

¡Hola! Bienvenidos a nuestro super proyecto de transferencia de estilo neuronal, donde tomamos imágenes y les damos un toque artístico al estilo de una obra maestra. ¡Es como si Phineas y Ferb hubieran decidido transformar tus fotos en arte mientras construyen un cohete para la luna!


<p align="center" width="100%">
    <img width="60%" src="https://github.com/user-attachments/assets/21474f00-d694-4a0c-ace2-79d5b5dd27bb"> 
</p>

## 🚀 **¿Qué Hace Este Proyecto?**

Este proyecto utiliza redes neuronales para aplicar un estilo artístico a tus imágenes, ¡y luego convierte el proceso en un video! Así que en lugar de ver un solo resultado, podrás ver cómo tu imagen se transforma gradualmente en una obra de arte. ¡Imagina una secuencia de video donde tu foto pasa de normal a espectacular!

## 🛠 **¿Cómo Funciona?**

1. **Cargar Imágenes:**
   Cargamos las imágenes de contenido y estilo que deseas combinar. ¡Es como elegir tu foto favorita y el estilo de tu pintor preferido!

2. **Definir el Modelo:**
   Usamos VGG19, un modelo preentrenado que es como tener un experto en arte en tu equipo. Extraemos características tanto del contenido como del estilo de las imágenes.

3. **Transferencia de Estilo:**
   Aplicamos un algoritmo que toma el contenido de una imagen y el estilo de otra, combinándolos en una imagen de salida. ¡Es como mezclar la esencia de Van Gogh con tu selfie!

4. **Generar el Video:**
   Guardamos cada iteración del proceso de transferencia de estilo y las combinamos en un video. ¡Así podrás ver la magia del arte en acción!

## 🎬 **¡Cómo Empezar!**

Para ejecutar el código en Google Colab, sigue estos pasos:

1. **Configuración Inicial:**
      Asegúrate de instalar las librerías necesarias:

```python
!pip install tensorflow numpy matplotlib
```
2. **Importar Librerías:**

```python
import tensorflow as tf
import numpy as np
import matplotlib.pyplot as plt
from tensorflow.keras.applications import VGG19
from tensorflow.keras.preprocessing import image as kp_image
from tensorflow.keras.models import Model
from tensorflow.keras import backend as K
import cv2

```
3. **Definir capas de estilo y contenido:**

```python
style_layers = ['block1_conv1', 'block2_conv1', 'block3_conv1', 'block4_conv1', 'block5_conv1']
content_layers = ['block5_conv2']
num_style_layers = len(style_layers)
num_content_layers = len(content_layers)
```

4. **Funciones auxiliares:**
   Define las funciones para cargar imágenes, procesarlas y mostrar resultados.

```python
def load_and_process_img(path_to_img):
    img = kp_image.load_img(path_to_img)
    img = kp_image.img_to_array(img)
    img = np.expand_dims(img, axis=0)
    img = tf.keras.applications.vgg19.preprocess_input(img)
    return img

def deprocess_img(processed_img):
    x = processed_img.copy()
    if len(x.shape) == 4:
        x = np.squeeze(x, 0)
    x[:, :, 0] += 103.939
    x[:, :, 1] += 116.779
    x[:, :, 2] += 123.68
    x = x[:, :, ::-1]
    x = np.clip(x, 0, 255).astype('uint8')
    return x

def show_img(img, title=None):
    if len(img.shape) == 4:
        img = np.squeeze(img, 0)
    img = deprocess_img(img)
    plt.imshow(img)
    if title:
        plt.title(title)
    plt.show()

```

5. **Definir el modelo:**

```python
def get_model():
    vgg = VGG19(include_top=False, weights='imagenet')
    vgg.trainable = False
    selected_layers = style_layers + content_layers
    outputs = [vgg.get_layer(name).output for name in selected_layers]
    model = Model([vgg.input], outputs)
    return model

def get_feature_representations(model, content_path, style_path):
    content_image = load_and_process_img(content_path)
    style_image = load_and_process_img(style_path)
    
    style_outputs = model(style_image)
    content_outputs = model(content_image)
    
    style_features = [style_layer[0] for style_layer in style_outputs[:num_style_layers]]
    content_features = [content_layer[0] for content_layer in content_outputs[num_style_layers:]]
    
    return style_features, content_features

```

6. **Definir las funciones de pérdida y el algoritmo de optimización:**

```python
def compute_content_loss(base_content, target):
    return tf.reduce_mean(tf.square(base_content - target))

def gram_matrix(input_tensor):
    channels = int(input_tensor.shape[-1])
    a = tf.reshape(input_tensor, [-1, channels])
    n = tf.shape(a)[0]
    gram = tf.matmul(a, a, transpose_a=True)
    return gram / tf.cast(n, tf.float32)

def compute_style_loss(base_style, gram_target):
    height, width, channels = base_style.get_shape().as_list()
    gram_style = gram_matrix(base_style)
    
    return tf.reduce_mean(tf.square(gram_style - gram_target))

def compute_loss(model, loss_weights, init_image, gram_style_features, content_features):
    style_weight, content_weight = loss_weights
    
    model_outputs = model(init_image)
    
    style_output_features = model_outputs[:num_style_layers]
    content_output_features = model_outputs[num_style_layers:]
    
    style_score = 0
    content_score = 0
    
    weight_per_style_layer = 1.0 / float(num_style_layers)
    for target_style, comb_style in zip(gram_style_features, style_output_features):
        style_score += weight_per_style_layer * compute_style_loss(comb_style[0], target_style)
    
    weight_per_content_layer = 1.0 / float(num_content_layers)
    for target_content, comb_content in zip(content_features, content_output_features):
        content_score += weight_per_content_layer * compute_content_loss(comb_content[0], target_content)
    
    style_score *= style_weight
    content_score *= content_weight
    
    loss = style_score + content_score
    return loss, style_score, content_score

@tf.function()
def compute_grads(cfg):
    with tf.GradientTape() as tape: 
        all_loss = compute_loss(**cfg)
    total_loss = all_loss[0]
    return tape.gradient(total_loss, cfg['init_image']), all_loss

```

7. **Ejecutar la transferencia de estilo:**

```python
def run_style_transfer(content_path, style_path, num_iterations=1000, content_weight=1e3, style_weight=1e-2): 
    model = get_model() 
    for layer in model.layers:
        layer.trainable = False
        
    style_features, content_features = get_feature_representations(model, content_path, style_path)
    gram_style_features = [gram_matrix(style_feature) for style_feature in style_features]
    
    init_image = load_and_process_img(content_path)
    init_image = tf.Variable(init_image, dtype=tf.float32)
    
    opt = tf.keras.optimizers.Adam(learning_rate=5.0, beta_1=0.99, epsilon=1e-1)
    
    iter_count = 1
    best_loss, best_img = float('inf'), None
    
    loss_weights = (style_weight, content_weight)
    cfg = {
        'model': model,
        'loss_weights': loss_weights,
        'init_image': init_image,
        'gram_style_features': gram_style_features,
        'content_features': content_features
    }
    
    norm_means = np.array([103.939, 116.779, 123.68])
    min_vals = -norm_means
    max_vals = 255 - norm_means   
    
    for i in range(num_iterations):
        grads, all_loss = compute_grads(cfg)
        loss, style_score, content_score = all_loss
        opt.apply_gradients([(grads, init_image)])
        clipped = tf.clip_by_value(init_image, min_vals, max_vals)
        init_image.assign(clipped)
        
        if loss < best_loss:
            best_loss = loss
            best_img = deprocess_img(init_image.numpy())
        
        if i % 100 == 0:
            print('Iteration: {}'.format(i))        
            print('Total loss: {:.4e}, style loss: {:.4e}, content loss: {:.4e}'.format(loss, style_score, content_score))
            
    return best_img, best_loss
```

7. **Generar el video:**

```python
def create_video(content_path, style_path, num_iterations=1000, video_filename='output_video.mp4'):
    fourcc = cv2.VideoWriter_fourcc(*'mp4v')
    height, width, _ = load_and_process_img(content_path).shape[1:]
    video = cv2.VideoWriter(video_filename, fourcc, 20.0, (width, height))
    
    model = get_model()
    for layer in model.layers:
        layer.trainable = False
    
    style_features, content_features = get_feature_representations(model, content_path, style_path)
    gram_style_features = [gram_matrix(style_feature) for style_feature in style_features]
    
    init_image = load_and_process_img(content_path)
    init_image = tf.Variable(init_image, dtype=tf.float32)
    
    opt = tf.keras.optimizers.Adam(learning_rate=5.0, beta_1=0.99, epsilon=1e-1)
    
    loss_weights = (1e-2, 1e3)
    cfg = {
        'model': model,
        'loss_weights': loss_weights,
        'init_image': init_image,
        'gram_style_features': gram_style_features,
        'content_features': content_features
    }
    
    norm_means = np.array([103.939, 116.779, 123.68])
    min_vals = -norm_means
    max_vals = 255 - norm_means   
    
    for i in range(num_iterations):
        grads, all_loss = compute_grads(cfg)
        loss, style_score, content_score = all_loss
        opt.apply_gradients([(grads, init_image)])
        clipped = tf.clip_by_value(init_image, min_vals, max_vals)
        init_image.assign(clipped)
        
        if i % 10 == 0:  # Guardar una imagen cada 10 iteraciones
            frame = deprocess_img(init_image.numpy())
            video.write(cv2.cvtColor(frame, cv2.COLOR_RGB2BGR))
        
        if i % 100 == 0:
            print('Iteration: {}'.format(i))
            print('Total loss: {:.4e}, style loss: {:.4e}, content loss: {:.4e}'.format(loss, style_score, content_score))
    
    video.release()

```

## 🚀 ¡Únete a la Diversión! 🚀

Si tienes alguna pregunta o sugerencia, ¡no dudes en abrir un "issue"! Y si te sientes aventurero, contribuye al proyecto para hacerlo aún más increíble. ¡Gracias por ser parte de esta aventura artística!

<p align="center" width="100%">
    <img width="60%" src="https://github.com/user-attachments/assets/c798c172-1f0e-47ec-a16d-df31124952df"> 
</p>

## 🚀 ¡Licencia! 🚀

Este proyecto está licenciado bajo la MIT License. ¡Siéntete libre de usar, modificar y compartir! 

