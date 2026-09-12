# Photovoltaic Land Viability Analysis in La Sagra (Toledo) :sun_with_face::battery:

Una herramienta de alto rendimiento de **Business Intelligence** y **SIG**, desarrollada con **Power BI** y **QGIS**, para evaluar la viabilidad técnica, geoespacial y económica de parcelas catastrales destinadas al desarrollo de parques solares fotovoltaicos en la comarca de La Sagra (Toledo, España).

Este proyecto integra el análisis espacial SIG con el modelado de datos corporativos. Va más allá de las simples coordenadas puntuales para procesar centroides catastrales en el sistema **WGS84 (EPSG:4326)**, modelando la superficie de la parcela, la topografía y parámetros financieros clave con el fin de ofrecer un panel interactivo para la selección de emplazamientos de energías renovables.

ENG

A high-performance **Business Intelligence** and **GIS** tool built with **Power BI** and **QGIS** to evaluate the technical, geospatial, and economic viability of cadastral land plots for photovoltaic solar farm development in La Sagra region (Toledo, Spain).

This project bridges GIS spatial analysis and corporate data modeling. It moves beyond simple point coordinates to process cadastral centroids in **WGS84 (EPSG:4326)**, modeling plot area, topographics, and key financial parameters to provide an interactive dashboard for renewable energy site selection.

![Dashboard Overview](docs/dashboard-powerbi.png)

## Tecnologías :zap:

<img alt="Static Badge" src="https://img.shields.io/badge/Power_BI-F2C811?style=plastic&logo=powerbi&logoColor=black"> <img alt="Static Badge" src="https://img.shields.io/badge/QGIS-red?style=plastic&logo=Qgis"> <img alt="Static Badge" src="https://img.shields.io/badge/DAX-orange?style=plastic&logo=dax">

[![My Skills](https://skillicons.dev/icons?i=python,git,vscode&theme=light)](https://skillicons.dev)

## Cómo funciona (demo) :bulb:

1. **Abre el dashboard:** Abre `powerbi/[dashboard].pbix` con **Power BI Desktop**, o accede a la versión publicada en **Power BI Service** mediante el enlace compartido.
2. **Explora el mapa:** Navega por La Sagra sobre el mapa de satélite (Bing Aerial/Hybrid) y localiza los centroides catastrales de cada parcela.
3. **Inspecciona una parcela:** Pasa el cursor o haz clic sobre cualquier centroide para ver su tooltip: referencia catastral (`nationalCadastralReference`), superficie exacta y potencia estimada.
4. **Filtra todo en tiempo real:** Tablas, KPIs y el mapa quedan sincronizados (cross-filtering) para evaluar cada emplazamiento al instante.
5. **Prioriza parcelas:** Usa el gradiente de `Score_Viabilidad` (0–100) y los colores por aptitud topográfica para preseleccionar las de alto rendimiento.

### Requisitos

- **Power BI Desktop** (para abrir/editar el `.pbix`).
- Cuenta gratuita de **Power BI Service** (solo para compartir la demo online).
- **QGIS** únicamente se usa en el preprocesamiento de datos; **no es necesario** para la demo.
- Datos catastrales de La Sagra (Toledo) en EPSG:4326.

## Arquitectura :building_construction:

```text
Datos catastrales (La Sagra, Toledo)
    │  Coordenadas en UTM (EPSG:25830)
    ▼
QGIS - Procesamiento Geoespacial
    │  Reproyección a WGS84 (EPSG:4326) + limpieza de datos espaciales
    ▼
Power Query (M) - Data Transformation
    │  Locale formatting y data type casting
    ▼
Power BI Data Model (DAX + Parámetros dinámicos)
    │  Potencia estimada (0.5 MWp/ha) y arrendamiento (1,500 €/ha/year)
    ▼
Score_Viabilidad (0-100) + Conditional Formatting
    │  Gradiente de color por idoneidad y clasificación topográfica
    ▼
Dashboard Interactivo (Mapas, KPIs, Tooltips, Cross-Filtering)
```

- **Geospatial Mapping:** Interactive map visualization with precise centroid placement over high-resolution satellite imagery (Bing Aerial/Hybrid basemaps).
- **Conditional Formatting & Legend Clustering:** Visual categorization by suitability score (gradient colors) and topographic classification.
- **Interactive Tooltips:** Instant hover details displaying unique cadastral references (`nationalCadastralReference`), exact area, and power potential.
- **Cross-Filtering:** Fully synchronized tables, KPIs, and geographic visuals for real-time site evaluation.

## Estructura del proyecto :electric_plug:

```text
Sitting-Fotovoltaico/
├── .gitignore                     # Configuración de exclusiones de Git
├── README.md                      # Documentación principal del repositorio
├── docs/
│   └── dashboard-preview.png      # Captura de pantalla del dashboard
├── data/                          # Datos catastrales procesados (EPSG:4326)
├── qgis/
│   └── [proyecto].qgz             # Proyecto QGIS con capas y simbología
└── powerbi/
    ├── [dashboard].pbix           # Modelo Power BI con medidas y DAX
    └── [conexiones].pbix          # Transformaciones Power Query (M)
```

## Resultados :vertical_traffic_light:

- <ins>Selección de emplazamientos</ins> para parques fotovoltaicos basada en datos técnicos, geoespaciales y económicos.
- Un solo <ins>dashboard interactivo</ins> para evaluar la viabilidad de cada parcela en tiempo real.
- Modelo de análisis <ins>escalable</ins> a cualquier región con datos catastrales.
- <ins>Score_Viabilidad</ins> (0-100) que prioriza de forma objetiva las parcelas de alto rendimiento.
