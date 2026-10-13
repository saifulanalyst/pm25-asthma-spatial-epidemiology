# Spatial Epidemiology of PM₂.₅ and Asthma Emergency Department Visits Across U.S. Counties

**A reproducible spatial epidemiology project using R, GIS, spatial autocorrelation diagnostics, and spatial regression modeling.**

## Project Overview

Air pollution is a major environmental public health concern, particularly for individuals with respiratory conditions such as asthma. However, environmental exposures and health outcomes are not randomly distributed across geographic areas. Neighboring communities often share similar pollution levels, socioeconomic characteristics, and healthcare environments.

This project investigates the relationship between ambient fine particulate matter (PM₂.₅) and adult asthma emergency department (ED) visit rates across U.S. counties using 2020 environmental and public health surveillance data.

The study emphasizes an important methodological question:

**How does accounting for spatial dependence change our understanding of the relationship between air pollution and asthma-related emergency department visits?**

By integrating geographic information systems (GIS), exploratory spatial analysis, and spatial regression modeling, the project demonstrates the importance of considering geographic relationships when analyzing environmental health data.

## Research Objectives

1. Examine the geographic distribution of PM₂.₅ concentrations and adult asthma ED visit rates.
2. Quantify spatial autocorrelation using Global Moran's I.
3. Identify geographic clusters and spatial outliers using Local Indicators of Spatial Association (LISA).
4. Evaluate the association between PM₂.₅ exposure and asthma ED visit rates using conventional and spatial regression models.
5. Assess whether spatial modeling improves model fit and addresses residual geographic dependence.

## Data Sources

The project integrates publicly available environmental, health, demographic, and geographic datasets.

| Data | Source | Description |
|---|---|---|
| PM₂.₅ concentrations | [U.S. EPA Air Quality System](https://www.epa.gov/aqs) | Annual county-level ambient PM₂.₅ concentrations |
| Asthma ED visit rates | [CDC Environmental Public Health Tracking Network](https://ephtracking.cdc.gov/) | Adult asthma emergency department visit rates |
| Socioeconomic indicators | [U.S. Census Bureau ACS](https://data.census.gov/) | Poverty, income, insurance coverage, demographic composition |
| Geographic boundaries | [U.S. Census TIGER/Line](https://www.census.gov/geographies/mapping-files/time-series/geo/tiger-line-file.html) | County-level geographic boundary files |

**Study year:** 2020

**Geographic coverage:** Contiguous United States, subject to available outcome data.

**Regression sample:** 3,166 county observations reported in the manuscript.

**Study design:** Cross-sectional ecological analysis.

## Analytical Workflow

### 1. Data Preparation and Integration

- Import environmental, health, and socioeconomic datasets.
- Standardize county identifiers using five-digit FIPS codes.
- Merge datasets at the county level.
- Examine missing values and reporting coverage.
- Integrate geographic boundary files.
- Transform geographic data into the NAD83 / Conus Albers projection (EPSG:5070).

### 2. Exploratory Spatial Data Analysis

Generate county-level choropleth maps to examine the geographic distributions of:

- Annual mean PM₂.₅ concentrations.
- Adult asthma emergency department visit rates.
- Spatial variation in model residuals.

### 3. Spatial Autocorrelation

Apply Global Moran's I to evaluate whether PM₂.₅ concentrations and asthma ED visit rates exhibit geographic clustering.

Use Local Indicators of Spatial Association (LISA) to identify:

- High–High clusters
- Low–Low clusters
- High–Low spatial outliers
- Low–High spatial outliers

Bivariate LISA analysis is used to explore geographic patterns involving PM₂.₅ concentrations and asthma ED visit rates.

### 4. Regression Modeling

Four regression models are considered:

| Model | Purpose |
|---|---|
| Unadjusted OLS | Estimate the crude PM₂.₅–asthma association |
| Adjusted OLS | Account for socioeconomic characteristics |
| Spatial Lag Model | Incorporate spatial dependence in neighboring outcomes |
| Spatial Error Model | Account for spatial dependence in model errors |

Model assessment includes Rao's Score diagnostics, Akaike Information Criterion (AIC), and residual spatial autocorrelation testing.

### 5. Sensitivity Analysis

The manuscript describes sensitivity analyses involving alternative spatial neighborhood definitions and exclusion of selected wildfire-affected western states. These analyses should be fully documented and verified before being presented as completed reproducibility results.

## Key Findings

### Geographic clustering

Both PM₂.₅ concentrations and asthma ED visit rates exhibited strong spatial autocorrelation.

| Measure | Global Moran's I |
|---|---:|
| PM₂.₅ concentration | 0.751 |
| Adult asthma ED visit rates | 0.644 |
| Adjusted OLS residuals | 0.462 |

All three statistics were reported as statistically significant.

### Conventional regression versus spatial regression

The adjusted OLS model estimated a PM₂.₅ coefficient of **0.599**, compared with **0.114** in the spatial lag model.

After accounting for spatial dependence and socioeconomic characteristics, PM₂.₅ remained positively associated with adult asthma ED visit rates (95% CI: 0.026–0.201; p = 0.011).

The spatial lag model also substantially improved model fit and reduced residual spatial autocorrelation.

These results demonstrate that accounting for spatial structure can materially change estimates obtained from county-level environmental health analyses.

### Geographic heterogeneity

Exploratory spatial analyses identified regional variation in PM₂.₅ concentrations and asthma ED visit rates, including elevated asthma burdens in portions of the Gulf Coast, Florida, and Mid-Atlantic.

The study also observed geographic differences between pollution concentrations and asthma ED visit rates in parts of the western United States.

These patterns warrant further investigation using source-specific pollution measurements, more complete health surveillance coverage, and additional contextual variables.

## Tools and Technologies

**Programming language:** R 4.4.2

**Core packages:**

- `sf` — Spatial data processing and geographic operations
- `spdep` — Spatial neighborhood structures and autocorrelation
- `spatialreg` — Spatial lag and spatial error regression
- `tidyverse` — Data manipulation and preparation
- `ggplot2` — Data visualization
- `tidycensus` — Census data retrieval
- `ggspatial` — Geographic visualization
- `patchwork` — Figure composition

**Statistical methods:** OLS regression, Moran's I, LISA, spatial autoregressive models, Rao's Score tests, and AIC-based model comparison.

## Reproducibility

The analysis was developed in R Markdown to integrate data processing, statistical analysis, visualizations, and reporting within a reproducible analytical workflow.

To reproduce the study, researchers should obtain the source datasets for the specified study year, standardize county identifiers, apply the documented geographic and data-processing procedures, and execute the analysis using compatible R packages.

The complete execution instructions and file paths should be finalized after the analysis scripts and required input files are added to this repository.

## Limitations

This study uses an ecological, cross-sectional design. Consequently, county-level associations should not be interpreted as individual-level causal effects.

Additional limitations include incomplete state-level asthma ED reporting, potential exposure misclassification from annual monitoring data, and the absence of several potentially relevant confounders.

## Research Applications

The project illustrates how spatial data science can contribute to:

- Environmental health surveillance and epidemiology
- Geographic identification of public health priorities
- Statistical model validation and diagnostics
- Integration of environmental and population health datasets
- Reproducible public health research

## Authors

**Md Saiful Hasan**  
MS in Public Health Data Science  
Department of Epidemiology and Biostatistics  
College of Public Health, Temple University  
Philadelphia, Pennsylvania, USA

**Dr. Md Jahirul Alam Azad**  
Adjunct Faculty, East West University  
Dhaka, Bangladesh

## Data Availability

The underlying data sources are publicly accessible through the EPA, CDC, and U.S. Census Bureau websites linked above.

Availability of processed data and complete analysis code through this repository will depend on the files included and applicable data redistribution requirements.

## Citation

If you use this repository or build upon its analytical workflow, please acknowledge the authors and cite the associated manuscript when its publication details become available.

**Manuscript:** *Mapping the Invisible: Spatial Dependence in the PM₂.₅ and Asthma Relationship Across U.S. Counties.*

**Publication status:** Manuscript under journal consideration; publication details to be added when available.

## License

A repository license will be specified after the authors select the appropriate terms for sharing the code and other original materials.
