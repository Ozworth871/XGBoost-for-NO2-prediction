# XGBoost for NO2 Prediction

## Project Overview

This project leverages **XGBoost** (Extreme Gradient Boosting) and **kNN-based feature selection** to predict hourly nitrogen dioxide (NO2) concentrations in Manchester Piccadilly. The study integrates meteorological and traffic datasets and explores various feature selection methods to improve prediction accuracy.

### Key Features:
- Implementation of XGBoost for time-series prediction.
- Use of kNN-based feature selection incorporating wind direction and distance.
- Comparative analysis across multiple prediction horizons (T+1, T+6, T+24, T+48).
- Evaluation of model performance during the pre-lockdown and lockdown periods.

---

## Table of Contents
1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Methodology](#methodology)
4. [Results and Analysis](#results-and-analysis)
5. [Conclusions](#conclusions)
6. [References](#references)

---

## Introduction

Nitrogen dioxide (NO2) is a significant atmospheric pollutant linked to adverse health and environmental impacts. Accurate forecasting of NO2 concentrations can inform policy and mitigate risks. This project combines:
- Meteorological data (e.g., wind speed, temperature) and traffic data.
- Advanced machine learning techniques (XGBoost).
- Feature selection using kNN variations based on wind direction and distance.

---

## Dataset

### Meteorological Data
- **Source:** Manchester Piccadilly Automatic Urban Monitoring Network (AURN).
- **Variables:** Wind direction, wind speed, temperature, humidity, air pressure, and precipitation.
- **Period:** January 1, 2016 – December 31, 2020.

### Traffic Data
- **Source:** Transport for Greater Manchester (TfGM).
- **Details:** Hourly traffic volume from 42 automatic traffic count (ATC) sites within a 3km radius of Piccadilly.

---

## Methodology

### kNN-Based Feature Selection Methods
1. **kNN1:** Selects nearest traffic sites based solely on distance.
2. **kNN2:** Considers traffic sites within 90° of wind direction.
3. **kNN3:** Adjusts distances based on wind direction using a Gaussian kernel.
4. **kNN4:** Enhances kNN3 with greater emphasis on wind direction.
5. **kNN5:** Builds on kNN3, excluding traffic sites with missing values.

### XGBoost
- Gradient boosting framework optimized for speed and accuracy.
- Handles missing values and prevents overfitting through regularization.
- Hyperparameters tuned using RandomizedSearchCV.

### Experimental Design
- Forecasting horizons: **T+1**, **T+6**, **T+24**, **T+48**.
- Periods:
  - **Entire period** (2016–2020).
  - **Pre-lockdown** (2016–March 2020).
  - **Lockdown** (March–May 2020).
- Evaluation metrics: RMSE, MAE, R².

---

## Results and Analysis

### Key Findings
1. **Short-Term Forecasting (T+1):**
   - kNN2 provided the best accuracy using wind direction for feature selection.
2. **Longer Horizons (T+6, T+24, T+48):**
   - kNN1 outperformed other methods, showing distance is more influential than wind direction over time.
3. **Lockdown Analysis:**
   - Models trained on pre-lockdown data failed to predict lockdown NO2 levels accurately, highlighting shifts in traffic and emission dynamics.
4. **Feature Selection:**
   - Models using fewer traffic sites (e.g., kNN2 with K=5) achieved similar accuracy to models with full datasets (K=42).

---

## Conclusions

- **Wind Direction’s Role:** Effective for short-term predictions but less impactful for longer horizons in a small study area (3km).
- **Lockdown Impacts:** Changes in emission sources during the COVID-19 lockdown significantly affected prediction accuracy.
- **XGBoost Strengths:** Successfully handled missing data and outperformed traditional models in air quality forecasting.

### Recommendations for Future Work:
- Expand the study area to include more diverse traffic and meteorological conditions.
- Incorporate additional features (e.g., industrial emissions, population density).
- Test alternative machine learning models like LSTM or hybrid approaches.

---

## References
- Ayus, I., Natarajan, N., & Gupta, D. (2023). Machine learning for air pollution prediction.
- DEFRA (2022). Air pollution in the UK.
- Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system.

For full details, refer to the dissertation and codebase in the repository.
