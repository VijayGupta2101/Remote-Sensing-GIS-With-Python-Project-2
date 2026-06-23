# India District-Level Raster Analysis

A geospatial analysis notebook that overlays raster data (DEM/LULC) on India's district boundaries, computes per-district zonal statistics, and visualises the results through maps and charts.

---

## Overview

This notebook demonstrates a complete raster–vector integration workflow using Python's geospatial stack. Starting from a clipped raster file and a district boundary shapefile, it reprojects both datasets to a common CRS, renders overlay maps, extracts zonal statistics for each district, and produces several visualisations.

---

## Requirements

| Package | Purpose |
|---|---|
| `pandas` | Tabular data handling |
| `geopandas` | Vector (shapefile) I/O and spatial operations |
| `numpy` | Numerical operations |
| `matplotlib` | Plotting and visualisation |
| `rasterio` | Raster file I/O and resampling |
| `rasterstats` | Zonal statistics (raster → vector aggregation) |

Install all dependencies:

```bash
pip install pandas geopandas numpy matplotlib rasterio rasterstats
```

---

## Data Requirements

Place the following files on your machine and update the paths in the notebook accordingly:

| File | Description |
|---|---|
| `India_District_Boundary.shp` (+ sidecar files) | India district-level boundary shapefile |
| `india.clipped.tif` | Clipped raster file (DEM or LULC) covering India |

The notebook currently uses hardcoded Windows paths — update these to match your local directory structure before running.

---

## Workflow

### 1. Data Loading
- Reads the district boundary shapefile into a GeoDataFrame
- Opens the raster file with `rasterio`

### 2. CRS Alignment
- Checks the coordinate reference systems of both datasets
- Reprojects the vector layer to match the raster CRS using `gdf.to_crs()`

### 3. Raster Visualisation
- Downsamples the raster (1/20th resolution) using average resampling for fast preview
- Plots the raster with a terrain colormap
- Overlays district boundaries in red/black

### 4. Raster–Vector Overlay
- Aligns spatial extents using `plotting_extent()` so both layers render in the same coordinate space
- Adds a colorbar labelled with raster value units

### 5. Zonal Statistics
- Uses `rasterstats.zonal_stats()` to compute `mean`, `min`, and `max` raster values per district
- Appends results as new columns (`mean_value`, `min_value`, `max_value`) to the GeoDataFrame

### 6. Choropleth Mapping
- Plots a district-level choropleth map of mean raster values using `YlOrRd_r` and `viridis` colormaps

### 7. Statistical Visualisations
- Histogram of mean raster value distribution across districts
- Boxplot of mean values
- Scatter plot of district index vs. mean value (saved as `Scatter_plot_mean_value.png` at 300 DPI)

### 8. Output Export
- Saves the enriched GeoDataFrame back to a shapefile (`India_District_Boundary.shp`)
- Exports a CSV (without geometry) as `India_District_Boundary.csv`

---

## Outputs

| File | Description |
|---|---|
| `India_District_Boundary.shp` | Shapefile with zonal statistics appended |
| `India_District_Boundary.csv` | Flat CSV of district attributes and statistics |
| `Scatter_plot_mean_value.png` | High-resolution scatter plot (300 DPI) |

---

## Notes

- The raster is downsampled to 1/20th of its original resolution for visualisation; the full-resolution file is used for zonal statistics computation.
- `nodata` is set to `-999` during zonal stats — verify this matches the actual nodata value in your raster.
- The notebook ends with a batch-processing skeleton using `glob` to iterate over multiple raster files; extend this for multi-raster workflows.
