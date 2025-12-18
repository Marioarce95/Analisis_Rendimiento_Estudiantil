# Análisis de Rendimiento Estudiantil

Este proyecto realiza un análisis exhaustivo de un conjunto de datos académicos para comprender los factores que influyen en el rendimiento de los estudiantes y su éxito en la colocación laboral. Se emplean técnicas de Análisis Exploratorio de Datos (EDA) y modelado predictivo (Regresión y Clasificación) para extraer insights valiosos.

## Descripción del Dataset

El conjunto de datos contiene información sobre 10,000 estudiantes con 10 atributos diferentes. Los datos fueron obtenidos de [este repositorio](https://raw.githubusercontent.com/cjuangab/EstadisticayExploraciondeDatosII/main/Datos/Datos_Estudiantes.csv).

**Dimensiones:** 10,000 filas x 10 columnas.

**Variables:**
*   **College_ID:** Identificador único de la universidad (Eliminado durante el preprocesamiento).
*   **IQ:** Coeficiente intelectual del estudiante (distribución normal ~100).
*   **Prev_Sem_Result:** Promedio del semestre anterior.
*   **CGPA:** Promedio ponderado acumulado actual.
*   **Academic_Performance:** Calificación académica anual.
*   **Internship_Experience:** Experiencia en pasantías (Sí/No).
*   **Extra_Curricular_Score:** Puntaje en actividades extracurriculares.
*   **Communication_Skills:** Puntaje en habilidades de comunicación.
*   **Projects_Completed:** Cantidad de proyectos completados.
*   **Placement:** Estado de colocación laboral (Target para clasificación).

**Calidad de Datos:** No se encontraron valores nulos ni duplicados.

## Metodología

El flujo de trabajo del análisis se divide en las siguientes etapas:

1.  **Preprocesamiento:**
    *   Limpieza de datos (eliminación de columnas irrelevantes como `College_ID`).
    *   Codificación de variables categóricas (`Internship_Experience`, `Placement`) utilizando `LabelEncoder`.

2.  **Análisis Exploratorio de Datos (EDA):**
    *   Análisis estadístico descriptivo (media, desviación estándar, asimetría, curtosis).
    *   Visualización de distribuciones mediante histogramas y diagramas de caja (boxplots) para detección de outliers.
    *   Análisis de correlación de Pearson y mapas de calor (heatmap).

3.  **Modelado Predictivo:**
    *   **Clasificación (Predicción de `Placement`):** Se entrenaron y evaluaron múltiples modelos dividiendo el dataset en entrenamiento (80%) y prueba (20%):
        *   Logistic Regression
        *   Decision Tree Classifier
        *   Random Forest Classifier
        *   Gradient Boosting Classifier
        *   **XGBoost Classifier**
    *   **Regresión Lineal (Explicación de `CGPA`):** Se analizó la relación lineal entre el resultado del semestre anterior y el CGPA actual.

## Resultados Clave

### Hallazgos del EDA
*   Existe una correlación positiva extremadamente fuerte (**0.89**) entre `Prev_Sem_Result` y `CGPA`.
*   La variable `Placement` muestra una fuerte correlación con `CGPA` (**0.80**) y `Prev_Sem_Result` (**0.71**), indicando que el desempeño académico es el mayor predictor de empleo.
*   `IQ` tiene una correlación débil con el desempeño académico y la colocación.
*   La mayoría de los estudiantes (~83%) en este dataset no obtuvieron colocación.

### Resultados de Clasificación
El objetivo fue predecir si un estudiante obtendría una colocación laboral. El rendimiento de los modelos (Accuracy) fue el siguiente:

*   Logistic Regression: 88.7%
*   Decision Tree: 90.6%
*   Random Forest: 93.2%
*   Gradient Boosting: 93.7%
*   **XGBoost: 94.1%** (Mejor Modelo)

### Resultados de Regresión
Se encontró que el `Prev_Sem_Result` es un predictor casi perfecto para el `CGPA`:
*   **R-cuadrado (R²):** 0.962
*   Esto indica que el **96.2%** de la variabilidad en el CGPA puede ser explicada por las notas del semestre anterior.
