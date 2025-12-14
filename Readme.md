# Patient Activity Forecasting

This project focuses on forecasting daily patient step counts by combining
time-series mobility data with clinical and demographic information.
It was developed as part of a Machine Learning Intern assignment.

---

## Project Overview

The goal of this project is to predict future patient activity levels
(daily step counts) using:

- High-frequency step-count data from mobile devices
- Clinical data including demographics, therapies, diagnoses, side effects, and events

The solution integrates data engineering, time-series forecasting,
and explainable machine learning techniques.

---

## Data Description

### 1. Time-Series Data
- Granular step-count intervals
- Aggregated into daily step counts
- Converted into a continuous daily timeline without gaps

### 2. Clinical Data
- Demographics (age, gender)
- Therapy intervals
- Side effects with intensity
- Diagnoses over time
- Clinical events such as relapse

All clinical features are mapped onto the daily timeline to represent
the complete patient state for each day.

---

## Methodology

### Data Processing
- Converted timestamps to Python datetime (UTC)
- Aggregated interval data into daily totals
- Created lag features and calendar-based features
- Fused clinical events into daily binary and numeric indicators

### Models Used
1. **Baseline Model (Univariate)**
   - SARIMA model using only historical step counts
   - Captures overall trends and weekly seasonality

2. **Multivariate Model**
   - Random Forest Regressor
   - Uses step history and engineered clinical features
   - Allows non-linear relationships and provides feature importance

### Evaluation
- Temporal train-test split (80/20)
- Metrics used:
  - RMSE (Root Mean Squared Error)
  - MAE (Mean Absolute Error)

---

## Explainability

Feature importance from the Random Forest model is used to understand
the impact of different variables on predicted step counts.
This helps interpret how recent activity, therapies, and clinical factors
influence patient mobility.

---

## Forecast Output

The final output is a 365-day forecast with the following structure:

| Date | Predicted_Steps | Trend_Component | Exogenous_Impact |
|------|-----------------|-----------------|------------------|

---

## Tech Stack

- Python
- Pandas, NumPy
- Scikit-learn
- Statsmodels
- Google Colab

---

## Repository Contents

patient-activity-forecasting/
│
├── patient_activity_forecasting.ipynb
├── README.md


---

## Notes

- The notebook is designed to run end-to-end in Google Colab
- AWS S3 upload logic is included as a commented optional step
- No credentials or sensitive data are hard-coded

---

## Author

Niraj Sawant