
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

### NOTEBOOK
En este proyecto, el modelo Random Forest y la técnica SHAP no pueden separarse en dos proyectos distintos.
El motivo es que SHAP necesita un modelo entrenado para calcular la importancia de las variables.
Primero se entrena el Random Forest y después SHAP utiliza ese modelo para explicar sus decisiones.
Ambos pasos son parte del mismo flujo y deben ejecutarse juntos y en orden.

Además, es fundamental leer cada celda y sus comentarios antes de ejecutarlas, ya que el proyecto no está diseñado para ejecutarse de forma desordenada ni por partes independientes.

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
