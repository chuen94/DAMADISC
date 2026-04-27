# A Deep Learning Framework for Predictive Maintenance of Evaporation Station Instruments via Temporal Feature Engineering

## Overview
This project introduces a time-series deep learning model to perform predictive maintenance on evaporation station instruments. By analyzing non-stationary industrial data, the pipeline successfully separates true mechanical equipment wear from normal day-to-day operational fluctuations to predict the Remaining Useful Life (RUL) of critical actuators.

## The Dataset
The analysis uses the **DAMADICS benchmark dataset** collected from the Lublin Sugar Factory. It comprises 2.16 million continuous records across 32 sensor variables. To manage high-frequency noise and non-stationary production loads, a Rolling Moving Average was applied, and statistical profiling was used to isolate key thermodynamic and mechanical signals.

## Modeling

* **LSTM + CUSUM:** A Long Short-Term Memory network processes strictly causal Cumulative Sum (CUSUM) features to capture long-term wear patterns and forecast continuous RUL without target leakage.

## Key Results
* **Prognostic Performance:** Achieved an R² of 0.9971 and an RMSE of 0.0154 for continuous RUL prediction.

## Repository Structure
* `merged_data.ipynb`: Combines all 25 days' datasets.
* `data_cleaning.ipynb`: Handles noise reduction, and prepares the raw sensor data.
* `EDA.ipynb`: Exploratory Data Analysis covering statistical profiling (stability, kurtosis, drift magnitude) and feature selection.
* `model.ipynb`: Feature engineering (CUSUM) and RUL forecasting.

## Limitations & Future Work
While highly precise, the current architecture operates sequentially and relies heavily on offline batch processing. Future iterations will explore transitioning to a real-time streaming system, compressing the models for edge-hardware deployment, and implementing dynamic feedback loops between the predictive and diagnostic modules.
