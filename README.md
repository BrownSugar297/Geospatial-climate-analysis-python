# Geospatial-climate-analysis-python
# Bangladesh Climate Data (2019-2025)

This repository contains a Python script and the resulting CSV dataset for **Bangladesh division-wise monthly climate data** (temperature and precipitation) for **2019-2025**.

The purpose of this project is to demonstrate **geospatial data analysis and climate data processing skills** using Python.

---
## **Files**

- `produce_bd_division_monthly.py` – Python script to process ERA5 NetCDF files and generate CSV.  
- `bd_division_monthly_2019_2025.csv` – Output dataset containing division-wise monthly averages.  

---

## **CSV Structure**

| Column             | Description                         |
|-------------------|-------------------------------------|
| `division`         | Name of the division (Bangladesh)   |
| `year`             | Year (2019 or 2025)                 |
| `month`            | Month (1–12)                        |
| `mean_t2m_C`       | Mean 2m temperature in Celsius      |
| `total_precip_mm`  | Total monthly precipitation in mm   |

---

## **How to Reproduce the CSV**

1. **Register and download ERA5 data**  
   - Go to [Copernicus Climate Data Store (CDS)](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-single-levels-monthly-means?tab=overview)  
   - Create a free account if you don’t have one.  
   - Select **Monthly Aggregates** → **Single Levels** → **2m Temperature (t2m)** and **Total Precipitation (tp)**.  
   - Select the years **2019 - 2025**.  
   - Download files in **NetCDF (.nc) format**.

2. **Organize files locally**  
   - Create a folder named `ERA5` in your project directory.  
   - Place the downloaded files there, and rename if necessary:  
     - `era5_t2m_monthly_2024.nc`  
     - `era5_tp_monthly_2024.nc`  
     - `era5_t2m_monthly_2025.nc`  
     - `era5_tp_monthly_2025.nc`  

3. **Download Bangladesh divisions shapefile**  
   - Use [GADM](https://gadm.org/download_country_v3.html) to get Bangladesh Level-1 shapefile.  
   - Place the shapefile in a `data/` folder.

4. **Update paths in the script**  
   ```python
   ERA5_DIR = r"PATH_TO_YOUR_ERA5_FOLDER"
   DIV_SHAPE = r"PATH_TO_YOUR_SHAPEFILE/gadm41_BGD_1.shp"
   OUT_CSV = r"PATH_TO_OUTPUT/bd_division_monthly_2024_2025.csv"
Install Python dependencies

bash:::
pip install xarray rioxarray geopandas pandas numpy rasterstats
Run the script

bash:::
python produce_bd_division_monthly.py
Check the output CSV

The script generates bd_division_monthly_2024_2025.csv containing all division-wise monthly averages.

Skill Demonstrated
Geospatial Data Analysis

Climate Data Processing

Python Automation & Data Aggregation


