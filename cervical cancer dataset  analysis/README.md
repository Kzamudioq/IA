# <p align="center">🌙 Repositorio de cervical cancer risk factors analysis 🤖</p>


---

¡Bienvenido al asombroso mundo de la detección mágica de objetos con 🤖 IA, donde la magia y el código se encuentran para crear algo increíble! 🌟

<p align="center" width="100%">
    <img width="60%" src="https://github.com/Kzamudioq/IA/assets/138271936/94d4e51e-2ba4-4ca8-973d-9d153c5d3cf8"> 
</p>

Este repositorio contiene un análisis detallado de los factores de riesgo para el cáncer cervical utilizando un conjunto de datos obtenido del UCI Repository y Kaggle.

/notebooks
    ├── 01_Exploracion_Datos.ipynb
    ├── 02_Transformacion_Variables.ipynb
    ├── 03_Analisis_Correlacion.ipynb
    ├── 04_Modelado_Evaluacion.ipynb
    ├── 05_Manejo_Datos_Desbalanceados.ipynb
    ├── 06_Validacion_Cruzada.ipynb

## Contenido

1. Exploración de Datos
2. Transformación de Variables
3. Análisis de Correlación
4. Modelado y Evaluación
5. Manejo de Datos Desbalanceados
6. Validación Cruzada

## ✨ Descripción ✨
Imagina un mundo donde las máquinas pueden detectar objetos mágicamente utilizando plantillas. ¿Suena a ciencia ficción? ¡Pues aquí lo hacemos realidad!, poco a poco, estos es solo los primeros pasos.

## ¿Qué Hace ? 🧙‍♂️

Para acer esto posible se implementa la poderosa técnica de "template matching" en OpenCV para detectar objetos en imágenes. Imagina que la IA tiene ojos mágicos que buscan patrones específicos en las imágenes para decirte dónde se esconde la magia. 🔍✨

## ¿Qué es OpenCV? 

<p align="center" width="50%">
    <img width="20%" src="https://github.com/Kzamudioq/IA/assets/138271936/e7194f2a-81fc-438b-8fd6-aa7f706df453"> 
</p>


OpenCV, o Open Source Computer Vision Library, es una biblioteca de visión por computadora de código abierto. En este tranquilo rincón, OpenCV se convierte en una varita mágica que permite a la IA ver y entender el mundo visual.

## ¿Qué es "Template Matching"? 🧩

La técnica de "template matching" es como tener un rompecabezas mágico. Imagina que tienes una pieza especial (una plantilla) y deseas encontrar dónde encaja en una imagen más grande. Este hechizo utiliza esa plantilla para buscar coincidencias en la imagen y encontrar dónde se oculta el objeto mágico.

## Funciones Mágicas ✨
### `load_and_preprocess_template(template_path)`
Carga y preprocesa la plantilla utilizada para la detección de objetos.

<p align="center" width="50%">
    <img width="50%" src="https://github.com/Kzamudioq/IA/assets/138271936/37a57c80-29da-4af3-8658-1e16ad367278"> 
</p>


### `object_detection(image_path, template_edges, template_size, confidence_threshold=70)`
Realiza la detección de objetos en una imagen utilizando la técnica de "template matching". Devuelve las coordenadas del objeto detectado si supera el umbral de confianza.

### `visualize_result(image, x_start, y_start, x_end, y_end)`
Visualiza el resultado de la detección dibujando un rectángulo alrededor del objeto detectado.

----

## ¿Qué Resultados Esperar? 
Este cuaderno te mostrará un mapa de la serenidad, donde un rectángulo tranquilo te indicará dónde se encuentra el objeto mágico. Y si no hay coincidencias, la calma te dirá que no hubo detecciones con el umbral especificado.

<p align="center" width="50%">
    <img width="50%" src="https://github.com/Kzamudioq/IA/assets/138271936/ffc12696-3f49-439b-b957-4c943f07e407"> 
</p>

### Características 
- 📏 **Invariante a Escala:** este codigo es como el sol que siempre sale. Es invariante a escala, lo que significa que puede detectar objetos incluso si cambian de tamaño en la imagen.

- 🕵️‍♂️ **Detecta un Objeto por Imagen:** como un observador zen, este hechizo se enfoca en un objeto a la vez. Solo detectará el objeto más dominante en la imagen.


## Ventajas 
- 🌙 **Fácil de Usar:** No necesitas ser un mago del código. Con unos clics, podrás usar esta herramienta tranquila.
- 🌿 **Versátil:** Detecta desde mariposas en el jardín hasta luces de luciérnagas en tus imágenes.

## Desventajas🧘‍♂️
- 🌊 **Dependiente de Plantillas:** Al igual que en un jardín zen, necesita de sus herramientas. Este código depende de tener una plantilla para buscar en las imágenes.

-----

## Relación con la IA 🌌
Este cuaderno tiene una conexión especial con la IA, donde la serenidad se encuentra con la inteligencia. Utiliza técnicas que harían sonreír a las inteligencias artificiales más avanzadas. ¡Imagina a Siri meditando mientras hace esto!

## Teorías🍀
Se rumorea que este código es la base para enseñar a los robots a detectar objetos amigables en el mundo. 🌍🤖 ¡Pero no te preocupes, aún estamos los primeros pasos para detectar objetos !


