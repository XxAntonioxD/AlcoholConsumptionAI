
# Título del proyecto: Predicción del Consumo de Alcohol mediante Machine Learning

## Descripción general
Este proyecto tiene como objetivo predecir los hábitos de consumo de bebidas alcohólicas a partir de variables demográficas utilizando técnicas de Machine Learning.

El modelo desarrollado permite, a partir de los datos de sexo, edad y nivel de estudios, estimar la probabilidad de que un individuo consuma alcohol. Este tipo de análisis puede ser útil para entender patrones de consumo en diferentes grupos poblacionales y apoyar en la toma de decisiones en campañas de concienciación.

## Instalación y configuración
Instrucciones para configurar el entorno del proyecto:

- Clonar el repositorio:
```bash
git clone https://github.com/XxAntonioxD/AlcoholConsumptionAI.git
```

## Datos
Este proyecto utiliza un conjunto de datos que contiene información sobre:
- Sexo
- Edad
- Nivel de estudios
- Consumo de bebidas alcohólicas

### Datos sin procesar
- Los datos originales fueron extraídos del Instituto Nacional de Estadística. El archivo que es utilizado en el programa (`datos_transformados2.csv`) parte de estos datos iniciales, editados con Excel para separar los parámetros por columnas de forma que el programa pueda reconocerlos correctamente.

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

Además, es fundamental leer ejecutarlo paso a paso.

## Estructura
```
/data
  - datos_transformados2.csv (datos sin procesar y procesados)

/src
  /notebooks
    - Notebooks Jupyter con los experimentos y visualizaciones

/docs
  - Documentación adicional en pdf

/public
  - Carpeta donde las páginas de GitLab escribirán el sitio web estático.
  - index.html La documentación en formato enriquecido (por ejemplo, HTML, Markdown, JavaScript) se completará public.
```

## Contacto
- Pablo Sáez Morales - pablo.saezmorales@studio.unibo.it
- Antonio Ruiz Jiménez - antonio.ruizjimenez@studio.unibo.it
- Candela Esparrica Torrecilla - candela.torrecilla2@studio.unibo.it
