<h1 align="center"> IA explicable aplicada a la Telerehabilitación </h1>

Este proyecto tiene como objetivo desarrollar modelos de aprendizaje automático para clasificar distintos gestos realizados por pacientes en un entorno de telerehabilitación. Además, se busca determinar si estos gestos son ejecutados correctamente y proporcionar explicaciones sobre las decisiones tomadas por los modelos.

<p align="center">
  <img src="/Imagenes/gestures.png" width="400" title="Ejercicios rehabilitación">
</p>

## 📚 Tutorial
### 🚀 Despliegue de la aplicación en local
1. Clona este repositorio
```
git clone https://github.com/nmartinser/Telerehabilitation_Interpretability
```
2. Instala las dependencias:
```
pip install -r requirements.txt
```
3. Para desplegar la aplicación en local:
```
streamlit run app.py
```

### 🖥️ Cómo usar la aplicación
**1. Prepara los datos:**

* En la carpeta `dataset` de este repositorio, encontrarás los datos de los videos de un paciente, organizados por gestos.
* Cada subcarpeta contiene archivos .txt que corresponden a las repeticiones de un gesto específico.
* Selecciona una de estas subcarpetas para cargar los datos.

**2. Carga los datos en la aplicación:**

* Una vez iniciada la aplicación, utiliza el menú desplegable para seleccionar y cargar los datos correspondientes a un movimiento específico.
* La aplicación procesará los datos y mostrará las predicciones realizadas por los algoritmos de aprendizaje automático, incluyendo la clasificación del gesto para identificar el tipo de movimiento realizado por el paciente, el estado de ejecución que evalúa si cada repetición es correcta o incorrecta, y explicaciones para las ejecuciones incorrectas que detallan por qué ciertas repeticiones fueron clasificadas como tales, ayudando al paciente a identificar áreas de mejora en sus gestos.

## 📁 Descripción del repositorio

### 📓 Notebooks

Este subdirectorio contiene los notebooks de Jupyter (.ipynb) utilizados para el procesamiento de datos y la creación de modelos de clasificación, así como un archivo adicional *function.py* que incluye funciones utilizadas tanto por los notebooks como por el programa principal *app.py*.

A continuación se describen los notebooks:

<details>
<summary>1. Procesar los datos de los videos</summary>
  
* **Descripción**: Este notebook procesa archivos de datos de video en formato crudo, extrayendo información esencial sobre cada grabación, como la ID del sujeto, el número de repetición, la precisión del gesto, y la posición de los puntos clave del cuerpo. Seguidamente calcula el ángulo entre disintos puntos del cuepro, y por último se realizan cálculos estadísticos (mínimo, máximo, desviación estándar, media, etc.) sobre los ángulos.  
* **Salida**: Genera tres archivos CSV:
  - `raw_pacientes.csv`: Contiene información detallada sobre cada grabación.
  - `angles.csv`: Incluye ángulos calculados entre keypoints.
  - `medidasPerRepetition.csv`: contiene una fila por repetición y gesto, que incluye estadísticas para cada ángulo calculado.

</details>

<details><summary>\textcolor{Cerulean}{2. Fase 1: Clasificación del movimiento}</summary>

* **Descripción**: Implementa, entrena y evalúa modelos de clasificación para identificar el tipo de gesto realizado por el paciente. 
* **Salida**: `modelo_fase1_copy.sav` Archivo que guarda el pipeline completo de clasificación entrenado, compuesto por:
  - Selección de variables: Utilizando `SelectKBest`.
  - Modelo de clasificación: Algoritmo de aprendizaje automático para predecir el tipo de movimiento.
</details>

<details><summary>\textcolor{Orchid}3. Fase 2: Clasificación de la ejecución del movimiento</summary>

* **Descripción**: Para cada gesto identificado en la Fase 1, se desarrollan modelos de clasificación específicos para determinar si cada repetición es ejecutada de manera correcta o incorrecta.
* **Salida**: Nueve archivos `.sav`, uno para cada gesto, que almacenan el pipeline completo de clasificación entrenado, incluyendo tanto el preprocesamiento como el modelo final.
  
</details>

<p align="center">
  <img src="/Imagenes/esquema_modelos.png" width="600" title="Esquema fases">
</p>

### 🗂️ Dataset

Esta carpeta contiene los datos de un paciente, organizados en subcarpetas separadas para cada gesto registrado durante las sesiones de telerehabilitación. Dentro de cada subcarpeta, se encuentra un archivo .txt por cada repetición, que almacena los datos extraídos de los videos.

### 📋 Resultados
Aquí se almacenan los archivos intermedios y resultados finales generados durante el procesamiento de datos y el entrenamiento de los modelos.

### ⚙️ Archivos de configuración

* *app.py*: programa principal de la aplicación.
 
* *.gitignore*: listas de archivos y carpetas que deben ser ignorados por el control de versiones.

* *requirements.txt*: lista de dependencias necesarias para la instalación.
