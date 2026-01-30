# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**procesos_SIG** - Scripts de ayuda para el procesamiento de información geoespacial (Helper scripts for geospatial information processing).

This is a Jupyter Notebook-based project for geospatial analysis focused on Mexico, particularly CDMX (Mexico City). The project performs urban accessibility analysis, census data processing, and geospatial validation.

## Development Setup

```bash
# Create and activate virtual environment
python -m venv venv
venv\Scripts\activate  # Windows

# Install dependencies
pip install -r requirements.txt

# Run notebooks
jupyter notebook notebooks/
```

## Key Dependencies

- **Geospatial**: geopandas, shapely, pyproj, pyogrio, folium
- **Network analysis**: osmnx, networkx, city2graph, rustworkx
- **Data processing**: pandas, numpy, scipy, scikit-learn
- **Data I/O**: pyarrow, requests, beautifulsoup4, dbfread

## Architecture

### Notebooks Directory Structure

- `nb_convertir_dbf.ipynb` - Converts INEGI census data (CPV 2020) from DBF to CSV format
- `nb_isocronas*.ipynb` - Isochrone analysis using OSMnx and street networks
- `nb_isodistancias_Pilares.ipynb` - Walking distance accessibility analysis around CDMX Pilares locations
- `nb_validacion_geoespacializacion.ipynb` - Geocoding validation using INEGI Marco Geoestadístico
- `nb_proceso_creacion_etiquetas_zonificacionsecundaria.ipynb` - Zone labeling for territorial divisions

### Data Flow Pattern

1. **Data acquisition** - Fetch from APIs (CDMX Pilares, OpenStreetMap via OSMnx) or local files
2. **Coordinate transformation** - Reproject between CRS (commonly EPSG:4326, EPSG:6372)
3. **Spatial analysis** - Network analysis, spatial joins, isochrone/isodistance calculations
4. **Visualization** - Generate interactive Folium maps or GeoJSON outputs

### Caching Strategy

Large API responses are cached in `notebooks/cache/` to avoid repeated requests.

## External Data Sources

- **INEGI Marco Geoestadístico 2024**: Mexican administrative boundaries (states, municipalities, localities)
- **CDMX Pilares API** (pilares.cdmx.gob.mx): Social/cultural center locations
- **OpenStreetMap**: Street networks via OSMnx
- **GTFS feeds**: Public transit data

## File Conventions

- GeoPackage (*.gpkg), GeoJSON (*.geojson), and JSON files are gitignored due to size
- Processed data outputs go in `notebooks/datos/`
