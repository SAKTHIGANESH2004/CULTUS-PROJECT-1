Hourly Energy Load Forecasting using HAR-ARIMA
Project Overview

This project implements an hourly electricity demand forecasting model using HAR-ARIMA (Hierarchical ARIMA). The dataset comes from the PJM Interconnection, which shows strong hourly, daily, and weekly seasonal patterns. Traditional ARIMA/SARIMA models struggle with long seasonal periods, and machine learning models require heavy feature engineering. HAR-ARIMA solves this by modeling multiple time horizons directly.

Methodology

The HAR-ARIMA approach builds three hierarchical lag-based features:

Short-Term (Lag-1): Captures immediate hourly changes.

Medium-Term (24-hour rolling mean): Models daily day–night patterns.

Long-Term (168-hour rolling mean): Captures weekly business cycles.

These features are fed into a transparent ARIMA structure, making the model efficient, interpretable, and able to capture multi-scale seasonality.

 Model Comparison

The model was compared with SARIMA and XGBoost:

SARIMA struggled with handling long seasonal cycles like 168 hours and responded slowly to sudden demand shifts.

XGBoost showed good accuracy but required many engineered features such as Fourier terms and multiple lags.

HAR-ARIMA achieved competitive or superior accuracy while being lightweight and easy to train.

Conclusion:

By explicitly modeling hourly, daily, and weekly memory, HAR-ARIMA provides an accurate and scalable forecasting solution. Its balance of simplicity, transparency, and performance makes it suitable for real-world energy demand prediction and grid decision-making.
