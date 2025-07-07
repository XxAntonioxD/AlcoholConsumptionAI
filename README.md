
# Título del proyecto: Predicción del Consumo de Alcohol mediante Machine Learning

## Descripción general
Este proyecto tiene como objetivo predecir los hábitos de consumo de bebidas alcohólicas a partir de variables demográficas utilizando técnicas de Machine Learning.

El modelo desarrollado permite, a partir de los datos de sexo, edad y nivel de estudios, estimar la probabilidad de que un individuo consuma alcohol. Este tipo de análisis puede ser útil para entender patrones de consumo en diferentes grupos poblacionales y apoyar en la toma de decisiones en campañas de concienciación.

## Instalación y configuración
Instrucciones para configurar el entorno del proyecto:

- Clonar el repositorio:
```bash
git clone <aquí_pones_tu_link_del_repositorio>
```

- Instalar dependencias:
```bash
pip install -r requirements.txt
```

## Datos
Este proyecto utiliza un conjunto de datos que contiene información sobre:
- Sexo
- Edad
- Nivel de estudios
- Consumo de bebidas alcohólicas

### Datos sin procesar
- `datos_transformados2.csv`: Archivo original que contiene los datos recogidos en formato CSV con las variables categóricas sin codificar.

### Datos procesados
- En el código se realiza la transformación de las variables categóricas mediante codificación de etiquetas (`LabelEncoder`).
- Los datos procesados se utilizan directamente en el modelo Random Forest para entrenar y evaluar el clasificador.

## Uso
Cómo ejecutar el proyecto:

### Instrucciones paso a paso

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

## Estructura
```
/data
  - datos_transformados2.csv (datos sin procesar y procesados)

/src
  /scripts
    - Scripts para entrenamiento y evaluación del modelo
  /notebooks
    - Notebooks Jupyter con los experimentos y visualizaciones

/tests
  - Casos de prueba (no implementados actualmente)

/docs
  - Documentación adicional (si corresponde)

/public
  - Carpeta para la página web estática (no implementada)
  - index.html (por completar en caso de documentar en GitLab Pages)
```

## Contribución
Las contribuciones son bienvenidas. Para colaborar en este proyecto, por favor, abre una "issue" o crea una "merge request" en el repositorio.

## Licencia
Este proyecto se distribuye bajo la licencia MIT, salvo que se indique lo contrario.

## Contacto
- [Tu nombre] - [Tu correo]
- [Puedes añadir otros colaboradores si corresponde]
