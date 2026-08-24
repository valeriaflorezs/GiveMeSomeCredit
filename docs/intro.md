# Evaluación de Modelos de Clasificación y Preprocesamiento para la Predicción de Riesgo Crediticio en *Give Me Some Credit*

**Valeria Flórez** · **Katherin Barrera**
Departamento de Matemáticas, Física y Ciencia de Datos, Universidad del Norte, Barranquilla, Colombia
`florezvaleria@uninorte.edu.co` · `lkatherin@uninorte.edu.co`

```{admonition} Estado del proyecto
:class: tip
**Completado:** ETL, Análisis Exploratorio de Datos (EDA) y un primer modelo de clasificación (regresión logística), con evaluación en un conjunto de prueba separado desde antes de imputar o escalar.
**Próximos pasos:** cerrar la brecha de recall en la clase minoritaria (ponderación de clases, remuestreo o ajuste de umbral) y aplicar a `RevolvingUtilizationOfUnsecuredLines` una transformación de escala similar a la usada en `DebtRatio`.
```

## Resumen

Este documento presenta la primera fase de un proyecto de clasificación de riesgo crediticio, desarrollado sobre el conjunto de datos público **Give Me Some Credit** (Kaggle), compuesto por 150,000 instancias y 11 variables financieras y de comportamiento de los clientes. En esta etapa se realiza el proceso de *Extract-Transform-Load* (ETL) y un Análisis Exploratorio de Datos (EDA) exhaustivo, con el fin de comprender la estructura del conjunto de datos, identificar valores atípicos y faltantes, y sentar las bases para las decisiones de preprocesamiento y modelamiento.

Tras la limpieza (imputación por mediana de dos variables con datos faltantes y eliminación de un registro con edad inválida), el dataset quedó con 149,999 filas sin valores nulos. El EDA reveló un fuerte desbalance de clases en la variable objetivo (93.32% sin morosidad grave frente a 6.68% con morosidad grave), asimetría positiva marcada en la mayoría de las variables numéricas, un código de valor especial (96/98) en las tres variables de conteo de atrasos que no representa un conteo real, y una anomalía en `DebtRatio` explicada por su cruce con los registros de ingreso no reportado. Dado el tamaño muestral (N ≈ 150,000), se evitaron pruebas formales de normalidad por exceso de potencia estadística, optando en su lugar por diagnósticos descriptivos de forma y por la prueba de Mann–Whitney U con tamaño de efecto corregido por empates (r de Rosenthal) y AUC univariado, aplicada uniformemente a ocho variables numéricas frente a la variable objetivo.

Con esa base se entrenó un primer modelo de clasificación (regresión logística), dividiendo el conjunto en entrenamiento y prueba antes de imputar los valores faltantes restantes y de ajustar el escalador, para evitar fuga de información del conjunto de prueba. El modelo obtiene accuracy ≈ 93.6% y AUC-ROC ≈ 0.821, pero un recall de apenas 16% sobre los clientes que sí presentan morosidad grave — evidencia de que el umbral de decisión por defecto, en un problema tan desbalanceado, no aprovecha toda la capacidad de discriminación del modelo. El notebook documenta este margen de mejora y los próximos pasos para cerrarlo.

**Palabras clave:** riesgo crediticio, clasificación binaria, análisis exploratorio de datos, valores atípicos, desbalance de clases.

## Contenido de este libro

- 📄 **[Reporte de avance (PDF)](paper.md)** — el documento formal de la Fase 1, con formato de artículo científico (plantilla Springer Nature).
- 📓 **[Análisis Exploratorio de Datos y Modelado](analisis_exploratorio.ipynb)** — el notebook completo e interactivo con todo el código, las visualizaciones, el modelo de regresión logística y las decisiones documentadas paso a paso.

## Enlaces

- **Dataset:** [Give Me Some Credit en Kaggle](https://www.kaggle.com/c/GiveMeSomeCredit)
- **Código fuente:** [github.com/valeriaflorezs/GiveMeSomeCredit](https://github.com/valeriaflorezs/GiveMeSomeCredit)

```{tableofcontents}
```
