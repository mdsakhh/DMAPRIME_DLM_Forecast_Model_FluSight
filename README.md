# DLM Recursive Forecast Model with EHR Covariates

## Model

**Dynamic Linear Model (DLM)** using statsmodels' `UnobservedComponents` with recursive multi-horizon forecasting for influenza hospitalizations.

- **Forecasting Strategy**: Recursive 1-step ahead prediction extended to horizons h=0,1,2,3 (1-4 weeks ahead)

## Data

| Source | Description |
|--------|-------------|
| **CDC FluSight Hub** | Weekly incident influenza hospitalizations (target variable) |
| **Prisma Health EHR** | Weekly positive tests, inpatient hospitalizations (SC) |
| **MUSC EHR** | Weekly positive tests, inpatient hospitalizations (SC) |

**Locations**: South Carolina (FIPS: 45), United States (US)

**Note**: SC EHR data is applied to both SC and US models.

## Features

| Feature Type | Description |
|--------------|-------------|
| **Y Lags** | Lagged hospitalization values (e.g., lag 1-10 weeks) |
| **EHR Positive Test Lags** | Lagged weekly positive tests from Prisma + MUSC (e.g., lag 5-10 weeks) |
| **EHR Inpatient Lags** | Lagged weekly inpatient hospitalizations from Prisma + MUSC (e.g., lag 5-10 weeks) |
| **Thanksgiving Flag** | Binary indicator (±3 days of 4th Thursday in November) |
| **Christmas Flag** | Binary indicator (December 20+) |
| **New Year Flag** | Binary indicator (January 1-7) |

**Transformation**: Log1p applied to target and EHR covariates for variance stabilization.

---
