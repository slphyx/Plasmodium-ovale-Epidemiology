# Plasmodium ovale Epidemiology

R code and curated epidemiological data accompanying the manuscript:

> **Global epidemiology of the *Plasmodium ovale* complex: a systematic analysis of published prevalence data**

This repository contains the final dataset and R scripts used to investigate the global epidemiology of the *Plasmodium ovale* complex, including *P. ovale curtisi* and *P. ovale wallikeri*.

## Overview

*Plasmodium ovale* is a relatively understudied cause of human malaria. The recognition of two genetically distinct taxa, *P. ovale curtisi* and *P. ovale wallikeri*, and differences in diagnostic approaches complicate comparisons of prevalence across geographical settings.

This study synthesises published epidemiological data to:

- Describe the geographical distribution of reported *P. ovale* infections.
- Compare reported prevalence between microscopy and molecular diagnostic methods.
- Examine geographical and temporal variation in reported prevalence.
- Quantify between-publication heterogeneity using Bayesian hierarchical models.
- Describe the distribution of *P. ovale curtisi* and *P. ovale wallikeri* among molecularly typed infections.

## Repository structure

```text
Plasmodium-ovale-Epidemiology/
├── Data/
│   └── Po_ovale_final_prevalence_analysis_187obs.csv
├── R/
│   ├── 01_descriptive_analysis.R
│   ├── 02_hierarchical_models.R
│   ├── Figure_2_P_ovale_geographical_evidence.R
│   ├── Figure_3_P_ovale_diagnostic_model_estimates.R
│   └── Figure_4_P_ovale_curtisi_wallikeri.R
├── README.md
└── LICENSE
```

## Data

The final prevalence dataset contains:

| Description | Total |
|---|---:|
| Publications | 156 |
| Epidemiological observations | 187 |
| Individuals examined | 688,680 |
| Reported *P. ovale* infections | 7,843 |

Each row represents an epidemiologically distinct observation. Multiple observations from the same publication were retained where they represented different populations, locations, study periods or diagnostic approaches.

For the primary prevalence analysis, infections reported as *P. ovale*, *P. ovale curtisi* or *P. ovale wallikeri* were considered collectively as the *P. ovale* complex.

The dataset includes study location, diagnostic method, infection counts, denominators and other relevant epidemiological information.

**Important:** The dataset represents observations extracted from published studies and should not be interpreted as a geographically representative estimate of global *P. ovale* prevalence.

## Statistical analysis

Bayesian hierarchical binomial regression models were fitted using the R package `brms`, which interfaces with Stan.

Four models were considered:

1. Intercept-only model with a publication-level random effect.
2. Diagnostic-method model with a publication-level random effect.
3. Diagnostic-method and continent model with a publication-level random effect.
4. Diagnostic-method, continent and study-year model with a publication-level random effect.

The primary hierarchical analyses were restricted to locally acquired infections. A beta-binomial model was additionally fitted as a sensitivity analysis to account for extra-binomial variation.

Model comparison was performed using leave-one-out cross-validation.

## Software

The analyses were conducted in R, using packages including:

- `brms` and `loo` for Bayesian modelling and model comparison.
- `dplyr`, `tidyr` and `readr` for data processing.
- `ggplot2`, `sf` and `rnaturalearth` for visualisation.

Additional package requirements are specified in the relevant R scripts.

## Reproducibility

Download or clone this repository, install the required R packages, and run the analysis scripts in their numbered order.

Some scripts may require adjustment of input and output paths according to the local working directory.

## Contact

For questions about the analysis, please contact:  
Email: sompob@tropmedres.ac
