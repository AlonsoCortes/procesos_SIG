# procesos_SIG

Serie de scripts de ayuda para el procesamiento de información geoespacial, enfocados en análisis urbano y de accesibilidad en México, particularmente en la Ciudad de México (CDMX).

## Descripción

Este repositorio contiene notebooks de Jupyter para realizar análisis geoespaciales que incluyen:

- **Análisis de isocronas e isodistancias**: Cálculo de zonas de accesibilidad peatonal utilizando redes viales de OpenStreetMap
- **Procesamiento de datos censales**: Conversión de datos del Censo de Población y Vivienda 2020 (INEGI) de formato DBF a CSV
- **Validación geoespacial**: Verificación de geocodificación mediante intersección con el Marco Geoestadístico de INEGI
- **Etiquetado de zonificación**: Creación de etiquetas para divisiones territoriales secundarias

## Requisitos

- Python 3.x
- Entorno virtual recomendado

## Instalación

```bash
# Clonar el repositorio
git clone https://github.com/AlonsoCortes/procesos_SIG.git
cd procesos_SIG

# Crear y activar entorno virtual
python -m venv venv
venv\Scripts\activate  # Windows
# source venv/bin/activate  # Linux/Mac

# Instalar dependencias
pip install -r requirements.txt
```

## Uso

```bash
# Ejecutar Jupyter Notebook
jupyter notebook notebooks/
```

## Estructura del Proyecto

```
procesos_SIG/
├── notebooks/
│   ├── cache/                    # Respuestas de API almacenadas en caché
│   ├── datos/                    # Datos geoespaciales procesados
│   ├── nb_convertir_dbf.ipynb    # Conversión de datos censales DBF a CSV
│   ├── nb_isocronas*.ipynb       # Análisis de isocronas
│   ├── nb_isodistancias_Pilares.ipynb  # Isodistancias para Pilares CDMX
│   ├── nb_validacion_geoespacializacion.ipynb  # Validación de geocodificación
│   └── nb_proceso_creacion_etiquetas_zonificacionsecundaria.ipynb
├── requirements.txt
└── README.md
```

## Notebooks Principales

### nb_convertir_dbf.ipynb
Convierte archivos DBF del Censo de Población y Vivienda 2020 (INEGI) a formato CSV. Procesa categorías demográficas como: características económicas, discapacidad, educación, etnicidad, fecundidad, vivienda, migración, entre otras.

### nb_isocronas_pilares_CDMX.ipynb
Genera zonas de accesibilidad (isocronas) alrededor de puntos de interés utilizando datos de OpenStreetMap y la biblioteca OSMnx. Crea mapas interactivos con Folium.

### nb_isodistancias_Pilares.ipynb
Analiza la accesibilidad peatonal a 750 metros alrededor de los 303+ Pilares (centros socioculturales) de la CDMX. Obtiene datos de la API oficial de Pilares CDMX.

### nb_validacion_geoespacializacion.ipynb
Valida resultados de geocodificación mediante intersección espacial con límites administrativos del Marco Geoestadístico 2024 de INEGI (localidades, municipios, estados).

## Fuentes de Datos

- **INEGI Marco Geoestadístico 2024**: Límites administrativos de México
- **API Pilares CDMX** (pilares.cdmx.gob.mx): Ubicaciones de centros socioculturales
- **OpenStreetMap**: Redes viales vía OSMnx
- **Datos GTFS**: Información de transporte público

## Dependencias Principales

- **Geoespaciales**: geopandas, shapely, pyproj, folium
- **Análisis de redes**: osmnx, networkx, city2graph
- **Procesamiento de datos**: pandas, numpy, scipy
