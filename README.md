# Clasificación de tumores de mama: KNN, SVM y MLP

Práctica de **Fundamentos de Inteligencia Artificial**, grupo LITIID71, Equipo ClimateAI.

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HectorPartido/Tumores-KNN-SVM-MLP/blob/main/Clasificacion_Tumores_KNN_SVM_MLP.ipynb)

Comparamos tres clasificadores supervisados, **K vecinos más cercanos (KNN)**, **máquina de vectores de soporte (SVM)** y **perceptrón multicapa (MLP)**, para decidir si un tumor de mama es benigno o maligno. Todo está en un solo notebook: `Clasificacion_Tumores_KNN_SVM_MLP.ipynb`.

## Datos

Wisconsin Diagnostic Breast Cancer (WDBC), Universidad de Wisconsin (1995): 569 tumores (357 benignos y 212 malignos) con 30 características numéricas de los núcleos celulares, calculadas de imágenes de una punción con aguja fina. Están en `data/wdbc.data`, y su descripción en `data/wdbc.names`.

## Cómo correrlo

**En Colab:** abre el botón de arriba y elige **Entorno de ejecución, Ejecutar todas**. El notebook descarga `data/wdbc.data` de este repositorio.

**En tu computadora:**

```bash
git clone https://github.com/HectorPartido/Tumores-KNN-SVM-MLP.git
cd Tumores-KNN-SVM-MLP
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook Clasificacion_Tumores_KNN_SVM_MLP.ipynb
```

## Método

- Partición estratificada: 80 % entrenamiento (455 tumores) y 20 % prueba (114), con `random_state = 42`.
- Cada modelo es un `Pipeline` con `StandardScaler`, para que la estandarización se calcule solo con entrenamiento.
- Hiperparámetros elegidos con `GridSearchCV` y validación cruzada estratificada de 5 pliegues, optimizando F1.
- Los tres se evalúan con el mismo conjunto de prueba: exactitud, precisión, exhaustividad (recall), F1, AUC y matriz de confusión. La clase positiva es **maligno**.

## Dónde está cada punto de la actividad

| Punto de la actividad | Sección del notebook |
|---|---|
| Cargar el dataset e identificar registros, variables y clases | 1 |
| Separar entradas y objetivo, dividir en entrenamiento y prueba, estandarizar | 2 |
| Entrenar y probar KNN, SVM y MLP con métricas y matriz de confusión | 3, 4 y 5 |
| Tabla comparativa y gráficas | 6 |
| Respuestas a las 4 preguntas | 7 |
| Conclusión | 8 |

## Resultados

La tabla comparativa, las respuestas a las preguntas y la conclusión están en las secciones 6 a 8 del notebook (PR 5).

## Equipo y PR

Cada integrante subió su sección del notebook en su propio PR, en este orden:

| PR | Integrante | Sección del notebook | Rama |
|---|---|---|---|
| Inicio | Hector Partido Flores | Estructura del repositorio, datos y portada del notebook | `main` |
| 1 | Hector Martínez Sánchez | 1 y 2: carga, exploración y preparación de los datos | `feat/datos` |
| 2 | Ismael Alexander Hidalgo Aguilando | 3: K vecinos más cercanos (KNN) | `feat/knn` |
| 3 | Gildardo Emmanuel González García | 4: máquina de vectores de soporte (SVM) | `feat/svm` |
| 4 | Anthony Oziel Ramos López | 5: perceptrón multicapa (MLP) | `feat/mlp` |
| 5 | Hector Partido Flores | 6 a 8: comparación, análisis, preguntas y conclusión | `feat/comparacion` |
