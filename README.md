# Evaluating Integrated Soybean Cyst Nematode Management Using Spatially Informed Mixed Models 

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Reproducible](https://img.shields.io/badge/reproducible-yes-brightgreen.svg)](#reproducibility)
[![Maintained by](https://img.shields.io/badge/maintained%20by-LopezNicoraLab-red.svg)](https://github.com/LopezNicoraLab)
 
---
 
## Associated Publication
 
Garnica, V. C. and Lopez-Nicora, H. D.  
Field evaluation of integrated soybean cyst nematode management using spatially informed mixed models.  
**Phytopathology** (*Under review*)
 
---

## Repository Purpose
 
This repository contains data and reproducible analysis scripts supporting the associated manuscript. The study evaluates integrated management strategies for soybean cyst nematode (SCN) across field trials conducted in 2022 and 2023 in Ohio, using mixed models with spatial covariance structures to account for within-field heterogeneity. The analysis quantifies treatment effects on SCN reproduction factor (*Rf*) and soybean yield, estimates cultivar-specific damage coefficients relating initial SCN population density to yield loss, and compares spatial model structures to identify the best-fitting covariance specification for each trial.
 
All figures, tables, and statistical outputs are generated programmatically from the scripts provided.

## Repository Structure
 
```
├── 01_data
│   └── pioneers.csv                 → Trial dataset
├── 02_code
│   ├── spatial_modeling_yld.qmd     → Yield response analysis (2022, 2023, multi-year)
│   ├── spatial_modeling_yld.html    → Rendered HTML output
│   ├── spatial_modeling_rf.qmd      → SCN reproduction factor analysis
│   ├── spatial_modeling_rf.html     → Rendered HTML output
│   └── spatial_modeling_rf.html     → Custom functions for spatial modeling and contrasts
├── 03_outputs
│   ├── cult_int/                → Cultivar and cultivar × seed treatment interaction estimates
│   ├── damage/                  → Damage function coefficients (Pi–yield relationships)
│   ├── model_selection/         → Spatial model comparison metrics (AIC/BIC)
│   ├── seed_trt/                → Seed treatment effect estimates
│   ├── variances/               → Variance component estimates
│   └── fig_1–4.tiff, fig_S1     → Manuscript figures
```
 
---

 
## Analysis Pipeline
 
**Yield response** (`spatial_modeling_yld.qmd`): Fits mixed models with alternative spatial covariance structures to soybean yield data from 2022, 2023, and combined multi-year trials. Exports model comparison metrics, treatment effect estimates, variance components, and cultivar-specific damage coefficients.
 
**Reproduction factor** (`spatial_modeling_rf.qmd`): Analyzes SCN reproduction factor (*Rf* = log(*Pf*/*Pi*)) using the same spatial modeling framework as the yield analysis.
 
**Custom functions** (`functions.R`): Defines functions for model evaluation (`icREML` for AIC/BIC computation), contrast estimation with optional back-transformation (`st_contrasts`, `cult_contrasts_ss`, `cult_contrasts_ms`), and spatial basis matrix construction for tensor-product spline modeling (`spatial_matrix`).
 
---
 
## Reproducibility Instructions

To reproduce results:

1. Clone this repository.
2. Install required R packages, including `ASReml-R` (license required), `tidyverse`, and dependencies listed at the top of each `.qmd` file.
3. Render `spatial_modeling_yld.qmd` and `spatial_modeling_rf.qmd`. All outputs in `results/` will regenerate automatically.

**Note:** `ASReml-R` requires a valid license from VSN International. The `TPSbits` package (Welham 2022) is not available on CRAN; it was obtained directly from the package author (S. J. Welham, stats4biol@gmail.com). All other dependencies are available from CRAN.

---
 
## Data Availability
 
The trial dataset (`pioneers.csv`) contains plot-level observations from the 2022 and 2023 field trials, including initial and final SCN egg counts, soybean yield, cultivar and seed treatment assignments, and row/column indexes.
 
---
 
## Citation
 
Please cite the associated publication and this archived repository (see `CITATION.cff`).
 
---