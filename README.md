# BleoTox Radiomics Project

Radiomics machine learning pipeline in R for investigating chemotherapy-associated 
pulmonary toxicity using Radiomics PET imaging features.

## Project Overview

This repository contains the analysis workflow accompanying a published Radiomics PET 
study investigating pulmonary toxicity development during chemotherapy treatment.

The project explores whether PET-derived Radiomic features can:
* Identify active pulmonary toxicity during treatment (interim scans)
* Predict toxicity development in the future from baseline scans
* Examine toxicity-related imaging patterns compared to control patient groups

The workflow combines Radiomics feature selection, multicollinearity reduction, 
machine learning classification, and statistical analysis within a reproducible R-based pipeline.

---

## Methodology & Validation

The analysis pipeline includes:

### 1) Feature preprocessing

* Baseline and interim PET scan separation
* Spearman correlation filtering against the features Volume and SUVmean
* Removal of highly intercorrelated Radiomic features to reduce multicollinearity

### 2) Machine learning

* Algorithm: Random Forest classification
* Hyperparameter tuning across multiple tree sizes to optimize the model 
* Validation strategy: Leave-One-Out Cross Validation (LOOCV) due to the clinical nature ans
  small sample size of the dataset. This approach ensures that every sample is used for 
  validation, providing an unbiased estimate of model accuracy. 
* Model selection: The final model configuration was automatically selected based on 
  maximizing the cross-validated accuracy metric.
* Feature importance analysis was assessed using the mean decrease in Gini 

### 3) Statistical analysis

* Paired Wilcoxon testing (non-parametric method due to the small sample size)
* Baseline vs interim comparison
* Toxicity and non-toxicity subgroup analysis
* Additional external control group validation

---

## Explainability & Clinical Interpretation

To avoid black-box model and ensure clinical relevance (essential for public health research):
* Feature importance analysis was assessed using the mean decrease in Gini
* This metric allows us to rank and interpret which specific Radiomics features contribute
  most to predict bleomycineo-induced toxicity.

---

## Results & Impact
Results:  The RF classifier correctly identified bleomycine-induced toxicity in 72.2% of the
patients and predicted the development of bleomycine-induced toxicity correctly in 50% of the 
patients

Clinical relevance: Certain regional 18F-FDG PET radiomics features can effectively identify
bleomycine-induced toxicity and 18F-FDG PET radiomics, with and without machine learning, 
might serve as potential biomarkers for to detect bleomycine induced toxicity.

---

## Technologies

This project was developed in R using:

* tidyverse
* caret
* randomForest
* ggplot2
* pROC
* readxl
* rmarkdown

---

## Repository Structure

```text
bleotox-radiomics/
│
├── README.md
├── bleotox_radiomics.Rmd
├── bleotox_radiomics.html
├── .gitignore
│
├── data/
│   └── example_input_structure.csv
│
├── figures/
│   ├── mds_plot.png
│   └── statistical_analysis.png
│
└── paper/
    └── bleotox_publication.pdf
```


---

## Running the analysis

Install required packages:
```r
install.packages(c(
  "tidyverse",
  "caret",
  "readxl",
  "randomForest",
  "pROC",
  "ggplot2",
  "rmarkdown"
))
```

Run the analysis pipeline:
```r
rmarkdown::render("bleotox_radiomics.Rmd")
```

---

## Data Availability

The datasets used in this study contain sensitive clinical patient information and 
cannot be publicly shared due to hospital privacy regulations and ethical restrictions.

This repository therefore provides:
* The complete analysis pipeline
* Preprocessing workflow
* Feature selection methodology
* Machine learning implementation
* Statistical analysis workflow
* A small dummy dataset demonstrating the expected input structure

The included dummy dataset does not contain real patient information and is provided 
solely for illustrative and reproducibility purposes.

Researchers interested in reproducing the study may adapt the pipeline to their 
own institutional datasets.

---
 
## Publication

Associated publication: 
Smith CLC et al. Diagnostics (2024).
https://doi.org/10.3390/diagnostics14222531

---

## Author

C.L.C. Smith



