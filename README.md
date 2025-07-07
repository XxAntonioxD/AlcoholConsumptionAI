
# Título del Proyecto: Predicción del Consumo de Alcohol mediante Machine Learning

## Descripción General
Este proyecto tiene como objetivo predecir los hábitos de consumo de bebidas alcohólicas a partir de variables demográficas utilizando técnicas de Machine Learning.

El conjunto de datos contiene información sobre el sexo, la edad y el nivel de estudios de cada individuo. El objetivo es entrenar un clasificador que, dadas estas variables, sea capaz de predecir si una persona consume bebidas alcohólicas.

El modelo utilizado es un **Random Forest Classifier**, y su rendimiento se evalúa mediante métricas como la precisión, la exactitud y la sensibilidad.

## Instalación y Configuración
Sigue estos pasos para configurar el entorno del proyecto:

1. Clona el repositorio:
```bash
git clone <aquí_pones_tu_link_del_repositorio>
```

2. Instala las dependencias necesarias:
```bash
pip install -r requirements.txt
```

📌 **Nota:** Las librerías necesarias son:
- pandas
- scikit-learn
- matplotlib

## Datos
El conjunto de datos utilizado en este proyecto es:  
**datos_transformados2.csv**

Este conjunto de datos contiene las siguientes columnas:
- `Sexo`: Género del individuo.
- `Edad`: Categoría de edad.
- `Nivel de estudios`: Nivel educativo.
- `Consumo de bebidas alchólicas`: Variable objetivo que indica si la persona consume alcohol.

Los datos ya están preprocesados y listos para el entrenamiento.

## Uso

### Cómo ejecutar el proyecto:

1. Cargar el conjunto de datos:
```python
import pandas as pd
df = pd.read_csv('datos_transformados2.csv', encoding='latin-1', sep=';')
```

2. Entrenar y evaluar el modelo:
```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import accuracy_score, precision_score, recall_score

# Definir características y etiquetas
features = ['Sexo', 'Edad', 'Nivel de estudios']
X = df[features].copy()
y = df['Consumo de bebidas alchólicas'].copy()

# Codificar variables categóricas
label_encoder = LabelEncoder()
X['Sexo'] = label_encoder.fit_transform(X['Sexo'])
X['Edad'] = label_encoder.fit_transform(X['Edad'])
X['Nivel de estudios'] = label_encoder.fit_transform(X['Nivel de estudios'])
y = label_encoder.fit_transform(y)

# Separar en conjuntos de entrenamiento y prueba
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=77)

# Entrenar el modelo
rf_model = RandomForestClassifier(n_estimators=100, max_depth=5, max_features='log2', random_state=42)
rf_model.fit(X_train, y_train)

# Realizar predicciones
y_pred = rf_model.predict(X_test)

# Evaluar el modelo
print("Exactitud:", accuracy_score(y_test, y_pred))
print("Precisión:", precision_score(y_test, y_pred, average='weighted'))
print("Sensibilidad:", recall_score(y_test, y_pred, average='weighted'))
```

3. Visualizar la importancia de las variables:
```python
import matplotlib.pyplot as plt

importances = rf_model.feature_importances_
feature_names = X.columns

plt.bar(feature_names, importances)
plt.title("Importancia de las Variables (Random Forest)")
plt.ylabel("Importancia")
plt.show()
```

## Estructura del Proyecto
```
/src
  /scripts
    - Scripts para procesamiento de datos y entrenamiento del modelo
  /notebooks
    - Notebooks Jupyter con los experimentos y evaluaciones

/docs
  - Documentación adicional en PDF
```

## Contacto
- [Tu nombre] - [Tu correo]
- [Puedes añadir otros colaboradores si quieres]
