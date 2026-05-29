# BleoTox Radiomics

Radiomics machine learning pipeline in R for predicting chemotherapy-associated pulmonary toxicity using PET imaging features.

## Overview

This repository contains the analysis pipeline accompanying the publication:

[ADD PAPER TITLE HERE]

The project investigates whether PET radiomic features can:

* identify active pulmonary toxicity during chemotherapy
* predict future toxicity development from baseline scans

The workflow includes:

* feature filtering using Spearman correlation
* multicollinearity reduction
* random forest classification
* leave-one-out cross-validation (LOOCV)
* feature importance analysis
* statistical comparison between baseline and interim scans

## Technologies

* R
* tidyverse
* caret
* randomForest
* ggplot2
* pROC

## Running the analysis

Install required packages:

```r
install.packages(c(
  "tidyverse",
  "caret",
  "readxl",
  "randomForest",
  "pROC",
  "ggplot2"
))
```

Run the analysis:

```r
rmarkdown::render("bleotox_radiomics.Rmd")
```

## Data availability

The datasets used in this study contain sensitive clinical patient information and cannot be publicly shared due to hospital privacy regulations and ethical restrictions.

The repository therefore provides:

* the complete analysis pipeline
* preprocessing workflow
* feature selection methodology
* machine learning implementation
* statistical analysis workflow

## Publication

[Add DOI or publication link here]
