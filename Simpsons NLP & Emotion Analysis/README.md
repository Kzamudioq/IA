@Kzamudioq ¿Qué te parece el repositorio? ¡Está chido! :+1:

<h1 align="center">
  <p align="center">:star: Simpsons NLP & Emotion Analysis :star:</p>
</h1>

`🎷 Hola, soy Lisa Simpson`

"¿Sabías que la inteligencia artificial puede analizar emociones, aprender patrones y hasta tocar jazz? Bueno, tal vez no literalmente, pero está cerca. ¡Déjame explicarte cómo funciona este proyecto!"

<p align="center" width="100%">
    <img width="100%" src="https://github.com/user-attachments/assets/b980cb55-13ad-4208-aa5f-238174e12421"> 
</p>

## 🤖 ¿Qué es la Inteligencia Artificial?

`La inteligencia artificial (IA) es la capacidad de las máquinas para resolver problemas, aprender de los datos y tomar decisiones de manera autónoma, imitando aspectos clave de la inteligencia humana. Pero no, no es magia, ni ciencia ficción. Es matemática, lógica y un poco de jazz computacional.`

La inteligencia artificial no solo se usa para analizar emociones en diálogos ficticios. Estas técnicas también tienen aplicaciones prácticas como:

1. **Análisis de sentimientos en redes sociales:** comprender la percepción del público sobre eventos o marcas.
2. **Mejora de chatbots:** crear asistentes virtuales más empáticos y efectivos.
3. **Clasificación de reseñas:** identificar si un comentario en una tienda online es positivo, negativo o neutral.
4. **Detección temprana de emociones:** en salud mental, analizar patrones en textos que podrían indicar problemas emocionales.

Este proyecto es solo un ejemplo divertido de cómo estas herramientas pueden aplicarse a situaciones más complejas. De esta manera, en el presente ejemplo la IA se aplica al procesamiento del lenguaje natural (NLP) para analizar cómo las emociones se expresan en los diálogos de mi familia. "Sí, incluso Bart tiene emociones... aunque a veces son solo `¡Ay, caramba!` repetido de diferentes maneras."

<p align="center">
    <img src="https://github.com/user-attachments/assets/f68264a5-d6a7-4842-a318-c6b07686d723" alt="bart Simpson GIF" width="100%">
</p>


## 🚀 ¿Qué hace este proyecto?

- **Preprocesamiento de texto:** Limpieza, tokenización, lematización… en otras palabras, convierte el caos en orden (¡algo que mi hermano Bart debería aprender!).
- **Traducción automática:** Transforma nuestros diálogos del inglés al español con la ayuda de `deep-translator`.
- **Análisis de emociones:** Usa `NRCLex`para encontrar sentimientos como alegría, tristeza, enojo y sorpresa. "¿Adivinen cuál predomina en Homero? ¡Pista: no es sorpresa!".
- **Visualización interactiva:** Nubes de palabras y gráficos que explican los resultados de forma elegante, como mis solos de saxofón.

---

## 📊 Datos del Proyecto

El análisis utiliza un dataset basado en los diálogos de **Los Simpson**, con líneas de texto y descripciones de escenas. A continuación, se describen las columnas principales del dataset:

1. **`id`:** Identificador único de cada línea de diálogo o descripción.
2. **`episode_id`:** Número del episodio al que pertenece la línea.
3. **`number`:** Orden de la línea dentro del episodio.
4. **`raw_text`:** El contenido del diálogo o descripción.

---

### **Ejemplo de las primeras líneas:**
| **id** | **episode_id** | **number** | **raw_text**                                                                                             |
|--------|----------------|------------|---------------------------------------------------------------------------------------------------------|
| 9549   | 32             | 209        | Miss Hoover: No, actually, it was a little of both. Sometimes when a disease is in all the magazines... |
| 9550   | 32             | 210        | Lisa Simpson: (NEAR TEARS) Where's Mr. Bergstrom?                                                      |
| 9551   | 32             | 211        | Miss Hoover: I don't know. Although I'd sure like to talk to him. He didn't touch my lesson plan...    |
| 9552   | 32             | 212        | Lisa Simpson: That life is worth living.                                                               |
| 9553   | 32             | 213        | Edna Krabappel-Flanders: The polls will be open from now until the end of recess...                     |

---

### **Transformaciones realizadas en los datos:**
Durante el análisis, el dataset se preprocesa para:
- **Limpiar:** Se eliminan caracteres innecesarios y palabras vacías.
- **Traducir:** Los diálogos se convierten del inglés al español.
- **Tokenizar y lematizar:** Se dividen las frases en palabras y se extraen sus raíces gramaticales.

Estos pasos garantizan que la inteligencia artificial pueda procesar el texto de manera eficiente para identificar emociones y patrones.

---

## 📁 Estructura del Repositorio

"Todo buen proyecto debe ser tan organizado como mi estantería de libros. ¡Aquí tienes cómo está estructurado este!"

```plaintext
Simpsons-NLP-Emotion-Analysis/
├── notebooks/                   # Contiene el notebook principal de Colab
├── data/                        # Archivos de datos utilizados
├── images/                      # Resultados visuales generados
├── README.md                    # Documentación principal
├── requirements.txt             # Lista de dependencias
├── LICENSE                      # Licencia del proyecto
```

## 💻 Uso del Proyecto

### Clonar el repositorio:
```bash
git clone https://github.com/tuusuario/Simpsons-NLP-Emotion-Analysis.git
cd Simpsons-NLP-Emotion-Analysis
```
### Subir archivos a Google Drive

1. Sube el contenido de la carpeta data/ a tu Google Drive.
2. Abre el notebook notebooks/simpsons_emotion_analysis.ipynb en Google Colab.

### Configurar entorno en Colab

Ejecuta las celdas de instalación y configuración del notebook para cargar dependencias y datos.

### Ejecutar el análisis

"Prepárate para descubrir secretos escondidos en las palabras de mi familia. Solo sigue las celdas para hacer lo siguiente:"

- Preprocesar los datos.
- Realizar traducciones.
- Analizar emociones.
- Generar visualizaciones interactivas.

## 🚀 Resultados ejemplo

- Nube de Palabras: Bart
"Mis primeras palabras fueron 'Ay, caramba', ¡y aquí está la prueba!"

- Análisis de Emociones: Lisa

"¿Sabías que mis diálogos tienen más confianza y alegría que los de cualquiera? ¡Soy la voz de la razón en esta familia!"

## 🛠️ Tecnologías

- Procesamiento de Lenguaje Natural (NLP): nltk, NRCLex
- Visualización: matplotlib, seaborn, wordcloud
- Traducción: deep-translator
- Entorno: Google Colab


## 📜 Contribuciones

"Siempre estoy abierta a nuevas ideas, especialmente si son tan brillantes como yo. ¡Si tienes mejoras, no dudes en colaborar!"

Este código en Markdown está listo para ser incluido en el archivo `README.md` de tu proyecto en GitHub. Simplemente ajusta la URL del repositorio en el comando `git clone` si es necesario.


