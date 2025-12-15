```markdown
# Haiti Mosquito Abundance Study

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![DOI](https://img.shields.io/badge/DOI-pending-blue.svg)](https://github.com/IanPsheaSmith/Haiti_MosqAbundanceStudy)

**Interactive Website:** [https://ianpsheasmith.github.io/Haiti_MosqAbundanceStudy/](https://ianpsheasmith.github.io/Haiti_MosqAbundanceStudy/)

## Table of Contents
- [Overview](#overview)
- [Species Studied](#species-studied)
- [Repository Structure](#repository-structure)
- [Data Files](#data-files)
- [Spatial Predictions](#spatial-predictions)
- [Figures and Visualizations](#figures-and-visualizations)
- [Interactive Maps](#interactive-maps)
- [Usage](#usage)
- [System Requirements](#system-requirements)
- [Citation](#citation)
- [License](#license)
- [Contact](#contact)

## Overview

This repository contains all data, code, predictions, and figures associated with a spatial modeling study of mosquito abundance in Haiti. The study investigates the ecological and environmental drivers of six medically important mosquito species using species-specific environmental buffers and spatiotemporal covariates.

**Key Features:**
- Species-specific mosquito count datasets with matched environmental covariates
- Complete R code for reproducible analysis
- High-resolution spatial predictions (baseline and monthly)
- Interactive web maps for data exploration
- Partial dependence plots showing covariate effects
- All manuscript figures and supplemental materials

## Species Studied

| Species | Abbreviation | Medical Importance |
|---------|--------------|-------------------|
| *Aedes aegypti* | Aeae | Primary dengue, Zika, chikungunya vector |
| *Aedes albopictus* | Aealb | Secondary arbovirus vector |
| *Aedes mediovittatus* | Aem | Potential arbovirus vector |
| *Culex quinquefasciatus* | Quinx | West Nile virus vector |
| *Culex nigripalpus* | Cxn | Eastern equine encephalitis vector |
| *Psorophora columbiae* | Psc | Potential arbovirus vector |

## Repository Structure

```
Haiti_MosqAbundanceStudy/
├── Data_and_Code/          # Raw data and analysis code
├── Figures/                # Manuscript figures
├── Predictions/            # Model predictions and visualizations
│   ├── Baseline/          # Annual average predictions
│   ├── Monthly/           # Month-specific predictions
│   ├── Interactive_Maps/  # HTML interactive maps
│   ├── PDPlots/          # Partial dependence plots
│   ├── StudySite/        # Study area visualizations
│   └── Summary_Statistics/ # Spatial statistics
├── index.html             # Repository website
└── README.md             # This file
```

## Data Files

### Mosquito Count Datasets
**Location:** `Data_and_Code/`

Six CSV files containing species-specific mosquito capture data:
- `HCM_Full_Aeae.csv` - *Aedes aegypti*
- `HCM_Full_Aealb.csv` - *Aedes albopictus*
- `HCM_Full_Aem.csv` - *Aedes mediovittatus*
- `HCM_Full_Cxn.csv` - *Culex nigripalpus*
- `HCM_Full_Cxq.csv` - *Culex quinquefasciatus*
- `HCM_Full_Psc.csv` - *Psorophora columbiae*

**Data Structure:**
Each dataset includes:
- `Date`: Collection date (YYYY-MM-DD)
- `Latitude`/`Longitude`: Trap coordinates (WGS84)
- `Count`: Number of mosquitoes captured
- Environmental covariates extracted at species-specific buffer radii:
  - Temperature (°C)
  - Precipitation (mm)
  - NDVI (Normalized Difference Vegetation Index)
  - Population density (persons/km²)
  - Elevation (m)
  - Built area (%)
  - Cropland cover (%)
  - Shrub cover (%)
  - Wind speed (m/s)

### Environmental Raster Stacks
**Location:** `Data_and_Code/Rasters/`

Contains 13 multi-band GeoTIFF files:
- `AverageStack.tif` - Annual average environmental covariates
- `January_Stack.tif` through `December_Stack.tif` - Monthly environmental data

**Raster Specifications:**
- Coordinate system: WGS84 / UTM Zone 18N
- Resolution: 250m × 250m
- Extent: Haiti national boundaries
- Bands: All environmental covariates listed above

### Geographic Data
**Location:** `Data_and_Code/`

- `Haiti_Shapefiles.zip` - Administrative boundaries and study area shapefiles

### Analysis Code
**Location:** `Data_and_Code/`

- `Haiti_MosqAbundance.Rmd` - Complete R Markdown document containing:
  - Data preprocessing
  - Model fitting and validation
  - Prediction generation
  - Figure creation
  - All analyses presented in the manuscript

## Spatial Predictions

### Baseline Predictions
**Location:** `Predictions/Baseline/{Species}/`

Annual average predictions for each species (11 files per species):

**Abundance Models:**
- `*_Abundance_Mean.tif` - Mean predicted abundance
- `*_Abundance_SD.tif` - Standard deviation
- `*_Abundance_Lower95.tif` - Lower 95% confidence interval
- `*_Abundance_Upper95.tif` - Upper 95% confidence interval

**Presence Models:**
- `*_Presence_Mean.tif` - Mean presence probability
- `*_Presence_SD.tif` - Standard deviation
- `*_Presence_Lower95.tif` - Lower 95% confidence interval
- `*_Presence_Upper95.tif` - Upper 95% confidence interval
- `*_Presence_Agreement.tif` - Model agreement metric

**Combined:**
- `*_Combined_Mean.tif` - Combined abundance-presence prediction
- `*_Combined_SD.tif` - Combined standard deviation

### Monthly Predictions
**Location:** `Predictions/Monthly/{Species}/`

Month-specific predictions for each species (36 files per species):
- `*_{Month}_Abundance.tif` - Monthly abundance predictions
- `*_{Month}_Presence.tif` - Monthly presence probabilities
- `*_{Month}_Presence_SD.tif` - Monthly presence uncertainty

### Vector Graphics
**Location:** `Predictions/Baseline/SVGs/`

Publication-quality vector graphics (24 files total):
- Mean abundance maps (PNG and SVG for each species)
- Mean presence maps (PNG and SVG for each species)

## Figures and Visualizations

### Manuscript Figures
**Location:** `Figures/`

- `Figure1.tif` - Study design and sampling locations
- `Figure2.tif` - Species distribution and abundance patterns
- `Figure3.tif` - Environmental drivers and model performance

### Supplemental Materials
**Location:** `Figures/`

- `S1.pdf` - Additional spatial predictions
- `S2.pdf` - Model diagnostics
- `S3.csv` - Summary statistics table
- `S4.pdf` - Temporal patterns

### Partial Dependence Plots
**Location:** `Predictions/PDPlots/{Species}/`

Species-specific partial dependence plots showing the relationship between environmental covariates and predictions:

**For each species:**
- `Abundance/` folder: Individual covariate effects on abundance
  - Built area, Cropland, Elevation, Precipitation, Shrub cover, Temperature, Wind speed
  - Each includes `.png` visualization and `_data.csv` with underlying data
- `Presence/` folder: Individual covariate effects on presence
  - Same covariates as abundance
- `*_Abundance_Combined.png` - All abundance effects in one figure
- `*_Presence_Combined.png` - All presence effects in one figure

### Study Site Visualizations
**Location:** `Predictions/StudySite/`

- `Abundance.png` - Abundance patterns across Haiti
- `Presence.png` - Presence patterns across Haiti
- `Uncertainty.png` - Prediction uncertainty patterns
- Vector versions (`.svg`) for publication

### Summary Statistics
**Location:** `Predictions/Summary_Statistics/`

- `Monthly_Extremes_Summary.csv` - Monthly prediction ranges
- `Spatial_Statistics_Abundance.csv` - Spatial statistics for abundance
- `Spatial_Statistics_Presence.csv` - Spatial statistics for presence
- `Spatial_Statistics_Long.csv` - Long-format spatial statistics

## Interactive Maps

**Web Access:** [https://ianpsheasmith.github.io/H_Count/](https://ianpsheasmith.github.io/H_Count/)

**Local Files:** `Predictions/Interactive_Maps/`

Interactive Leaflet maps for each species:
- [*Aedes aegypti* Map](https://ianpsheasmith.github.io/H_Count/AeaeMap.html)
- [*Aedes albopictus* Map](https://ianpsheasmith.github.io/H_Count/AealbMap.html)
- [*Aedes mediovittatus* Map](https://ianpsheasmith.github.io/H_Count/AemMap.html)
- [*Culex quinquefasciatus* Map](https://ianpsheasmith.github.io/H_Count/QuinxMap.html)
- [*Culex nigripalpus* Map](https://ianpsheasmith.github.io/H_Count/CxnMap.html)
- [*Psorophora columbiae* Map](https://ianpsheasmith.github.io/H_Count/PscMap.html)

**Features:**
- Toggle between abundance and presence predictions
- View monthly temporal variation
- Interactive tooltips with prediction values
- Layer controls for different prediction types
- Downloadable for offline use

## Usage

### Cloning the Repository

```bash
git clone https://github.com/IanPsheaSmith/Haiti_MosqAbundanceStudy.git
cd Haiti_MosqAbundanceStudy
```

## Citation

If you use this data or code in your research, please cite:

```
[Author names]. (Year). [Manuscript title]. [Journal name]. DOI: [pending]
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

**Data Usage:** All data are freely available for use with proper attribution. We encourage researchers to use these data for:
- Model validation and comparison
- Meta-analyses
- Vector control planning
- Educational purposes

## Contact

Ian Pshea-Smith  
Email: [ismithgh@umich.edu](mailto:ismithgh@umich.edu)

**Issues and Questions:**  
Please use the [GitHub Issues](https://github.com/IanPsheaSmith/Haiti_MosqAbundanceStudy/issues) page for:
- Data questions
- Code issues
- Feature requests
- General inquiries

## Acknowledgments

### Funding
- This work was funded by the Armed Forces Health Surveillance Branch (AFHSB), Global Emerging Infections Surveillance (GEIS) Section, under ProMIS ID (P0154_24_EC and P0118-24-RD). The funders had no role in study design, data collection and analysis, decision to publish, or preparation of the manuscript.

### Disclaimer
 - The use of either trade or manufacturers’ names in this report does not constitute an official endorsement of any commercial products. This report may not be cited for purposes of advertisement. The opinions, interpretations, conclusions, recommendations and views in this publication are those of the authors and do not necessarily reflect the official policy or position of the Uniformed Services University of the Health Sciences, Department of the Army, Department of the Navy, Department of Defense, nor the U. S. Government. Multiple authors are military service members of the U.S. Government. This work was prepared as part of their official duties. Title 17, U.S.C., §105 provides that copyright protection under this title is not available for any work of the U.S. Government. Title 17, U.S.C., §101 defines a U.S. Government work as a work prepared by a military Service member or employee of the U.S. Government as part of that person’s official duties.


---

**Last Updated:** December 2025  
**Repository Status:** Active Development  
**Manuscript Status:** In Preparation
```