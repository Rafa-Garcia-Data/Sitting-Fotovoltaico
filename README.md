# Photovoltaic Land Viability Analysis in La Sagra (Toledo) :sun_with_face::battery:

A high-performance **Business Intelligence** and **GIS** tool built with **Power BI** and **QGIS** to evaluate the technical, geospatial, and economic viability of cadastral land plots for photovoltaic solar farm development in La Sagra region (Toledo, Spain).

This project bridges GIS spatial analysis and corporate data modeling. It moves beyond simple point coordinates to process cadastral centroids in **WGS84 (EPSG:4326)**, modeling plot area, topographics, and key financial parameters to provide an interactive dashboard for renewable energy site selection.

![Dashboard Overview](docs/dashboard-preview.png)

## Tecnologías :zap:

<img alt="Static Badge" src="https://img.shields.io/badge/Power_BI-F2C811?style=plastic&logo=powerbi&logoColor=black"> <img alt="Static Badge" src="https://img.shields.io/badge/QGIS-red?style=plastic&logo=Qgis"> <img alt="Static Badge" src="https://img.shields.io/badge/DAX-orange?style=plastic&logo=dax"> <img alt="Static Badge" src="https://img.shields.io/badge/Power_Query_(M)-purple?style=plastic"> <img alt="Static Badge" src="https://img.shields.io/badge/EPSG:4326-blue?style=plastic">

[![My Skills](https://skillicons.dev/icons?i=python,git,vscode&theme=light)](https://skillicons.dev)

## Cómo funciona :bulb:

1. **Topographic Assessment:** Classification by terrain slope (`Aptitud_Topografica`).
2. **Estimated Power Capacity:** Calculated dynamically based on available plot area ($0.5 \text{ MWp/ha}$).
3. **Financial Estimation:** Yearly land lease cost projections ($1,500 \text{ €/ha/year}$).
4. **Technical Suitability Score (`Score_Viabilidad`):** An aggregated score ranging from 0 to 100 to prioritize high-yield plots.
5. **Interactive Dashboard:** Cross-filter maps, KPIs and tables in real time to evaluate each plot's viability.

### Requisitos

- Power BI Desktop
- QGIS (preprocesamiento geoespacial)
- Datos catastrales de La Sagra (Toledo) en EPSG:4326

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