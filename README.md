# 1.	Introducción 
Objetivo del proyecto: 
El presente proyecto tiene como finalidad el análisis del mercado de valores, precisamente de la compañía “Microsoft”, este proyecto se centra en la parte del análisis técnico, el mismo utiliza el conjunto de datos de los precios de las acciones desde el 13 de marzo 1986 hasta el presente día, para construir un modelo capaz de estimar los precios de las acciones.
Importancia del tema: 
El proyecto resulta de importancia para el conocimiento de los inversionistas de la empresa y para los interesados en el tema de las acciones, ya que, un análisis técnico resulta de ayuda como una herramienta para la toma de decisiones y permite una mejor gestión de riesgos en las estrategias de inversión, además, durante el tiempo de predicción se hace un análisis de los eventos financieros de mayor relevancia que afectaron a los valores y como el mercado reacciono a distintos contextos. 
Breve descripción de los datos:
Los datos utilizados en el proyecto fueron exportados de la base de datos de Yahoo finances, esto con el fin de, poder crear el modelo predictivo con los datos desde el 13 de marzo 1986 hasta la actualidad, además, para el análisis de eventos utilizamos distintas fuentes confiables de noticias que explicaran el comportamiento del mercado. 
### 2.	Planteamiento del problema 
Pregunta de investigación:
¿Cómo actuara la bolsa de valores de la empresa Microsoft en un futuro cercano? 
¿Cuáles son las tendencias de comportamiento de las acciones en una empresa? 
¿Qué factores influyen en el comportamiento del precio de las acciones? 
### 3.	Conjunto de datos 
Descripción del dataset:
•	Fuente de los datos: Yahoo Finances
•	Características principales: Número de filas, columnas, tipos de variables (numéricas, categóricas, etc.).
•	Procedencia de los datos: https://finance.yahoo.com/quote/MSFT/ 
•	Procesamiento inicial:
¿Qué transformaciones aplicaste para preparar los datos? 
Se reviso la existencia de valores faltantes o duplicados, sin embargo, los datos ya estaban limpios, por lo que, no fue necesario realizar la limpieza
### 4.	Modelamiento de los datos 
Selección de Variables:

1.	Nombre de la Variable: open
Tipo de Dato: numérico
 
Resumen Estadístico: 

Valor mínimo: 0.054594

Valor máximo: 466.159

Media: 55.2994

Desviación: 94.8405

Valores Únicos: np

3.	Nombre de la Variable: Fecha
   

Tipo de Dato: numérico 

Resumen Estadístico: np

Valores Únicos: np

4.	Nombre de la Variable: High
   
Tipo de Dato: numérico 

Resumen Estadístico: 

Valor mínimo: 0.056735

Valor máximo: 467.507368

Media: 55.848034

Desviación: 95.694483

Valores Únicos: np

5.	Nombre de la Variable: Low
   
Tipo de Dato: numérico 

Resumen Estadístico: 

Valor mínimo: 0.054594

Valor máximo: 463.624357

Media: 54.726007

Desviación: 93.905329

Valores Únicos: np

6.	Nombre de la Variable: Close
   
Tipo de Dato: numérico 

Resumen Estadístico: 

Valor mínimo: 0.055665

Valor máximo: 466.718781

Media: 55.308327

Desviación: 94.841109
	
Valores Únicos: np

7.	Nombre de la Variable: Volume
   
Tipo de Dato: numérico 

Resumen Estadístico: 

Valor mínimo: 2.304000 e+06

Valor máximo: 1.031789 e+09

Media: 5.651423 e+07

Desviación: 3.813929 e+07

Valores Únicos: np

8.	Nombre de la Variable: Dividens
   
Tipo de Dato: numérico 

Resumen Estadístico: 

Valor mínimo: 0.00000

Valor máximo: 3.08000

Media: 0.003038

Desviación: 0.046973

Valores Únicos: np

9.	Nombre de la Variable: Stock splits

Tipo de Dato: numérico 

Resumen Estadístico: 

Valor mínimo: 0.00000

Valor máximo: 2.000

Media: 0.01745

Desviación: 0.057738

Valores Únicos: np

Proceso utilizado para seleccionar las variables: No hubo

## Descripción del modelo
•	Tipo de modelo utilizado: 
Algoritmo de clasificación 

•	Justificación de la elección del modelo.

Simplifica el proceso de elección creando un sistema binario donde 1 representa que el precio subió y 0 que el precio bajo, además es lo necesario para predecir el comportamiento de estos.

Proceso de Modelamiento
•	Dividir los datos en conjuntos de entrenamiento y prueba.
Se entrena con las ultimas 100 lineas del dataset. Se utilizan todos los datos menos las ultimas 100 lineas para predecir las ultimas 100 lineas, no queremos predecir el pasado con informacion del futuro

•	Explicar si se utilizó validación cruzada u otro método de validación.
No se implemento ningun metodo de validacion

•	Código empleado para construir y entrenar el modelo (en Python o R).
•	from sklearn.ensemble import RandomForestClassifier
•	import numpy as np
•	
•	# Create a random forest classification model.  Set min_samples_split high to ensure we don't overfit.
•	model = RandomForestClassifier(n_estimators=100, min_samples_split=200, random_state=1)
Se crea un modelo de RandomForestClassifier con 100 árboles y se entrena con los datos de entrenamiento.


#Create a train and test set
train = data.iloc[:-100]
test = data.iloc[-100:]
model.fit(train[predictors], train["Target"])

## Evaluación del Modelo:
•	Métricas utilizadas para evaluar el rendimiento del modelo
Se utilizo la funcion precision_score de sklearn, esta se utiliza para calcular la precisión de un modelo de clasificación. La precisión es la proporción de verdaderos positivos entre el total de predicciones positivas hechas por el modelo. En otras palabras, mide la exactitud de las predicciones positivas del modelo.

### Gráficos de evaluación generados a partir de los resultados del modelo:

<img width="281" alt="image" src="https://github.com/user-attachments/assets/1c28f780-0b10-4cba-a859-f55584076b53">

 
## 5.	Resultados:
Tabla con los resultados del modelo:

<img width="279" alt="image" src="https://github.com/user-attachments/assets/07c70aa6-bf1c-48db-8aea-fd877d93c62b">


Interpretación: 

El modelo consiguió una precisión del 59%, sin embargo, es notable que la cantidad de movimientos o trades que hace disminuyo sustancialmente, esto hace que, si el modelo dice que va a subir, si o si lo hara, aunque esto pase muy pocas cosas.
Relaciona los hallazgos con las preguntas planteadas en el planteamiento del problema.

# 6.	Conclusiones

Resumen del proyecto:

•	¿Qué aprendiste al realizar este proyecto?

Durante el proceso de la realización del proyecto aprendimos de las metodologías de ciencia de datos, además, pudimos aprender como funciona un modelo de clasificación y también, sobre la bolsa de valores y como puede cambiar su comportamiento debido a otros factores. 

Aplicaciones prácticas:

•	¿Cómo se pueden usar los resultados obtenidos en un contexto real?

Pues prácticamente se utilizó todo en base al contexto real, por lo que, los resultados obtenidos serian aplicados en base a lo investigado, es decir, de manera que nos ayude a predecir si las acciones de la empresa deseada subirán o bajaran su valor.

Límites del análisis:

•	Explica las limitaciones del dataset o del análisis realizado.

La principal limitante de nuestro análisis predictivo es que nuestro modelo no toma en cuenta otros factores externos, debido a esto, limita su capacidad para interpretar movimientos predecibles. 

Propuestas futuras:

•	¿Qué podríamos mejorar o explorar en proyectos futuros?

Podríamos mejorar nuestra base de datos, además, utilizar diferentes metodologías que nos ayuden a organizarnos en un futuro. 

