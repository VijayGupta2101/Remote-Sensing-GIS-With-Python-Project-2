# Remote-Sensing-GIS-With-Python-Project-2
# Raster and Vector Integration using GeoPandas and Rasterio

## Overview

This project demonstrates the integration of raster and vector geospatial data using Python. It loads an India Digital Elevation Model (DEM) raster and India district boundary shapefile, aligns their coordinate reference systems (CRS), and visualizes both datasets together.

The project is useful for learning fundamental GIS concepts such as:

* Raster Data Handling
* Vector Data Handling
* Coordinate Reference Systems (CRS)
* Raster and Vector Overlay
* Geospatial Data Visualization
* DEM Analysis

---

## Technologies Used

* Python
* GeoPandas
* Rasterio
* NumPy
* Pandas
* Matplotlib

---

## Dataset

### Vector Data

* India District Boundary Shapefile (.shp)

### Raster Data

* India DEM Raster (.tif)

---

## Project Workflow

### 1. Import Required Libraries

The notebook imports essential geospatial and visualization libraries.

### 2. Load Vector Data

The India district boundary shapefile is loaded using GeoPandas.

### 3. Load Raster Data

The India DEM raster is loaded using Rasterio.

### 4. Check Coordinate Reference Systems

The CRS of both raster and vector datasets is verified.

### 5. Reproject Vector Data

The vector layer is transformed to match the raster CRS.

### 6. Handle Large Raster Files

Since the raster dataset is large, a lower-resolution version is generated using Rasterio resampling techniques to reduce memory consumption.

### 7. Raster and Vector Visualization

The DEM raster is displayed using a terrain color map, and district boundaries are overlaid for spatial analysis.

---

## Features

* Load and visualize raster datasets
* Load and visualize vector datasets
* CRS validation and transformation
* Memory-efficient raster visualization
* Raster and vector overlay analysis
* GIS data integration workflow

---

## Output

The final output displays:

* India DEM Raster
* India District Boundaries
* Combined Raster and Vector Visualization

This allows users to understand how vector boundaries relate to elevation data across India.

---

## Installation

Install the required libraries:

```bash
pip install geopandas rasterio matplotlib pandas numpy
```

---

## Run the Project

1. Download the raster (.tif) and shapefile (.shp) datasets.
2. Update the file paths in the notebook.
3. Open the notebook:

```bash
jupyter notebook Third.ipynb
```

4. Run all cells.

---

## Learning Outcomes

By completing this project, users will learn:

* GIS data processing in Python
* Raster visualization techniques
* Vector boundary analysis
* CRS transformations
* Handling large geospatial datasets
* Raster and Vector Integration concepts

---

## Author

Developed as a geospatial data analysis and GIS learning project using Python, GeoPandas, and Rasterio.
