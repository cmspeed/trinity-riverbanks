# Floods drive bankline kinematics and fluvial preservation along the coastal Trinity River, Texas

This repository contains the data, analysis code, and plotting routines to reproduce the findings and figures for the manuscript: **"Floods drive bankline kinematics and fluvial preservation along the coastal Trinity River, Texas: Evidence from high-resolution PlanetScope images"** (currently in review at *JGR: Earth Surface*).

This project represents among the first quantitative application of high-cadence, 3m-resolution PlanetScope satellite imagery to extract and track river bankline evolution at the flood-event scale. River banklines are extracted using the automated [rivabar](https://github.com/zsylvester/rivabar) and analyzed using [meandergraph](https://github.com/zsylvester/meandergraph). This analysis resolves meter-scale erosion, deposition, and event-scale stratigraphic preservation across a 90-river-kilometer reach of the coastal Trinity River over a seven-year period.

## Repository Structure

* **`data/`**: Contains raw and processed spatial/hydrological datasets used in the analysis.
  * `banklines/`, `centerlines/`, `last_channel/`: Geospatial river geometries.
  * `polygon_graphs/`: Directed-graph outputs mapping channel kinematics.
  * `bar_graphs/`: Stratigraphic preservation outputs.
  * `discharge/`: Hydrological data from [USGS 08066500](https://waterdata.usgs.gov/monitoring-location/USGS-08066500/#dataTypeId=continuous-00065-0&period=P7D&showFieldMeasurements=true) .

* **`notebooks/`**: Contains `analysis.ipynb`, the summary Jupyter Notebook that includes all analysis and generates all non-map manuscript figures.
* **`figures/`**: Automatically generated directory where `analysis.ipynb` exports finalized, publication-ready manuscript plots.
* **`environment.yml`** & **`requirements.txt`**: Dependency files for reproducing the exact Python environment.

## Getting Started

To ensure full reproducibility and properly handle geospatial C-library dependencies (like PROJ and GDAL), using `conda` or `mamba` to build the environment is strongly recommended.

### 1. Clone the repository
```bash
git clone https://github.com/cmspeed/trinity-riverbanks.git
cd trinity-riverbanks
```

### 2. Create and activate the environment
```bash
# Using mamba (recommended for faster solving)
mamba env create -f environment.yml
conda activate trinity-river-env
```

(A requirements.txt is also provided for lightweight setups, but `environment.yml` is recommended to prevent spatial projection errors with `geopandas`.)

### 3. Run the analysis
Launch Jupyter, open `notebooks/analysis.ipynb`, and run the cells sequentially. The notebook will automatically locate the `data/` directory and save all generated plots to the `figures/` directory at the project root.
```bash
jupyter notebook notebooks/analysis.ipynb
```

### Citation
If you use `rivabar` your research, please cite the corresponding preprint:

```bash
@article{sylvesterdual,
  author  = {Sylvester, Z. and Speed, C. M.},
  title   = {A dual-graph approach to automated mapping and tracking of river banks in satellite imagery},
  journal = {Earth Surface Dynamics (In review)},
  year    = {2026},
  doi     = {10.22541/essoar.15005317/v1}
}
```