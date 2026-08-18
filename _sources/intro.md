# Evaluación de Modelos de Clasificación y Preprocesamiento para la Predicción de Riesgo Crediticio en *Give Me Some Credit*

**Valeria Flórez** · **Katherin Barrera**
Departamento de Matemáticas, Física y Ciencia de Datos, Universidad del Norte, Barranquilla, Colombia
`florezvaleria@uninorte.edu.co` · `lkatherin@uninorte.edu.co`

```{admonition} Estado del proyecto
:class: tip
**Fase 1 completada:** ETL y Análisis Exploratorio de Datos (EDA).
**Próximas fases:** tratamiento definitivo de anomalías, selección y entrenamiento de modelos de clasificación, y evaluación comparativa frente a los modelos vistos en el curso.
```

## Resumen

Este documento presenta la primera fase de un proyecto de clasificación de riesgo crediticio, desarrollado sobre el conjunto de datos público **Give Me Some Credit** (Kaggle), compuesto por 150,000 instancias y 11 variables financieras y de comportamiento de los clientes. En esta etapa se realiza el proceso de *Extract-Transform-Load* (ETL) y un Análisis Exploratorio de Datos (EDA) exhaustivo, con el fin de comprender la estructura del conjunto de datos, identificar valores atípicos y faltantes, y sentar las bases para las decisiones de preprocesamiento y modelamiento.

Tras la limpieza (imputación por mediana de dos variables con datos faltantes y eliminación de un registro con edad inválida), el dataset quedó con 149,999 filas sin valores nulos. El EDA reveló un fuerte desbalance de clases en la variable objetivo (93.32% sin morosidad grave frente a 6.68% con morosidad grave), asimetría positiva marcada en la mayoría de las variables numéricas, un código de valor especial (96/98) en las tres variables de conteo de atrasos que no representa un conteo real, y una anomalía en `DebtRatio` explicada por su cruce con los registros de ingreso no reportado. Dado el tamaño muestral (N ≈ 150,000), se evitaron pruebas formales de normalidad por exceso de potencia estadística, optando en su lugar por diagnósticos descriptivos de forma y por la prueba de Mann–Whitney U con tamaño de efecto corregido por empates (r de Rosenthal) y AUC univariado, aplicada uniformemente a ocho variables numéricas frente a la variable objetivo. El desarrollo del modelo predictivo, su evaluación y los resultados finales se abordarán y documentarán en las siguientes etapas del proyecto.

**Palabras clave:** riesgo crediticio, clasificación binaria, análisis exploratorio de datos, valores atípicos, desbalance de clases.

## Contenido de este libro

- 📄 **[Reporte de avance (PDF)](paper.md)** — el documento formal de la Fase 1, con formato de artículo científico (plantilla Springer Nature).
- 📓 **[Análisis Exploratorio de Datos](analisis_exploratorio.ipynb)** — el notebook completo e interactivo con todo el código, las visualizaciones y las decisiones documentadas paso a paso.

## Enlaces

- **Dataset:** [Give Me Some Credit en Kaggle](https://www.kaggle.com/c/GiveMeSomeCredit)
- **Código fuente:** [github.com/valeriaflorezs/GiveMeSomeCredit](https://github.com/valeriaflorezs/GiveMeSomeCredit)

```{tableofcontents}
```
