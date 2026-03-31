# 🌏 Bangladesh Division-Wise Climate Analysis (2019–2025)

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Data%20Source-ERA5%20Reanalysis-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white" />
  <img src="https://img.shields.io/badge/Domain-Geospatial%20%7C%20Climate-2E8B57?style=for-the-badge" />
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" />
</p>

<p align="center">
  A Python pipeline that processes <strong>ERA5 reanalysis NetCDF files</strong> and produces clean, division-level monthly climate statistics for Bangladesh — covering <strong>temperature</strong> and <strong>precipitation</strong> from 2019 to 2025.
</p>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Repository Structure](#-repository-structure)
- [Dataset](#-dataset)
- [How to Reproduce](#-how-to-reproduce)
- [Dependencies](#-dependencies)
- [Skills Demonstrated](#-skills-demonstrated)

---

## 🔍 Overview

This project demonstrates end-to-end **geospatial climate data processing** using Python. The pipeline ingests raw ERA5 monthly reanalysis files (NetCDF format), spatially aggregates them over Bangladesh's 8 administrative divisions using a GADM shapefile, and outputs a tidy CSV ready for analysis or visualization.

| Feature | Detail |
|---|---|
| **Geography** | Bangladesh — 8 administrative divisions |
| **Temporal range** | January 2019 – 2025 (monthly) |
| **Climate variables** | 2 m air temperature, total precipitation |
| **Data source** | [ERA5 Monthly Means — Copernicus CDS](https://cds.climate.copernicus.eu/) |
| **Output format** | Tidy CSV, one row per division × month |

---

## 📁 Repository Structure

```
Geospatial-climate-analysis-python/
│
├── produce_bd_division_monthly.py   # Main processing script
├── bd_division_monthly_2019_2025.csv  # Pre-generated output dataset
├── Analysis.zip                     # Supplementary analysis files
└── README.md
```

---

## 📊 Dataset

The output file `bd_division_monthly_2019_2025.csv` contains **division-level monthly climate averages** and is ready to use without running the pipeline.

### Schema

| Column | Type | Description |
|---|---|---|
| `division` | `string` | Name of the Bangladesh division |
| `year` | `int` | Year (2019–2025) |
| `month` | `int` | Month (1 = January … 12 = December) |
| `mean_t2m_C` | `float` | Mean 2 m air temperature (°C) |
| `total_precip_mm` | `float` | Total monthly precipitation (mm) |

### Sample rows

```
division,year,month,mean_t2m_C,total_precip_mm
Barisal,2019,1,19.78,0.06
Chittagong,2019,1,19.47,0.92
Dhaka,2019,1,18.86,0.36
Khulna,2019,1,18.95,0.27
Sylhet,2019,1,18.65,0.42
```

---

## 🚀 How to Reproduce

### 1 — Download ERA5 data

1. Register (free) at [Copernicus Climate Data Store](https://cds.climate.copernicus.eu/).
2. Navigate to **ERA5 Monthly Averaged Reanalysis → Single Levels**.
3. Select variables: **2m Temperature (t2m)** and **Total Precipitation (tp)**.
4. Select years **2019–2025**, all months.
5. Download in **NetCDF (.nc)** format.

### 2 — Organise files

```
project/
├── ERA5/
│   ├── era5_t2m_monthly_2019.nc
│   ├── era5_tp_monthly_2019.nc
│   ├── ...
│   ├── era5_t2m_monthly_2025.nc
│   └── era5_tp_monthly_2025.nc
└── data/
    └── gadm41_BGD_1.shp   (+ companion files)
```

Download the **Bangladesh Level-1 shapefile** from [GADM](https://gadm.org/download_country_v3.html) and place it in `data/`.

### 3 — Configure paths

Open `produce_bd_division_monthly.py` and update the three path constants at the top:

```python
ERA5_DIR  = r"PATH_TO_YOUR_ERA5_FOLDER"
DIV_SHAPE = r"PATH_TO_YOUR_SHAPEFILE/gadm41_BGD_1.shp"
OUT_CSV   = r"PATH_TO_OUTPUT/bd_division_monthly_2019_2025.csv"
```

### 4 — Install dependencies

```bash
pip install xarray rioxarray geopandas pandas numpy rasterstats
```

### 5 — Run

```bash
python produce_bd_division_monthly.py
```

The script writes `bd_division_monthly_2019_2025.csv` to the path specified in `OUT_CSV`.

---

## 📦 Dependencies

| Package | Purpose |
|---|---|
| `xarray` | Reading and slicing NetCDF files |
| `rioxarray` | Geospatial extensions for xarray (CRS, clipping) |
| `geopandas` | Loading and managing the division shapefile |
| `rasterstats` | Zonal statistics — aggregating raster data over polygons |
| `pandas` | Data wrangling and CSV export |
| `numpy` | Numerical operations |

---

## 🛠 Skills Demonstrated

- **Geospatial data processing** — working with NetCDF rasters and vector shapefiles in the same pipeline
- **Zonal statistics** — spatial aggregation of continuous raster fields over administrative polygons
- **Climate data engineering** — handling ERA5 reanalysis products, unit conversions, and time-series structuring
- **Python automation** — reproducible, end-to-end data pipeline with configurable paths
- **Tidy data principles** — producing analysis-ready output with a clean, long-format schema

---

<p align="center">
  Made with ❤️ using ERA5 reanalysis data — <a href="https://cds.climate.copernicus.eu/">Copernicus Climate Change Service</a>
</p>


