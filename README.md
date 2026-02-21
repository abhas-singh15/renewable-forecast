#Short-Term Solar Energy Forecasting Using Statistical and Machine Learning Models
#Overview

This project investigates short-term solar energy forecasting using both classical statistical methods and modern machine learning models. The objective is to evaluate model performance under nonlinear weather-driven variability and compare forecasting accuracy over a realistic operational horizon.

The study focuses on hourly solar energy generation forecasting over a 7-day horizon using a rolling 60-day training window.

#Problem Statement

Accurate short-term forecasting of renewable energy generation is critical for:

Grid stability and load balancing

Energy dispatch planning

Storage scheduling

Integration of renewable sources into power systems

Solar generation exhibits:

Strong daily seasonality

High short-term autocorrelation

Nonlinear dependence on meteorological conditions

This project evaluates whether nonlinear machine learning models outperform classical time-series approaches under these characteristics.

#Dataset Description

Multi-year solar energy dataset

Original resolution: 15-minute intervals

Resampled to hourly energy generation

Target variable: Energy delta (Wh)

Meteorological features available: temperature, humidity, cloud cover

Experimental Setup

Training window: Last 60 days (hourly data)

Forecast horizon: 7 days (168 hours)

#Evaluation metrics:

Mean Absolute Error (MAE)

Root Mean Squared Error (RMSE)

#Models Compared
1. Persistence Model (Baseline)

Forecast equation:

𝑦^𝑡=𝑦𝑡−1

Captures short-term autocorrelation and serves as a strong benchmark.

2. SARIMA Model

Configuration:

(1,0,1)(1,0,1,24)

General formulation:

Φ(𝐵𝑠)𝜙(𝐵)(1−𝐵)𝑑(1−𝐵𝑠)𝐷𝑦𝑡=Θ(𝐵𝑠)𝜃(𝐵)𝜀𝑡ΦBs)()1B(1−Bs)Dy=Θ(Bs)θ(B)εt​


Models linear autoregressive structure with daily seasonality (24-hour cycle).

3. Random Forest Regressor

Uses cyclical encoding of hour:

sin(2πh/24)

cos(2πh/24)

Incorporates meteorological variables

Captures nonlinear feature interactions

4. Multi-Layer Perceptron (MLP)

Input: 24-hour rolling window

Neural mapping:

𝑦^=𝑓(𝑊2𝜎(𝑊1𝑋+𝑏1)+𝑏2)y^=f(W2σ(W1X+b1)+b2)

Captures nonlinear temporal dependencies without explicit recurrence.

#Results
Model	MAE	RMSE
Persistence	1067	1902
SARIMA	1555	2892
Random Forest	1168	2214
MLP Neural Network	887	1419

#Forecast Comparison

#7-Day Forecast
<img width="1188" height="590" alt="image" src="https://github.com/user-attachments/assets/5157f9e6-3d06-4dc6-9151-6873e274ebbf" />


#Zoomed 72-Hour Forecast
<img width="1190" height="590" alt="image" src="https://github.com/user-attachments/assets/3861f17c-649a-4d39-b07e-20be45e9c1a1" />


#Key Observations

Strong short-term autocorrelation
The persistence model performs competitively, indicating structural temporal dependence in solar output.

Linear models underperform
SARIMA struggles due to nonlinear weather-driven variability.

Nonlinear ML improves accuracy
Random Forest captures nonlinear interactions but lacks explicit sequential structure.

Neural network performs best
The MLP effectively models nonlinear temporal relationships across daily windows.

#Conclusion

This study demonstrates that nonlinear neural architectures outperform classical statistical models for short-term solar energy forecasting. While persistence remains a strong baseline, advanced machine learning approaches provide improved robustness under meteorological variability.

#Future work may explore:

LSTM / GRU architectures

Multi-horizon forecasting

Hyperparameter optimization

Integration of forecasted weather inputs

#Technologies Used

Python

pandas

NumPy

scikit-learn

statsmodels

matplotlib
