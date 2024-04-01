@Kzamudioq ¿Qué te parece el repositorio? ¡Está chido! :+1:

<h1 align="center">
  <p align="center">:star: Bart Simpson te guía: Repositorio de predicción del clima en Australia, Man! :star:</p>
</h1>


`¡Hola, soy Bart Simpson!`



<p align="center" width="100%">
    <img width="60%" src="https://github.com/Kzamudioq/IA/assets/138271936/66d219c8-e5f3-4040-8602-01874c9a4f05"> 
</p>

¡Ey, man! Bienvenido a este proyecto loco donde estamos tratando de predecir el clima en Australia, mediate una base de datos extensa. Prepárate para una aventura salvaje en el mundo de los datos y los modelos de aprendizaje automático. ¡Es como una montaña rusa, pero para tus neuronas!

## 🧠 **¿Qué rayos es este proyecto?** 


Aquí tienes la primicia: estamos tratando de ser los más listos de la clase prediciendo el clima, estamos usando datos de los aeropuertos de Australia y alimentándolos a nuestros modelos de aprendizaje automático para ver si pueden adivinar qué tiempo va a hacer el dia de mañana. ¡Es como una apuesta, pero con datos!

<p align="center" width="100%">
    <img width="100%" src="https://github.com/Kzamudioq/IA/assets/138271936/b5193987-3d43-4213-bca6-f8f384d2fb1b"> 
</p>


## 💡 **Características Molonas** 💡

Vamos a hablar de las cosas geniales que estamos haciendo aquí:

1. Modelos alucinantes: hemos lanzado toda la artillería pesada: Random Forest, Regresión Logística, LDA. Estos modelos son como los superhéroes de la predicción del tiempo. ¡Prepárate para verlos en acción!

2. Datos del clima: antes de alimentar a nuestros modelos con datos, tenemos que hacerles una manicura de datos. Eso significa limpiarlos, normalizarlos y prepararlos para la batalla. ¡No hay lugar para datos desordenados en este proyecto!

### Paso 1: preparación 🚀

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
### Paso 2: carga de datos 📊

Luego, metemos los datos en la batidora, aquí estamos cargando los datos del clima, ¡eso es lo que necesitamos para hacer magia! [Kaggle Rain in Australia - Predict next-day rain in Australia](https://www.kaggle.com/datasets/jsphyg/weather-dataset-rattle-package?resource=download)

<p align="center" width="100%">
    <img width="100%" src="https://github.com/Kzamudioq/IA/assets/138271936/8bcb4246-2399-46c6-9629-bff242b0dcdb"> 
</p>


```python
Data = pd.read_csv('weatherAUS.csv')
print('Tamaño del dataset :', Data.shape)
```

### Paso 2: preprocesamiento 💪

El preprocesamiento de datos es como preparar la escena para una gran actuación. Así que, antes de que nuestros modelos puedan brillar en el escenario, tenemos que asegurarnos de que los datos estén en perfectas condiciones. Aquí te explico un poco más sobre lo que hicimos:

#### Eliminación de Valores Nulos 💥

Imagina que estás ensayando una obra y de repente un actor no aparece en el escenario. ¡Vaya lío! Bueno, los valores nulos en los datos son como esos actores desaparecidos. No podemos permitirnos tener datos faltantes porque podrían arruinar toda la actuación. Así que, si encontramos valores nulos en nuestro conjunto de datos, los eliminamos sin piedad. ¡No hay lugar para la vacilación en el mundo del modelado de datos!

#### Normalización 📏

Ahora, la normalización es como ajustar las luces en el escenario para que todos los actores se vean igual de brillantes. En nuestro caso, queremos que todas las características de nuestros datos estén en la misma escala. Si una característica tiene valores muy grandes y otra tiene valores muy pequeños, puede que nuestro modelo preste demasiada atención a la que tiene valores grandes y se pierda la más pequeña. Así que, utilizamos la normalización para asegurarnos de que todas las características estén en el mismo rango.

#### Tratamiento de Outliers 🎭

Los outliers son como esos momentos inesperados en una obra de teatro que hacen que todos se queden boquiabiertos. A veces, estos valores extremos pueden distorsionar nuestros modelos, así que tenemos que tratarlos con cuidado. Podemos eliminarlos, transformarlos o incluso dejarlos como están, dependiendo de la situación. Lo importante es asegurarnos de que no estén interfiriendo con el rendimiento general de nuestros modelos.

```python
#tratamiento de outliers.
def outlier_diagnostic_plots(df, variable):
    fig,axes = plt.subplots(1,3,figsize=(20,4))

    sns.histplot(df[variable], bins=30,ax=axes[0], kde=True)
    axes[0].set_title('Histograma')
    
    stats.probplot(df[variable], dist="norm", plot=axes[1])
    axes[1].set_title('QQ')
    
    # boxplot    
    sns.boxplot(y=df[variable],ax=axes[2])
    axes[2].set_title('Box&Whiskers')

outlier_diagnostic_plots(DataDarwin_missing, 'Evaporation')
```

<p align="center" width="100%">
    <img width="100%" src="https://github.com/Kzamudioq/IA/assets/138271936/e0472fc2-dd1e-4cda-a440-2c2637786a72"> 
</p>


#### Balanceo de clases ⚖️

El balanceo de datos es como asegurarnos de que todos los actores tengan el mismo tiempo en el escenario. Si una clase tiene muchos más ejemplos que otra, nuestro modelo podría estar sesgado hacia la clase mayoritaria. Para evitar esto, podemos aplicar técnicas de balanceo de datos como el sobremuestreo (oversampling) o el submuestreo (undersampling) para igualar el número de ejemplos en cada clase y mejorar así la capacidad predictiva de nuestro modelo.


### Paso 4: entrenamiento y evaluación 🏋️‍♂️

¡Es hora de enseñarle a estos modelos quién manda aquí! Vamos a entrenar un Random Forest, una Regresión Logística y un LDA.
Pero primero, vamos a preparar esos datos para entrenar a nuestros modelos, separaremos las características de las etiquetas y dividiremos los datos en conjuntos de entrenamiento y prueba.

```python

x_train_Darwin, x_test_Darwin, y_train_Darwin, y_test_Darwin = train_test_split(x_Darwin,y_Darwin,test_size=0.3,random_state = 42)
x_train_Perth, x_test_Perth, y_train_Perth, y_test_Perth = train_test_split(x_Perth,y_Perth,test_size=0.3,random_state = 42)
x_train_SydneyAirpor, x_test_SydneyAirpor, y_train_SydneyAirpor, y_test_SydneyAirpor =train_test_split(x_SydneyAirpor,y_SydneyAirpor,test_size=0.3,random_state = 42)
x_train_MelbourneAirport, x_test_MelbourneAirport, y_train_MelbourneAirport, y_test_MelbourneAirport = train_test_split(x_MelbourneAirport,y_MelbourneAirport,test_size=0.3,random_state = 42)

# Random Forest
rf_model = RandomForestClassifier()
rf_model.fit(x_train_SydneyAirpor_os, y_train_SydneyAirpor_os.values.ravel())
pred_rf = rf_model.predict(x_test_SydneyAirpor)
print(classification_report(y_test_SydneyAirpor,pred_rf))
print(rf_model.score(x_test_SydneyAirpor, y_test_SydneyAirpor))

# Regresión Logística
lr_model = LogisticRegression()
lr_model.fit(X_train_scaled, y_train)
lr_predictions = lr_model.predict(X_test_scaled)
lr_report = classification_report(y_test, lr_predictions)

# LDA
lda_model = LinearDiscriminantAnalysis()
lda_model.fit(X_train_scaled, y_train)
lda_predictions = lda_model.predict(X_test_scaled)
lda_report = classification_report(y_test, lda_predictions)

```


### Las Métricas! 🏆

<p align="center" width="100%">
    <img width="60%" src="https://github.com/Kzamudioq/IA/assets/138271936/5dda83b5-045c-42e6-a6d7-f1a8ac7f83b8"> 
</p>


Ahora, la parte que realmente importa, ¿no crees? Aquí tienes las métricas de los modelos, como si fueran los puestos en una competencia de skate:

| Modelo               | Clase | Precision | Recall | F1-score |
|----------------------|-------|-----------|--------|----------|
| Random Forest        | 0     | 0.93      | 0.94   | 0.93     |
| Random Forest        | 1     | 0.76      | 0.72   | 0.74     |
| Regresión Logística  | 0     | 0.90      | 0.76   | 0.82     |
| Regresión Logística  | 1     | 0.50      | 0.74   | 0.60     |
| LDA                  | 0     | 0.90      | 0.78   | 0.84     |
| LDA                  | 1     | 0.53      | 0.74   | 0.62     |

## Próximos Pasos 🚀

Esto es solo el comienzo. En futuros repositorios, profundizaremos en modelos predictivos y más. ¡Mantente al tanto!




