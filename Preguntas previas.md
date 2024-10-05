# 1. Identificación del problema
>¿Cuál es el problema específico que quieren abordar?

El problema es la saturación de redes de distribución de energía eléctrica cuando hay un exceso de consumo por parte de los usuarios. Mediante la predicción del consumo de energía eléctrica a nivel domiciliario individual, la empresa prestadora de servicio puede preveer cuándo ocurrirá un pico de consumo, y en base a ello tomar las acciones pertinentes para evitar la saturación de la red (mantenimiento preventivo). 

---

# 2. Relevancia del problema
>¿Por qué es importante o relevante este problema?

Porque en el caso que haya un exceso en el consumo se puede producir un corte en el suministro de energía (se deja sin servicio a los usuarios), y además hay riesgo de rotura de equipos en la red (por ejemplo transformadores) y en las instalaciones del usuario. 

Esto impacta tanto en el usuario (corte de suministro y posible rotura de dispositivos eléctricos) como en la empresa prestadora (gastos por mantenimiento elevados, disminuye el tiempo de disponibilidad del servicio, reclamos/denuncias por parte de usuarios afectados)

---

# 3. Datos disponibles
>¿Qué bases de datos tienen identificadas y cómo planean utilizarlas?

El dataset "Individual Household Electric Power Consumption" contiene mediciones de consumo de potencia en una vivienda unifamiliar en Francia, entre dic-2006 y nov-2010 (un registro por minuto)
https://doi.org/10.24432/C58K54

Se entrenan modelos de series temporales en base a este dataset (habiendo hecho limpieza del mismo), que permiten luego poder predecir consumos futuros.

---

# 4. Posibles métodos de análisis
>¿Qué métodos o técnicas de análisis de datos consideran adecuados?

Los pasos del EDA son:

* Análisis de histograma: para conocer la distribución de los datos. Tests pertinentes
* Análisis de estadísticos: medidas de tendencia central, dispersión, mínimos y máximos
* Pruebas de Pearson para determinar correlación lineal entre variables y descartar las que no aportan información
* Análisis en dominio de Fourier: se asume que existen patrones de comportamiento periódicos en los datos. Con el análisis en este dominio, se identifican los períodos en los cuales el comportamiento es periódico
* Análisis en ventanas temporales: gráficos de promedios en ventanas temporales dadas por el análisis de Fourier, para tener una idea del comportamiento esperado. Ventanas de: 1 día, 1 semana, 1 mes, 1 año
* Descomposición en componentes de tendencia, seasonality y ruido

El dataset contiene muchas features. Se pone como objetivo predecir el consumo sólo en base a valores anteriores de esta variable (potencia aparente), con lo cual no se utilizarán features del dataset como puede ser el consumo por zonas del domicilio, la intensidad de corriente o el voltaje. Estas variables se analizaron en el EDA, pero dado el objetivo propuesto de predecir sólo en base a históricos, se descartaron. Algunos análisis realizados en relación a estas variables: gráficos de torta de consumo activo vs reactivo, gráfico de barras de consumo acumulado por zonas, heatmap y scatterplot entre todas las variables, tests de pearson entre variables para determinar correlación.

---

# 5. Objetivos específicos
>¿Cuáles son los objetivos concretos y medibles de su proyecto?

Lograr una MAE menor al 60% para una ventana de 1 año (el año siguiente a partir del último dato de entrenamiento)

---

# 6. Preguntas de investigación
>¿Qué preguntas de investigación guiarán su análisis de datos?

1. ¿Existen comportamientos periódicos en los datos? ¿En qué ventanas temporales?
2. ¿Se observa alguna tendencia en los datos?
3. Analizando las curvas temporales, ¿puedo inferir patrones de comportamiento de los habitantes?
4. ¿Existe alguna variable exógena que me permita mejorar los resultados de la predicción?

---

# 7. Herramientas y tecnologías a utilizar
>¿Qué herramientas y tecnologías de ciencia de datos planean emplear?

Se utilizará el lenguaje Python, en el entorno de Google Colab. Se pueden desarrollar algunos scripts por fuera de este entorno, usando el mismo lenguaje 

Para el EDA se usa matplotlib, seaborn, numpy, pandas

Para el entrenamiento de modelos se usa pandas, scikit-learn (modelos, train/test split, escalamiento y métricas), matplotlib para graficar métricas. 

En cuanto a modelos se utilizan Random Forests (sklearn), Redes Neuronales (tensorflow) y Prophet 

Para despliegue de modelos se usa Gradio

Para almacenamiento se utiliza principalmente Google Drive y Github

---

# 8. Hipótesis iniciales o suposiciones
>¿Cuáles son sus hipótesis o suposiciones iniciales?

1. Es posible predecir el consumo futuro en base a históricos, debido a que hay comportamientos periódicos en los datos
2. Cuanto mayor es la ventana de predicción (cuanto más a largo plazo predigo), mayor será el error
3. Hay una correlación de consumo con la variable exógena temperatura
4. Hay una tendencia al aumento en el consumo de energía


---

# 9. Potenciales desafíos y limitaciones
>¿Qué desafíos y limitaciones anticipan para su proyecto?

1. La predicción en base a valores históricos únicamente puede ser insuficiente (se pueden requerir variables exógenas para mejorar el modelo)
2. Los datos de entrenamiento del modelo son hasta 2010, si se quiere predecir algo más a futuro (por ejemplo 2024) pueden haber cambiado los hábitos de consumo de la población y el modelo entrenado ya no será adecuado
3. Que los modelos elegidos no capturen comportamientos periódicos, y que su performance se degrade cuanto más tiempo se prediga a futuro


---

# 10. Planificación preliminar y distribución del trabajo
>¿Cómo planean organizar y distribuir el trabajo dentro del equipo?

Este trabajo va a ser unipersonal según acuerdo con coordinadora. No va a haber distribución