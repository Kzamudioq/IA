<h1 align="center">
  <p align="center">:star: Análisis de Lenguaje y Emociones en Los Simpson :star:</p>
</h1>

`🎷 Hola, soy Lisa Simpson`

"¿Sabías que la inteligencia artificial puede analizar emociones, aprender patrones y hasta tocar jazz? Bueno, tal vez no literalmente, pero está cerca. ¡Déjame explicarte cómo funciona este proyecto!"

<p align="center" width="100%">
    <img width="100%" src="https://github.com/user-attachments/assets/b980cb55-13ad-4208-aa5f-238174e12421"> 
</p>

---

## 🤖 ¿Qué es la Inteligencia Artificial?

La inteligencia artificial (IA) es la capacidad de las máquinas para resolver problemas, <span title="El aprendizaje es clave en la IA: las máquinas identifican patrones a partir de datos para mejorar su desempeño." style="color:yellow;">**aprender**</span> de los datos y tomar decisiones de manera autónoma, imitando aspectos clave de la inteligencia humana. Pero no, no es magia, ni ciencia ficción. Es <span title="La matemática proporciona la base para modelos, algoritmos y cálculos precisos en la IA." style="color:yellow;">**matemática**</span>, <span title="La lógica es el estudio del razonamiento válido, que se utiliza para estructurar procesos de decisión y análisis en IA." style="color:yellow;">**lógica**</span> y un poco de <span title="El jazz computacional es una metáfora para expresar cómo la IA puede improvisar dentro de ciertas reglas." style="color:yellow;">**jazz computacional**</span>.

---

## 🌍 Aplicaciones prácticas

1. **<span title="Analizar publicaciones y comentarios en redes sociales permite entender opiniones y emociones predominantes." style="color:yellow;">Análisis de sentimientos en redes sociales</span>:**
   - Comprender la percepción del público sobre eventos o marcas.
2. **<span title="Los chatbots modernos utilizan IA para interactuar de manera natural y resolver problemas en tiempo real." style="color:yellow;">Mejora de chatbots</span>:**
   - Crear asistentes virtuales más empáticos y efectivos.
3. **<span title="Clasificar reseñas ayuda a las empresas a priorizar problemas o destacar puntos positivos en sus servicios." style="color:yellow;">Clasificación de reseñas</span>:**
   - Identificar si un comentario en una tienda online es positivo, negativo o neutral.
4. **<span title="En salud mental, la IA puede analizar textos en busca de patrones que sugieran emociones o estados críticos." style="color:yellow;">Detección temprana de emociones</span>:**
   - Analizar patrones en textos para identificar problemas emocionales.

---

## 🚀 ¿Qué hace este proyecto?

Este proyecto aplica **procesamiento del lenguaje natural (NLP)** para analizar cómo las emociones se expresan en los diálogos de mi familia. "Incluso Bart tiene emociones... aunque a veces son solo `¡Ay, caramba!` repetido de diferentes maneras."

<p align="center">
    <img src="https://github.com/user-attachments/assets/f68264a5-d6a7-4842-a318-c6b07686d723" alt="bart Simpson GIF" width="100%">
</p>

### **Características principales:**

- **Preprocesamiento de texto:** Limpieza, tokenización y lematización.
- **Traducción automática:** Transforma diálogos del inglés al español.
- **Análisis de emociones:** Encuentra sentimientos como alegría, tristeza, enojo y sorpresa.
- **Visualización interactiva:** Nubes de palabras y gráficos.

---

## 📊 Datos del Proyecto

### **Descripción del dataset:**

| **Columna**      | **Descripción**                                                                  |
|-------------------|----------------------------------------------------------------------------------|
| `id`             | Identificador único de cada línea de diálogo o descripción.                      |
| `episode_id`     | Número del episodio al que pertenece la línea.                                   |
| `number`         | Orden de la línea dentro del episodio.                                           |
| `raw_text`       | El contenido del diálogo o descripción.                                          |

---

### **Ejemplo de las primeras líneas:**

| **id** | **episode_id** | **number** | **raw_text**                                                                                             |
|--------|----------------|------------|---------------------------------------------------------------------------------------------------------|
| 9549   | 32             | 209        | Miss Hoover: No, actually, it was a little of both. Sometimes when a disease is in all the magazines... |
| 9550   | 32             | 210        | Lisa Simpson: (NEAR TEARS) Where's Mr. Bergstrom?                                                      |

---

### **Transformaciones realizadas en los datos:**

#### 1. **Limpieza**
Eliminación de caracteres no alfabéticos y palabras vacías.

#### 2. **Tokenización**
División de frases en palabras o signos de puntuación.

#### 3. **Lematización**
Conversión de palabras a su forma base.

```plaintext
Texto original: "Lisa Simpson está aprendiendo inteligencia artificial."
Tokens: ["Lisa", "Simpson", "está", "aprendiendo", "inteligencia", "artificial", "."]
Tokens lematizados: ["Lisa", "Simpson", "estar", "aprender", "inteligencia", "artificial", "."]
```
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


