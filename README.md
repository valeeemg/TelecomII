# TelecomX

Informe de Análisis y Predicción de Cancelación de Clientes

La cancelación de clientes, también conocida como churn, representa uno de los principales desafíos para muchas empresas de servicios. Comprender por qué los clientes deciden cancelar permite desarrollar estrategias de retención más efectivas y mejorar la estabilidad del negocio.

En este análisis se trabajó con una base de datos de clientes que incluye información demográfica, características del servicio contratado y variables relacionadas con el comportamiento de consumo. El objetivo principal fue identificar los factores que influyen en la cancelación de clientes y desarrollar modelos predictivos capaces de anticipar este comportamiento.

Para lograrlo, se realizaron diversas etapas que incluyeron limpieza de datos, transformación de variables, análisis exploratorio, balanceo de clases y construcción de modelos de machine learning.

Preparación y preprocesamiento de los datos

Como primera etapa del análisis, se eliminaron columnas que no aportaban valor predictivo al modelo, como identificadores únicos de clientes. Este tipo de variables no contienen información relevante para explicar el comportamiento de cancelación y pueden afectar negativamente el desempeño de los modelos.

Posteriormente, las variables categóricas fueron transformadas a formato numérico mediante técnicas de codificación, específicamente utilizando one-hot encoding, lo que permitió que los algoritmos de machine learning pudieran procesar correctamente la información.

Durante el análisis también se evaluó la proporción de clientes que cancelaron el servicio frente a aquellos que permanecieron activos. Los resultados mostraron la siguiente distribución:

Clientes que permanecen activos: 73.46%

Clientes que cancelaron: 26.53%

Esto indica un desbalance moderado entre las clases, lo cual puede influir en el desempeño de los modelos predictivos. Para abordar este problema se exploró el uso de técnicas de balanceo como SMOTE (Synthetic Minority Over-sampling Technique), que permite generar ejemplos sintéticos de la clase minoritaria para mejorar la capacidad del modelo de identificar correctamente los casos de cancelación.

Adicionalmente, se evaluó la necesidad de normalizar o estandarizar los datos, dependiendo del tipo de modelo a utilizar. Los modelos basados en distancia o en optimización de parámetros, como Regresión Logística, requieren normalización para evitar que variables con valores más grandes dominen el proceso de aprendizaje. En contraste, modelos basados en árboles como Random Forest no dependen de la escala de los datos.

Análisis exploratorio de datos

Se realizaron diversas visualizaciones para comprender mejor la relación entre las variables y la cancelación de clientes.

Uno de los análisis clave fue la matriz de correlación, que permitió identificar relaciones entre variables numéricas y detectar posibles factores asociados con la cancelación.

Además, se analizaron variables específicas mediante gráficos como boxplots y scatter plots, particularmente:

Tiempo de contrato vs cancelación

Gasto total vs cancelación

Estos análisis permitieron identificar patrones relevantes. Por ejemplo, se observó que los clientes con contratos más cortos o menor tiempo de permanencia presentan una mayor probabilidad de cancelar el servicio. Asimismo, ciertos patrones en el gasto total o mensual pueden reflejar niveles de compromiso o satisfacción con el servicio.

Construcción de modelos predictivos

Para predecir la cancelación de clientes se construyeron dos modelos de machine learning con enfoques diferentes:

Regresión Logística

La Regresión Logística es un modelo de clasificación ampliamente utilizado para estimar la probabilidad de ocurrencia de un evento binario, en este caso la cancelación del cliente.

Debido a que este modelo es sensible a la escala de las variables, se aplicó previamente normalización utilizando StandardScaler. Esto garantiza que todas las variables tengan una escala comparable y evita que las variables con valores más grandes influyan de forma desproporcionada en el modelo.

Random Forest

El segundo modelo utilizado fue Random Forest, un algoritmo basado en múltiples árboles de decisión que combina los resultados de varios modelos para mejorar la precisión y reducir el riesgo de sobreajuste.

A diferencia de la Regresión Logística, Random Forest no requiere normalización, ya que las decisiones se toman mediante divisiones de los datos y no mediante cálculos de distancia.

Evaluación de los modelos

Para evaluar el desempeño de los modelos se utilizaron diversas métricas de clasificación:

Exactitud (Accuracy)

Precisión (Precision)

Recall

F1-score

Matriz de confusión

La exactitud mide el porcentaje total de predicciones correctas realizadas por el modelo. Sin embargo, debido al desbalance entre clases, también es importante analizar métricas como precision y recall, que permiten evaluar con mayor detalle la capacidad del modelo para identificar correctamente a los clientes que cancelan.

El F1-score combina precisión y recall en una sola métrica, proporcionando una medida equilibrada del rendimiento del modelo.

Tras comparar los resultados, el modelo de Random Forest mostró un mejor desempeño general, ya que logró capturar relaciones más complejas entre las variables del conjunto de datos. Esto es común en problemas donde las interacciones entre variables no son completamente lineales.

En términos de generalización, no se observaron indicios graves de underfitting, ya que ambos modelos lograron identificar patrones en los datos. Sin embargo, modelos más complejos como Random Forest pueden presentar cierto riesgo de overfitting si no se controlan adecuadamente parámetros como la profundidad de los árboles o el número de estimadores.

Análisis de las variables más relevantes

Una vez entrenados los modelos, se realizó un análisis para identificar las variables más influyentes en la predicción de cancelación.

En el caso de la Regresión Logística, se analizaron los coeficientes asociados a cada variable. Estos coeficientes indican cómo cada variable afecta la probabilidad de cancelación:

Coeficientes positivos → aumentan la probabilidad de cancelación

Coeficientes negativos → reducen la probabilidad de cancelación

Para el modelo Random Forest, se utilizó la métrica de importancia de variables, que mide cuánto contribuye cada variable a mejorar las divisiones dentro de los árboles de decisión.

A partir de estos análisis, se identificaron como factores relevantes:

Tiempo de permanencia del cliente (tenure)

Nivel de gasto del cliente

Características del contrato

Tipo de servicio contratado

Estas variables influyen significativamente en la probabilidad de que un cliente decida cancelar el servicio.

Factores principales que influyen en la cancelación

Con base en el análisis exploratorio y los modelos predictivos, se identificaron varios factores clave que influyen en la cancelación de clientes:

Tiempo de contrato o permanencia
Los clientes con menor tiempo de permanencia presentan mayor probabilidad de cancelar.

Nivel de gasto o facturación
Cambios en el nivel de gasto pueden reflejar menor compromiso con el servicio o posibles problemas de satisfacción.

Tipo de contrato o servicio
Algunas combinaciones de servicios pueden estar asociadas con mayor o menor probabilidad de cancelación.

Características del cliente
Variables demográficas o relacionadas con el uso del servicio también pueden influir en el comportamiento de cancelación.

Estrategias de retención de clientes

Con base en los resultados obtenidos, se proponen varias estrategias que pueden ayudar a reducir la tasa de cancelación:

1. Programas de fidelización para nuevos clientes

Dado que los clientes con menor tiempo de permanencia tienen mayor probabilidad de cancelar, la empresa podría implementar programas de fidelización durante los primeros meses del servicio, como descuentos o beneficios adicionales.

2. Ofertas personalizadas

Utilizando modelos predictivos como los desarrollados en este análisis, la empresa podría identificar clientes con alto riesgo de cancelación y ofrecer promociones personalizadas para incentivar su permanencia.

3. Mejora de la experiencia del cliente

Analizar los servicios asociados con mayor cancelación puede ayudar a identificar problemas en la calidad del servicio o en la experiencia del usuario, permitiendo implementar mejoras específicas.

4. Monitoreo predictivo continuo

La implementación de modelos de machine learning en sistemas operativos permitiría detectar tempranamente clientes en riesgo de cancelar, facilitando intervenciones proactivas.

Conclusión

Este análisis permitió identificar los principales factores asociados con la cancelación de clientes y desarrollar modelos predictivos capaces de anticipar este comportamiento.

Los resultados muestran que variables relacionadas con el tiempo de permanencia, el nivel de gasto y las características del servicio tienen un impacto significativo en la probabilidad de cancelación.

Entre los modelos evaluados, Random Forest mostró un mejor desempeño, debido a su capacidad para capturar relaciones complejas entre las variables.

La aplicación de estos modelos en un entorno empresarial puede ayudar a reducir la tasa de cancelación mediante estrategias de retención más efectivas, permitiendo a las empresas tomar decisiones basadas en datos y mejorar la satisfacción de sus clientes.
