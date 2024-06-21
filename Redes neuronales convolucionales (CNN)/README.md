@Kzamudioq ¿Qué te parece el repositorio? ¡Está chido! :+1:

<h1 align="center">
  <p align="center">:star:  Clasificador de Imágenes con Redes Neuronales Convolucionales (CNN) :star:</p>
</h1>

¡Bello! ¡Bienvenido a nuestro proyecto de clasificación de imágenes usando redes neuronales convolucionales (CNN)! 🚀🎉


## ¿Qué son las Redes Neuronales Convolucionales (CNN)? 🤔📚

Las Redes Neuronales Convolucionales (CNN) son un tipo de red neuronal especialmente efectiva para procesar datos con una estructura de cuadrícula, como las imágenes. 🍌🎨

### ¿Cómo funcionan? 🧐🔬

1. **Capas Convolucionales**: Detectan características locales de la imagen, como bordes y texturas, aplicando filtros de convolución. 🕵️‍♂️🔍
2. **Capas de Pooling**: Reducen la dimensionalidad de los datos, manteniendo las características más importantes. Es como hacer zoom out en la imagen. 📉🔍
3. **Capas Densas**: Conectan todas las neuronas y permiten la clasificación final de la imagen. 🤝🔗

## Nuestro Proyecto 🎯🏗️

Vamos a entrenar un modelo CNN para clasificar imágenes de dígitos escritos a mano usando el famoso conjunto de datos MNIST. ✏️🔢

## Código del Proyecto 📝🐼

```python
# Instalación de TensorFlow (si no está instalado)
!pip install tensorflow

# Importar las librerías necesarias
import tensorflow as tf
from tensorflow.keras import layers, models
import matplotlib.pyplot as plt
import numpy as np

# Cargar el conjunto de datos MNIST (números escritos a mano)
mnist = tf.keras.datasets.mnist
(train_images, train_labels), (test_images, test_labels) = mnist.load_data()

# Normalizar las imágenes
train_images, test_images = train_images / 255.0, test_images / 255.0

# Definir el modelo de red neuronal convolucional
model = models.Sequential([
    layers.Conv2D(32, (3, 3), activation='relu', input_shape=(28, 28, 1)),
    layers.MaxPooling2D((2, 2)),
    layers.Conv2D(64, (3, 3), activation='relu'),
    layers.MaxPooling2D((2, 2)),
    layers.Conv2D(64, (3, 3), activation='relu'),
    layers.Flatten(),
    layers.Dense(64, activation='relu'),
    layers.Dense(10, activation='softmax')
])

# Compilar el modelo
model.compile(optimizer='adam',
              loss='sparse_categorical_crossentropy',
              metrics=['accuracy'])

# Añadir una dimensión para el canal de color (escala de grises)
train_images = train_images[..., np.newaxis]
test_images = test_images[..., np.newaxis]

# Entrenar el modelo
history = model.fit(train_images, train_labels, epochs=5, 
                    validation_data=(test_images, test_labels))

# Evaluar el modelo
test_loss, test_acc = model.evaluate(test_images, test_labels)

print('Test accuracy:', test_acc)

# Función para mostrar imágenes y predicciones
def plot_image(i, predictions_array, true_label, img):
    predictions_array, true_label, img = predictions_array[i], true_label[i], img[i]
    plt.grid(False)
    plt.xticks([])
    plt.yticks([])

    plt.imshow(img, cmap=plt.cm.binary)

    predicted_label = np.argmax(predictions_array)
    if predicted_label == true_label:
        color = 'blue'
    else:
        color = 'red'

    plt.xlabel("{} {:2.0f}% ({})".format(predicted_label,
                                         100 * np.max(predictions_array),
                                         true_label),
               color=color)

# Mostrar una imagen con sus predicciones
def plot_value_array(i, predictions_array, true_label):
    predictions_array, true_label = predictions_array[i], true_label[i]
    plt.grid(False)
    plt.xticks(range(10))
    plt.yticks([])
    thisplot = plt.bar(range(10), predictions_array, color="#777777")
    plt.ylim([0, 1])
    predicted_label = np.argmax(predictions_array)

    thisplot[predicted_label].set_color('red')
    thisplot[true_label].set_color('blue')

# Hacer predicciones
predictions = model.predict(test_images)

# Seleccionar una imagen de prueba
img_index = 0
plt.figure(figsize=(6,3))
plt.subplot(1,2,1)
plot_image(img_index, predictions, test_labels, test_images.squeeze())
plt.subplot(1,2,2)
plot_value_array(img_index, predictions,  test_labels)
plt.show()
```

## Pasos para ejecutar el código 🏃‍♂️💻

1. **Instalar TensorFlow**: ejecuta !pip install tensorflow para instalar TensorFlow en tu entorno Colab. 🛠️
2. **Importar librerías**: importa las librerías necesarias con import tensorflow as tf y otros. 📦
3. **Cargar y Normalizar Datos**: carga el conjunto de datos MNIST y normaliza las imágenes dividiendo por 255. 📊
4.  **Definir y compilar el modelo**: crea el modelo CNN usando tf.keras.models.Sequential y compílalo. 🏗️
5. **Entrenar el modelo**: entrena el modelo con model.fit por 5 épocas. 🏋️‍♂️
6. **Evaluar el modelo**: evalúa el rendimiento del modelo en datos de prueba. 📈
7. **Visualizar predicciones:**: usa funciones de matplotlib para mostrar predicciones y ver qué tan bien clasifica los dígitos. 👀


# ¡Diviértete aprendiendo y creando con IA! 
¡Espero que este `README.md` te sea útil y divertido para tu proyecto! 😄🎬

