# Survival and Infection Control in Burn Patients: A Cox Model Analysis

This project analyzes survival in burn patients and explores infection-related risk using **Cox proportional hazards** modeling. It includes data cleaning, exploratory survival analysis (KM curves, log-rank tests), model building/diagnostics, and interpretation of hazard ratios.

---

## 📄 What’s in this repo

- **`Analysis_report.html`**  
  The rendered report with methods, figures, tables, and results.

- **`Burn_survival_proj.Rmd`**  
  The R Markdown source code used to produce the analysis/report (R language).

> To inspect the code directly, open `Burn_survival_proj.Rmd`. To view results quickly, open `Analysis_report.html` in a browser (or host via GitHub Pages).

---

## 📦 Dataset

We use the **`burn`** dataset from the **KMsurv** package (Klein & Moeschberger survival datasets).  
It contains **time-to-event** outcomes with **event indicators** and clinical covariates relevant to burn severity and infection control.

- **Source:** `KMsurv::burn`  
- **Outcome:** survival time (e.g., hospital time or follow-up) and event (death) indicator  
- **Covariates (examples):** demographic and burn-severity measures (e.g., extent of burn), and infection-related variables documented in the package reference.

> Load in R:
> ```r
> install.packages("KMsurv")
> library(KMsurv)
> data("burn")
> str(burn)
> ```

> **Note:** Please consult `?KMsurv::burn` for precise variable definitions.

---

## 🔧 Libraries used

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
