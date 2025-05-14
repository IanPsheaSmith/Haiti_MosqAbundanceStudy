
# Haiti_MosqAbundanceStudy

This repository contains data and code associated with a spatial modeling study of mosquito abundance in Haiti. The study aims to understand the ecological and environmental drivers of six mosquito species based on species-specific environmental buffers and spatiotemporal covariates.

## Repository Contents

- **Datasets (6 CSV files)**  
  Each `.csv` file corresponds to one mosquito species captured in the field study. The datasets include:
  - Daily mosquito count data
  - Latitude and longitude coordinates of trap locations
  - Matched environmental covariate data extracted using species-specific buffer radii  
  The covariates include ecological factors aligned with the spatiotemporal resolution of trapping events.

- **Modeling and Figure Code (.Rmd file)**  
  The `.Rmd` file contains all code used to:
  - Fit statistical models of mosquito abundance
  - Perform model diagnostics and selection
  - Generate the final maps and figures presented in the associated manuscript

## Data Description

Each species-specific dataset includes:
- `Date`: Date of mosquito collection  
- `Latitude` / `Longitude`: Coordinates of the trap site  
- `Count`: Number of mosquitoes captured (species-specific)  
- Environmental covariates such as temperature, precipitation, NDVI, population density, elevation, etc., which have been extracted using buffer zones tailored to each species' known dispersal range

## Species Covered
The following six species are included in this study:
1. *Aedes aegypti*
2. *Aedes albopictus*
3. *Culex quinquefasciatus*
4. *Culex nigripalpus*
5. *Aedes mediovittatus*
6. *Psorophora columbiae*

## Usage Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/[YourUsername]/Haiti_MosqAbundanceStudy.git
   ```
2. Open the `.Rmd` file in RStudio.
3. Install any required R packages (listed at the top of the `.Rmd` file).
4. Knit the document to reproduce model outputs and figures.

## Citation
If you use this code or data in your research, please cite the associated manuscript:
> [Manuscript Citation Placeholder – update with DOI or full citation when available]

## License
This project is licensed under the [MIT License](LICENSE) — feel free to use, modify, and distribute with attribution.

## Contact
For questions or collaborations, please contact:  
**Ian Pshea-Smith**  
University of Florida  
Email: [your-email@domain.edu]
