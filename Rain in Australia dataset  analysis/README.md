@Kzamudioq ¿Qué te parece el repositorio? ¡Está chido! :+1:

<h1 align="center">
  <p align="center">:star: Bart Simpson te guía: Repositorio de predicción del clima en Australia, Man! :star:</p>
</h1>


`¡Hola, soy Bart Simpson!`

¡Bienvenidos al Repositorio del Análisis de Riesgo de Cáncer Cervical!

<p align="center" width="100%">
    <img width="60%" src="https://github.com/Kzamudioq/IA/assets/138271936/71d33894-4482-40a6-9848-3cac38c7bdd1"> 
</p>

¡Ey, man! Bienvenido a este proyecto loco donde estamos tratando de predecir el clima en Australia, mediate una base de datos extensa. Prepárate para una aventura salvaje en el mundo de los datos y los modelos de aprendizaje automático. ¡Es como una montaña rusa, pero para tus neuronas!

## 🧠 **¿Qué Rayos es Este Proyecto?** 


Aquí tienes la primicia: estamos tratando de ser los más listos de la clase prediciendo el clima. Estamos usando datos de los aeropuertos de Australia y alimentándolos a nuestros modelos de aprendizaje automático para ver si pueden adivinar qué tiempo va a hacer el dia de mañana. ¡Es como una apuesta, pero con datos!


💡 **Características Molonas** 💡

Vamos a hablar de las cosas geniales que estamos haciendo aquí:

1. Modelos Alucinantes: hemos lanzado toda la artillería pesada: Random Forest, Regresión Logística, LDA. Estos modelos son como los superhéroes de la predicción del tiempo. ¡Prepárate para verlos en acción!

2.Datos Enloquecidos: antes de alimentar a nuestros modelos con datos, tenemos que hacerles una manicura de datos. Eso significa limpiarlos, normalizarlos y prepararlos para la batalla. ¡No hay lugar para datos desordenados en este proyecto!

## Paso 1: Preparación 🚀

Primero las primeras, ¿sabes? Importamos las herramientas necesarias, como pandas para manejar los datos, sklearn para entrenar los modelos y algunas otras cosas más.

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis
from sklearn.metrics import classification_report
```
## Paso 2: Carga de Datos 📊

Luego, metemos los datos en la batidora, aquí estamos cargando los datos del clima, ¡eso es lo que necesitamos para hacer magia! [Kaggle Rain in Australia - Predict next-day rain in Australia](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package?resource=download)

![image](https://github.com/Kzamudioq/IA/assets/138271936/8bcb4246-2399-46c6-9629-bff242b0dcdb)


```python
Data = pd.read_csv('weatherAUS.csv')
print('Tamaño del dataset :', Data.shape)
```

Aquí te dejo una descripción de cada variable en nuestro conjunto de datos:

1. **Age:** Edad de las mujeres en estudio.
2. **Number of sexual partners:** Número de parejas sexuales.
3. **First sexual intercourse:** Edad en la que tuvieron su primera relación sexual.
4. **Num of pregnancies:** Número de embarazos.
5. **Smokes:** Si fuman o no.
6. **Smokes (years):** Años de tabaquismo.
7. **Smokes (packs/year):** Paquetes de cigarrillos por año.
8. **Hormonal Contraceptives:** Uso de anticonceptivos hormonales.
9. **Hormonal Contraceptives (years):** Años de uso de anticonceptivos hormonales.
10. **IUD:** Uso de dispositivo intrauterino.
11. **IUD (years):** Años de uso de dispositivo intrauterino.
12. **STDs:** Si tienen enfermedades de transmisión sexual.
13. **STDs (number):** Número de enfermedades de transmisión sexual.
14. **STDs:condylomatosis:** Condilomas.
15. **STDs:cervical condylomatosis:** Condilomas cervicales.
16. **STDs:vaginal condylomatosis:** Condilomas vaginales.
17. **STDs:vulvo-perineal condylomatosis:** Condilomas vulvo-perineales.
18. **STDs:syphilis:** Sífilis.
19. **STDs:pelvic inflammatory disease:** Enfermedad inflamatoria pélvica.
20. **STDs:genital herpes:** Herpes genital.
21. **STDs:molluscum contagiosum:** Molluscum contagioso.
22. **STDs:AIDS:** VIH/SIDA.
23. **STDs:HIV:** VIH.
24. **STDs:Hepatitis B:** Hepatitis B.
25. **STDs:HPV:** Virus del papiloma humano.
26. **STDs: Number of diagnosis:** Número de diagnósticos de enfermedades de transmisión sexual.
27. **STDs: Time since first diagnosis:** Tiempo desde el primer diagnóstico.
28. **STDs: Time since last diagnosis:** Tiempo desde el último diagnóstico.
29. **Dx:Cancer:** Diagnóstico de cáncer.
30. **Dx:CIN:** Diagnóstico de neoplasia intraepitelial cervical.
31. **Dx:HPV:** Diagnóstico de virus del papiloma humano.
32. **Dx:** Diagnóstico general.
33. **Hinselmann:** Resultado del test de Hinselmann.
34. **Schiller:** Resultado del test de Schiller.
35. **Citology:** Resultado de la citología.
36. **Biopsy:** Resultado de la biopsia.

**Nota:** Las variables van desde datos numéricos hasta categóricos, por lo que será emocionante explorar cómo estas afectan el riesgo de cáncer cervical. ¡Sigue pendiente para más análisis!



## ¿Por qué es Importante?

Bueno, resulta que la detección temprana es clave. El 15% de los casos ocurren entre los 20 y 30 años, ¡así que chicas jóvenes, la prevención es esencial! 💪

<p align="center" width="100%">
    <img width="50%" src="https://github.com/Kzamudioq/IA/assets/138271936/a5e73bbc-d4d4-4fbd-bef3-1fb5183bea24"> 
</p>

## ¿Qué Hay en Este Repositorio?

- **`Análisis Exploratorio de Datos:`** comencemos explorando la distribución de variables numéricas y categóricas. Los histogramas y gráficos de barras serán nuestras herramientas de elección para visualizar estas gemas de información. ¡Estamos a punto de descubrir patrones y secretos!
  
- **`Transformación de Variables:`**  a veces, las variables necesitan un pequeño cambio para brillar. Analizaremos si alguna transformación es necesaria para nuestras variables. ¿Será necesario convertir algunas en variables dummy o estandarizar las numéricas? ¡Misterios por resolver!
  
- **`Análisis de Correlación:`** desentrañaremos las relaciones entre las variables mediante la calculadora de la matriz de correlación. ¿Hay multicolinealidad o características altamente correlacionadas? Prepárate para descubrimientos fascinantes.
  
- **`Modelado y Evaluación:`** aquí es donde las cosas se ponen emocionantes. Construiremos modelos de machine learning para predecir nuestra variable objetivo. Hablaremos de divisiones de conjunto de datos, selección de modelos y cómo evaluar su rendimiento. ¿Preparado para el desafío?
  
- **`Manejo de Datos Desbalanceados:`** si la variable objetivo está desequilibrada, no te preocupes. Discutiremos estrategias como el muestreo estratificado y métricas de evaluación adecuadas para enfrentar este desafío.

- **`Validación Cruzada:`** para obtener estimaciones robustas del rendimiento del modelo, aprenderemos sobre la validación cruzada. ¡Una técnica esencial para maestros de datos intrépidos como tú!

`Recuerda, el conocimiento es poder. ¡corramos a ver el codigo!`

<p align="center" width="100%">
    <img width="50%" src="https://github.com/Kzamudioq/IA/assets/138271936/ef6198dd-e239-479f-9039-7967b07062c9"> 
</p>


## Próximos Pasos 🚀

Esto es solo el comienzo. En futuros repositorios, profundizaremos en modelos predictivos y más. ¡Mantente al tanto!



**¡Para obtener más información sobre el conjunto de datos, visita [Kaggle](https://www.kaggle.com/datasets/loveall/cervical-cancer-risk-classification/data)!**

