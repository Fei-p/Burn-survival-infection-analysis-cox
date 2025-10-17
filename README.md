# Survival and Infection Control in Burn Patients: A Cox Model Analysis

## Overview
This project examines predictors of **time to infection** in burn patients, comparing two treatment strategies: routine bathing vs. total body cleansing with antimicrobial agents. Using data from 154 patients (Ichida et al., 1993), we evaluate how treatment type, demographics, burn severity, and time-dependent interventions (e.g., surgical excision, prophylactic antibiotics) relate to infection risk.

A stratified Cox proportional hazards framework is used to estimate hazard ratios, assess proportional-hazards assumptions, and interpret clinically actionable effects.

## Key findings (brief)
- **Timely surgical excision** is associated with a **lower hazard of infection**.
- **Antimicrobial cleansing** shows **marginal benefits** relative to routine bathing.
- **Race** appears associated with infection hazard (White patients higher in this sample), but this may reflect **sample imbalance** and warrants caution.
- **Burn site** and **percent burned** are not independently significant in simple models; potential **interactions/complex effects** are discussed.

> Results should be interpreted in context of sample size, covariate balance, and the observational design.

## Methods used
- **Kaplan–Meier estimation** for descriptive survival curves by groups
- **Log-rank tests** for unadjusted curve comparisons
- **Cox proportional hazards models** (univariable and multivariable)
- **Stratified Cox models** to account for non-PH or baseline hazard differences
- **Time-dependent covariates** (e.g., surgical excision, antibiotics) where applicable
- **PH diagnostics** using Schoenfeld residuals and `cox.zph`
- **Model fit/selection** via likelihood tests and AIC
- **Sensitivity checks** (functional form, influence diagnostics as needed)

## Repository contents
- **`Analysis_report.html`** — Rendered report with methods, figures, tables, and results.
- **`Burn_survival_proj.Rmd`** — R Markdown source code used to produce the analysis and report.

> To view results quickly, open `Analysis_report.html` in a browser.  
> To inspect or rerun the analysis, open `Burn_survival_proj.Rmd` in R or RStudio.

## Dataset
The analysis uses the **`burn`** dataset from the **KMsurv** package (Klein & Moeschberger survival datasets). It contains time-to-event outcomes with event indicators and clinical covariates relevant to burn severity and infection control.

- **Source:** `KMsurv::burn`  
- **Outcome:** time to infection (with event indicator) as used in this project’s modeling  
- **Covariates:** demographic factors, burn-severity measures, and infection-related variables as documented in the package reference

Load and inspect in R:
```r
install.packages("KMsurv")
library(KMsurv)
data("burn")
str(burn)
# See ?KMsurv::burn for exact variable definitions and coding
``` 
---

## Libraries used

Core analysis and reporting packages (install as needed):

```r
install.packages(c(
  "survival",     # Surv(), coxph(), diagnostics
  "survminer",    # KM plots, model visualization
  "KMsurv",       # burn dataset
  "tidyverse",    # dplyr, ggplot2, readr, tidyr
  "broom",        # tidy model outputs
  "gt"            # nicer tables (optional)
))
