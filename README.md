# ciencia-de-datos-everest
# ¿Podemos anticipar quién llegará a la cima del Everest?

Proyecto de Ciencia de Datos (UTN FRC, 2026): modelos de clasificación para estimar, con información previa a la expedición, si un escalador alcanzará la cima. Trabajo grupal de 8 integrantes, organizado con **Scrum en 4 sprints**.

## Datos
Dataset de Kaggle *Everest & the Death Zone — Will They Summit?* (`everest_summit_master.csv`), con unos 45.000 intentos de ascenso y 25 variables. Variable objetivo: `summited`. No se incluye en este repositorio; descargarlo desde Kaggle.

## Proceso
- **ETL y limpieza:** exclusión del personal de apoyo y de registros inconsistentes (quedaron 28.934).
- **Prevención de data leakage:** se excluyeron variables posteriores al inicio del ascenso, como `turnaround_reason` y `serious_incident`.
- **Transformaciones:** One-Hot Encoding de variables categóricas y estandarización para la regresión logística.
- **Partición estratificada** 64 % entrenamiento, 16 % validación y 20 % prueba.
- **Modelos comparados:** Regresión Logística, Random Forest y XGBoost, con distintos umbrales de decisión.

## Resultado
Se eligió **Regresión Logística con umbral 0,70**, que priorizó reducir las predicciones incorrectas de llegada a la cima. En el conjunto de prueba obtuvo precision de 72,91 %, especificidad de 98,29 % y ROC-AUC de 0,75, con recall bajo (10,11 %). Es un modelo conservador: casi no da falsas alarmas, pero detecta pocos ascensos exitosos.

## Contenido
- `notebooks/01_exploracion_y_limpieza.ipynb`
- `notebooks/02_modelado.ipynb`
- `notebooks/03_demostracion_prediccion.ipynb`

## Tecnologías
Python · pandas · scikit-learn · XGBoost · Google Colab
