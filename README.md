# Nighttime Land Surface Temperature Forecasting to 2040 Using Exponential Smoothing (ETS)

This repository contains an R script developed to model historical thermal trajectories and project summer nighttime Land Surface Temperature (LST) up to the year 2040 for the Phase I (Pre-2000) urbanized area of Dhaka. 

The pipeline implements an Error-Trend-Seasonal (ETS) state-space exponential smoothing framework to generate predictive trajectories alongside formal 95% confidence intervals and standard error bounds.

---

## What the Script Does

1. **Loads historical time series data:** Ingests annual mean nighttime LST records from Excel (`Pre 2000 Night time LST.xlsx`) and structures them into a univariate annual time series object (`ts`).
2. **Fits the ETS model & projects forward:**
   * Automatically identifies the optimal Error-Trend-Seasonal components via `forecast::ets()`.
   * Projects annual mean LST values 15 steps ahead ($h = 15$) spanning 2026 to 2040 at a 95% prediction interval.
3. **Quantifies forecast uncertainty:** Extracts point forecasts along with upper and lower 95% confidence boundaries, calculating corresponding standard errors for each predicted year.
4. **Builds a publication-quality forecast graphic:** Uses `forecast::autoplot()` and `ggplot2` to plot historical observations alongside the projected 15-year forecast envelope with shaded uncertainty bands (exported at 300 DPI as `ETS_Forecast_Plot.png`).
5. **Exports structured tabular projections:** Writes the forecasted annual values, standard errors, and 95% confidence limits into a clean spreadsheet (`Pre2000_LST_ETS_Forecast_2040.xlsx`).

---

## Required Packages

Ensure the following packages are installed in your R environment:

```r
install.packages(c("readxl", "forecast", "writexl", "ggplot2"))
