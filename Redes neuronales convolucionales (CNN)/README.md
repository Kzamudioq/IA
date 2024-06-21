@Kzamudioq ¿Qué te parece el repositorio? ¡Está chido! :+1:

<h1 align="center">
  <p align="center">:star: Sistema de preguntas y respuestas con BERT! :star:</p>
</h1>


`¡Hola, soy Stuart Minions!`

¡Hola, minions! 👋 Este repositorio tiene una forma divertida de hacer que la computadora responda preguntas usando BERT, que es una tecnología muy avanzada (¡más avanzada que las bananas! 🍌). Usamos la biblioteca `transformers` de Hugging Face y un modelo BERT que ya ha sido entrenado con muchas preguntas y respuestas del conjunto de datos SQuAD.


<p align="center" width="100%">
    <img width="60%" src="https://github.com/Kzamudioq/IA/assets/138271936/62b8018f-e03e-447e-abea-1802d3417ff7"> 
</p>


## 📚 Tabla de Contenidos

- [🚀 Instalación](#🚀-instalación)
- [🛠️ Uso](#🛠️-uso)
- [🔍 Funcionalidad](#🔍-funcionalidad)
- [📝 Ejemplos](#📝-ejemplos)
- [📜 Licencia](#📜-licencia)

## 🚀 Instalación

Primero, necesitamos instalar algunas cosas para que todo funcione. ¡Usa este comando mágico! 🪄

```python
pip install torch transformers
```

## 🛠️ Uso
Aquí te mostramos cómo usar este sistema para hacer preguntas y obtener respuestas. ¡Es como magia! ✨

### Inicializando el tokenizador y el modelo

Primero, necesitamos iniciar nuestro modelo de BERT y el tokenizador (que es como un traductor para que BERT entienda nuestras preguntas) 📖:

```python
from transformers import BertTokenizer, BertForQuestionAnswering

tokenizer = BertTokenizer.from_pretrained("bert-large-uncased-whole-word-masking-finetuned-squad")
model = BertForQuestionAnswering.from_pretrained("bert-large-uncased-whole-word-masking-finetuned-squad")
```
### Definiendo la función de preguntas y respuestas

Ahora, definimos una función especial que tomará nuestra pregunta y el contexto y nos dará una respuesta 💡:

```python
import torch

def ask_question(question, context):
    inputs = tokenizer.encode_plus(question, context, return_tensors="pt", add_special_tokens=True)
    input_ids = inputs["input_ids"].tolist()[0]

    outputs = model(**inputs)
    start_scores = outputs.start_logits
    end_scores = outputs.end_logits

    answer_start = torch.argmax(start_scores)
    answer_end = torch.argmax(end_scores) + 1

    answer = tokenizer.convert_tokens_to_string(tokenizer.convert_ids_to_tokens(input_ids[answer_start:answer_end]))
    return answer

```
## 🔍 Funcionalidad

Este sistema usa BERT para encontrar respuestas en un texto dado. La función ask_question toma una pregunta y un contexto y devuelve una respuesta que BERT encuentra en el contexto. 🤖

## 📝 Ejemplos

¡Ahora vamos a jugar con algunos ejemplos! 🎉

### Ejemplo 1: Aprendizaje Automático 🤖

```python
context = """
El aprendizaje automático es una rama de la inteligencia artificial (IA) que permite a las computadoras aprender sin ser programadas explícitamente.
El aprendizaje automático supervisado utiliza datos etiquetados para entrenar algoritmos, mientras que el aprendizaje no supervisado trabaja con datos no etiquetados.
En el aprendizaje supervisado, los ejemplos de entrenamiento incluyen tanto las entradas como las salidas deseadas, y el algoritmo aprende a mapear las entradas a las salidas.
Ejemplos comunes de algoritmos de aprendizaje automático supervisado incluyen regresión lineal, máquinas de vectores de soporte (SVM), y redes neuronales.
"""

question = "¿Qué es el aprendizaje automático?"
answer = ask_question(question, context)
print("Respuesta del chatbot:", answer)

# Salida: una rama de la inteligencia artificial ( ia ) que permite a las computadoras aprender sin ser programadas explicitamente
```

### Ejemplo 2: Cambio Climático 🌍

<p align="center" width="100%">
    <img width="40%" src="https://github.com/Kzamudioq/IA/assets/138271936/063935b9-5184-4620-a3e7-98d315a1a6a7"> 
</p>

```python
context = """
El cambio climático se refiere a los cambios significativos y duraderos en los patrones del clima global.
Es un problema complejo que involucra varias causas entre ellas el aumento de las concentraciones de gases de efecto invernadero en la atmósfera debido a actividades humanas como la quema de combustibles fósiles y la deforestación.
Estos gases atrapan el calor en la atmósfera, lo que lleva al calentamiento global.
El cambio climático puede resultar en eventos meteorológicos extremos, cambios en los patrones de lluvia, y aumento del nivel del mar, afectando a ecosistemas y comunidades humanas en todo el mundo.
Las acciones para mitigar el cambio climático incluyen la reducción de las emisiones de gases de efecto invernadero, el uso de fuentes de energía renovable, y la mejora de la eficiencia energética.
"""

question = "¿Qué es el cambio climático?"
answer = ask_question(question, context)
print("Respuesta del chatbot:", answer)

# Salida: un problema complejo que involucra varias causas

```

## 📜 Licencia

Este proyecto está licenciado bajo la Licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles. 📄


¡Y así es como los minions pueden usar el sistema de preguntas y respuestas con BERT! ¡Banana! 🍌

