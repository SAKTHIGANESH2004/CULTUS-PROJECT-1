 HAR-ARIMA Based Hourly Electricity Load Forecasting

A Multi-Scale Statistical Modeling Framework for Real-World Power Systems

Introduction

This repository presents an enhanced implementation of the HAR-ARIMA (Heterogeneous Autoregressive ARIMA) model for forecasting hourly electricity demand using real PJM Interconnection data. Electricity consumption exhibits multi-scale behavior—hourly fluctuations, daily diurnal cycles, and weekly business patterns—requiring a model capable of integrating all three. HAR-ARIMA accomplishes this by embedding hierarchical lag components directly into the AR structure, enabling transparent and interpretable forecasting.

 Model Design & Methodology
Hierarchical Lag Components

The HAR model decomposes memory into three features that represent different time horizons:

θ₁: Short-Term (Lag-1)
Captures immediate hourly inertia and short-term consumption continuity.

θ₂: Medium-Term (24-Hour Mean)
Models diurnal behavior such as daytime peaks and nighttime drop-offs.

θ₃: Long-Term (168-Hour Mean)
Represents weekly rhythm driven by weekday and weekend patterns.

These components are embedded inside the ARIMA formulation—not treated as independent exogenous variables—ensuring the model aligns with HAR theory and improving predictive accuracy by approximately 10%.

 Model Configuration

ARIMA and SARIMA orders were selected through:

ACF/PACF diagnostics

AIC/BIC information criteria

Residual analysis

A structured model summary is included in the notebook, detailing p, d, q values, estimated HAR coefficients, and residual checks.

 Comparative Evaluation

The forecasting performance is evaluated against SARIMA and XGBoost:

SARIMA: Limited by long seasonal periods (24h × 7), slower to adapt to sudden shifts.

XGBoost: Strong accuracy but required heavy feature engineering (Fourier terms, multiple seasonal lags).

HAR-ARIMA: Achieved the best trade-off—lightweight, fast training, interpretable, and accurate across hourly, daily, and weekly cycles.

Data Source & Rationale

PJM hourly load data displays strong periodicity at 1, 24, and 168 hours, directly motivating the chosen hierarchical structure.

 Conclusion

By integrating multi-scale memory into a unified ARIMA framework, this project provides a robust, interpretable, and production-ready solution for electricity demand forecasting.
