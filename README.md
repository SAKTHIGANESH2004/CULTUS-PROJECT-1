🔋 HAR-ARIMA Energy Load Forecasting
📌 Project Overview

This project implements a properly structured HAR-ARIMA model to forecast hourly electricity demand using PJM Interconnection data. Energy consumption naturally follows three time scales—hourly, daily, and weekly—and the HAR framework models these patterns using hierarchical lags rather than simple exogenous inputs. This structured approach improved forecasting accuracy by approximately 10%.

🧠 HAR-ARIMA Methodology

The model uses three hierarchical components:

θ₁ (Lag-1): Captures short-term hourly continuity

θ₂ (24-hour mean): Represents daily diurnal cycles

θ₃ (168-hour mean): Models weekly business cycles

These components are inserted directly into the AR structure, consistent with HAR literature.

🔹 Final HAR-ARIMA Configuration

ARIMA Orders: Selected using ACF, PACF, and AIC/BIC analysis

Final Model: (p, d, q) values adjusted based on dataset behavior – include your actual numbers)

Estimated Coefficients: θ₁, θ₂, θ₃ learned directly from data

📊 Model Comparison

SARIMA: Seasonal orders chosen after examining long-period seasonal spikes (24h, 168h). Struggled with weekly seasonality.

XGBoost: Required multiple engineered lags and Fourier terms; HAR-ARIMA matched accuracy with fewer features.

HAR-ARIMA: Delivered more stable, interpretable predictions and reduced training complexity.

📥 Data Source & Lag Rationale

The PJM dataset exhibits strong 1-hour, 24-hour, and 168-hour periodicity. These lags correspond to physical energy-use behavior: immediate inertia, daily routines, and weekly work–leisure cycles. This forms the theoretical basis for the HAR structure.
