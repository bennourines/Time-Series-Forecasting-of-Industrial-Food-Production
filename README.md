# Time Series Forecasting of Industrial Food Production

Forecasting monthly industrial food production using R, ARIMA/SARIMA models, and structural break detection.

![Project Banner](banner.png)

Monthly industrial food production is analyzed and forecasted using advanced time-series techniques in R. This repository (currently centered on the notebook `Times_Series_Assesment.ipynb`) provides a reproducible workflow: data preparation, exploratory analysis, decomposition, structural break detection, ARIMA-based modeling, and forward forecasting.

---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Data Description](#2-data-description)
3. [Methodology](#3-methodology)
4. [Modeling & Forecasting Pipeline](#4-modeling--forecasting-pipeline)
5. [Setup & Reproducibility](#5-setup--reproducibility)
6. [Extending the Project](#6-extending-the-project)
7. [References](#7-references)

---

## 1. Project Overview
Industrial food production often exhibits trend, seasonal, and cyclical components influenced by demand cycles, supply chain constraints, and macroeconomic factors. Accurate forecasting supports capacity planning, inventory management, and strategic decision-making.

---

## 2. Data Description
- **Frequency:** Monthly  
- **Target:** Industrial food production index or volume  
- **Assumptions:** Data is continuous, mostly complete; missing values handled during cleaning.

---

## 3. Methodology
Core analytical stages performed:

- **Import & Clean:** Handle missing values, convert date formats, filter anomalies.  
- **Exploratory Data Analysis (EDA):** Time plots, seasonal subseries, distribution summaries.  
- **Transformation:** Optional log or differencing for variance stabilization and stationarity.  
- **Decomposition:** Additive & multiplicative (classical + STL if added later).  
- **Structural Break Detection:** `strucchange` (breakpoints in level or trend).  
- **Stationarity Tests:** Augmented Dickey-Fuller (ADF), KPSS for confirmation.  
- **Autocorrelation Analysis:** ACF/PACF to guide ARIMA orders.  
- **Model Building:** `auto.arima()` and manually tuned Seasonal ARIMA.  
- **Residual Diagnostics:** Normality, independence, homoskedasticity checks, Ljung-Box test.  
- **Forecast Generation:** Point forecasts + confidence intervals.  
- **Model Comparison:** Information criteria (AICc), RMSE/MAE on holdout, residual patterns.

---

## 4. Modeling & Forecasting Pipeline
1. Convert series to `ts()` object (start year, frequency = 12).  
2. Visual inspection: Trend, seasonal strength, potential regime shifts.  
3. Test stationarity; apply differencing (seasonal + non-seasonal) as required.  
4. Fit baseline `auto.arima()`.  
5. Evaluate residuals; if inadequate, iterate with manual SARIMA specification.  
6. Validate with training/validation split or time-series cross-validation (rolling origin).  
7. Produce multi-period forecasts (e.g., next 12–24 months) and visualize.  
8. Summarize performance metrics and select champion model.

---

## 5. Setup & Reproducibility
You can work in either R directly or via the Jupyter notebook interface (with an R kernel).  

**Required R packages:**
- `forecast`  
- `tseries`  
- `psych`  
- `strucchange`  
- (Optional) `ggplot2`, `dplyr`, `readr`, `lubridate`, `TSstudio`, `xts`, `zoo`  

**Install in R:**
```r
install.packages(c("forecast","tseries","psych","strucchange","ggplot2","dplyr","readr","lubridate"))


## 6. Extending the Project
Enhancement ideas:
- Incorporate exogenous regressors (XREG) — macroeconomic indicators, commodity prices.
- Try advanced models: TBATS, ETS, Prophet, or neural approaches (RNN/LSTM via `keras`).
- Add rolling-origin cross-validation for more robust performance evaluation.
- Implement automated report generation (R Markdown → HTML/PDF).
- Deploy forecasts via an API or dashboard (e.g., Shiny app).

## 7. References
- Hyndman, R.J. & Athanasopoulos, G. (Forecasting: Principles and Practice).
- `forecast` R package documentation.
- `strucchange` package vignette.
- Time Series Analysis texts (Box-Jenkins methodology).

