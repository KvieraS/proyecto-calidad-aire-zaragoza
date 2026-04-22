# Proyecto final: Calidad del aire en Zaragoza

## Descripción del proyecto

Este proyecto tiene como objetivo analizar la calidad del aire en Zaragoza a partir de datos históricos de contaminación atmosférica y variables meteorológicas, combinando un análisis exploratorio realizado con Python y una visualización interactiva desarrollada en Power BI.

El trabajo se centra en estudiar la evolución temporal de distintos contaminantes, comparar estaciones de medición, identificar diferencias entre contaminantes y construir un dashboard que facilite la interpretación de los datos de forma clara y visual.

El periodo analizado comprende los años **2020, 2021, 2022 y 2023**.

---

## Objetivos

Los objetivos principales del proyecto han sido:

- Extraer, unificar y limpiar los datos de calidad del aire de Zaragoza.
- Integrar la información meteorológica para enriquecer el análisis.
- Realizar un análisis exploratorio de datos con Python.
- Identificar patrones temporales, diferencias entre contaminantes y comportamiento por estación.
- Construir un dashboard en Power BI con una estructura clara y visualmente limpia.
- Presentar conclusiones relevantes a partir de los datos analizados.

---

## Fuentes de datos

Para este proyecto se han utilizado dos grandes bloques de información:

### 1. Datos de calidad del aire
Datos horarios de contaminación atmosférica correspondientes a Zaragoza para los años:

- 2020
- 2021
- 2022
- 2023

Contaminantes trabajados:

- CO
- NO
- NO2
- O3
- PM10
- PM2.5
- SO2

### 2. Datos meteorológicos
Datos diarios descargados de AEMET para Zaragoza, integrados posteriormente con los datos de contaminación.

Variables meteorológicas principales utilizadas:

- temperatura media
- temperatura mínima
- temperatura máxima
- precipitación
- velocidad media del viento
- racha máxima
- insolación
- presión máxima
- presión mínima

---

## Herramientas utilizadas

### Python
Utilizado para la extracción, limpieza, transformación, análisis exploratorio y preparación del dataset final.

Librerías principales:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `requests`
- `pathlib`

### Power BI
Utilizado para el modelado final y la creación del dashboard interactivo.

### Otras herramientas
- Visual Studio Code
- Jupyter Notebook
- Git
- GitHub

---

## Estructura del proyecto

```text
proyecto-final-calidad-aire-zaragoza/
│
├── dashboard/
│   └── dashboard_calidad_aire_zaragoza.pbix
│
├── data/
│   ├── raw/
│   │   └── aire_miteco/
│   │       ├── aire_2020.csv
│   │       ├── aire_2021.csv
│   │       ├── aire_2022.csv
│   │       └── aire_2023.csv
│   │
│   └── processed/
│       ├── aire_total_unido.csv
│       ├── aire_zaragoza_ancho.csv
│       ├── aire_zaragoza_long.csv
│       ├── aemet_zaragoza_diario.csv
│       ├── dataset_final_aire_meteo_zaragoza.csv
│       ├── dataset_final_aire_meteo_zaragoza_limpio.csv
│       ├── resumen_contaminante.csv
│       ├── tabla_correlaciones_meteorologicas.csv
│       ├── tabla_estacion_contaminante.csv
│       ├── tabla_resumen_final.csv
│       └── top_estaciones.csv
│
├── notebooks/
│   ├── 01_extraccion_y_carga.ipynb
│   ├── 02_limpieza_y_transformacion.ipynb
│   ├── 03_eda_y_estadistica.ipynb
│   └── 04_conclusiones_y_exportacion.ipynb
│
├── reports/
│   ├── informe_analisis.md
│   └── images/
│
├── src/
│   ├── funciones_eda.py
│   ├── funciones_limpieza.py
│   └── funciones_visualizacion.py
│
├── README.md
└── requirements.txt
```
Proceso de trabajo en Python
1. Extracción y carga de datos

En una primera fase se cargaron los archivos anuales de calidad del aire, comprobando:

número de archivos encontrados
separador correcto
codificación
dimensiones de cada fichero

Posteriormente se unificaron en un único dataset bruto.

También se descargaron los datos meteorológicos de AEMET y se almacenaron en un fichero independiente para su posterior integración.

2. Limpieza y transformación de datos

Durante la fase de transformación y limpieza se realizaron, entre otras, las siguientes tareas:

filtrado de registros correspondientes a la provincia de Zaragoza
selección de contaminantes relevantes
transformación de formato ancho a formato largo
creación de una columna única de valor
construcción de columnas temporales:
fecha
datetime
año
mes
día
estación del año
tipado correcto de columnas numéricas y temporales
tratamiento de nulos
revisión de duplicados
homogeneización del nombre de contaminantes
integración de datos meteorológicos diarios con el dataset de contaminación

También se tuvo en cuenta la existencia de distintas unidades de medida según el contaminante:

CO en mg/m3
resto de contaminantes en µg/m3

Esto fue especialmente importante para evitar comparaciones incorrectas.

3. Análisis exploratorio de datos

Con el dataset ya limpio y estructurado se realizó un análisis exploratorio que incluyó:

revisión del rango temporal
análisis de nulos
identificación de contaminantes y estaciones presentes
estadísticos descriptivos:
media
mediana
mínimo
máximo
desviación estándar
evolución temporal de los contaminantes
comparativa entre estaciones
análisis mensual
relación entre contaminación y variables meteorológicas
generación de tablas resumen para apoyo al dashboard
4. Exportación de datasets procesados

Finalmente se exportaron distintos archivos procesados para:

facilitar el análisis intermedio
reutilizar resultados
alimentar el dashboard de Power BI
disponer de tablas resumen limpias para comparativas
Trabajo realizado en Power BI

Tras la fase de análisis en Python, se construyó un dashboard en Power BI orientado a la exploración visual y a la comparación de resultados.

Modelado de datos

Se trabajó con una tabla principal y varias dimensiones:

Tabla principal
dataset_final_aire_meteo_zaragoza_limpio
Tablas dimensión
DimContaminante
DimEstacion
DimFecha

Se crearon relaciones entre dimensiones y tabla de hechos para facilitar el filtrado y la navegación del modelo.

Medidas DAX

Se desarrollaron medidas para:

concentración media
concentración máxima
registros analizados
número de estaciones
número de contaminantes
medidas específicas para CO
textos dinámicos para tarjetas
medidas comparativas para contaminantes en µg/m3

También se organizó el modelo con carpetas de medidas para mantener una estructura clara:

Auxiliares
Concentración
CO
Comparativa
Estación
Registros
Diseño del dashboard

Se diseñó una plantilla visual homogénea para todas las páginas:

cabecera superior con degradado gris-rojo
panel lateral de filtros
fondo gris claro
visualizaciones limpias y consistentes
uso de una paleta basada en rojo para mantener coherencia visual

Además, se tuvo en cuenta la legibilidad y la claridad de lectura durante el diseño.

Hojas del dashboard
1. Resumen

Esta página funciona como portada del análisis.

Incluye:

filtros principales
tarjetas resumen
evolución mensual del contaminante seleccionado
comparativa de concentración media por estación
2. Comparativa por contaminante

Esta página está orientada a comparar contaminantes entre sí.

Incluye:

contaminantes analizados
mayor media y mayor máxima en µg/m3
comparación de concentración media por contaminante
bloque específico para CO
tabla resumen por contaminante

Se separó CO del resto para evitar comparaciones engañosas, ya que utiliza una unidad distinta.

3. Análisis por estación

Esta página permite comparar el comportamiento de las diferentes estaciones.

Incluye:

filtros de contaminante, año y estación del año
evolución mensual por estación
tabla resumen por estación
tarjetas con métricas generales del contexto filtrado
Principales hallazgos

A lo largo del proyecto se observaron varios aspectos relevantes:

Existen diferencias claras entre contaminantes en términos de concentración media y concentración máxima.
CO requiere tratamiento separado debido a su unidad de medida diferente.
Algunas estaciones presentan concentraciones medias superiores a otras de forma consistente.
La evolución temporal mensual permite detectar patrones y cambios más claros que la visualización diaria.
La comparación por estación ayuda a identificar comportamientos diferenciados según ubicación.
La integración con datos meteorológicos aporta contexto adicional para interpretar mejor la evolución de la contaminación.
Principales dificultades encontradas

Durante el desarrollo del proyecto aparecieron varios retos técnicos:

lectura e integración de múltiples ficheros anuales
transformación de datos horarios desde formato ancho a formato largo
tratamiento correcto de fechas y horas
diferencias de unidad entre contaminantes
descarga de datos meteorológicos desde AEMET
limitaciones de rango temporal en la API de AEMET
conflicto entre formatos numéricos al importar tablas resumen en Power BI
organización de medidas DAX y limpieza del modelo

Cada uno de estos problemas se fue resolviendo progresivamente hasta obtener un flujo estable de trabajo.

Cómo ejecutar o revisar el proyecto
Python
1ºClonar el repositorio.
2ºInstalar dependencias:
```text
pip install -r requirements.txt
```
3ºEjecutar los notebooks en orden:
01_extraccion_y_carga.ipynb
02_limpieza_y_transformacion.ipynb
03_eda_y_estadistica.ipynb
04_conclusiones_y_exportacion.ipynb


Power BI
1ºAbrir el archivo:
```text
dashboard/dashboard_calidad_aire_zaragoza.pbix
```
Revisar las tres páginas del dashboard:
Resumen
Comparativa por contaminante
Análisis por estación


Conclusión

Este proyecto ha permitido construir un flujo completo de análisis de datos, desde la extracción y preparación en Python hasta la visualización final en Power BI.

Además del análisis exploratorio, el proyecto ha servido para trabajar tareas habituales de un entorno real de análisis:

limpieza y transformación de datos
integración de fuentes heterogéneas
modelado para visualización
diseño de dashboards
interpretación de resultados

El resultado final es un proyecto completo y estructurado que combina análisis técnico y presentación visual clara.

Autor

Kevin Jesús Santoveña Viera

GitHub: KvieraS
