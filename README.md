# sg-inflation-MLandARIMA-forecast
*Predicting Singapore's MAS Core Inflation using ARIMA, Random Forest and XGBoost.* 
<br>
<br>
<br>
<br>

## 📌 Project Overview

This project forecasts Singapore's MAS Core Inflation by bridging macroeconomic theory with modern machine learning architectures. It compares a traditional econometric model (ARIMA) against tuned tree-based models (Random Forest and XGBoost).

<br>
<br>
<br>
<br>


## 📊 Data Sources

The dataset is constructed by merging four distinct macroeconomic indicators, standardized to a Month-End (ME) frequency:

MAS Core Inflation: The target variable (Source: MAS).

S$NEER (NNSGBIS): Nominal Effective Exchange Rate, representing the Monetary Authority of Singapore's primary policy lever (Source: FRED).

Brent Crude Oil (POILBREUSDM): A proxy for global energy shocks (Source: FRED).

GSCPI: Global Supply Chain Pressure Index, capturing global logistical bottlenecks (Source: New York Fed).


<br>
<br>
<br>
<br>



## 🧠 Methodology & Feature Engineering

A major focus of this project is avoiding standard machine learning pitfalls when dealing with chronological economic data:

Targeted Lags (Economic Intuition): Rather than applying uniform lags, features were engineered based on economic transmission mechanisms. Global shocks (Oil, GSCPI) were given short lags (1, 2, 3 months), while monetary policy (S$NEER) was given structural long lags (6, 9, 12 months) to reflect real-world policy delays.

Chronological Integrity: Used TimeSeriesSplit (expanding window cross-validation) during hyperparameter tuning to completely eliminate look-ahead bias and data leakage.

Hyperparameter Tuning: Conducted an extensive GridSearchCV to optimize tree depth, estimator count, and learning rates, minimizing Out-of-Sample RMSE.


<br>
<br>
<br>
<br>



## 📈 Key Economic Insights

The ML Edge Over ARIMA: Traditional univariate models (like ARIMA) aggressively revert to the historical mean during stable periods, assuming future inflation will smoothly follow past trends. Consequently, they fail to capture the sudden, non-linear macro shocks that define real-world economies. By contrast, the optimized XGBoost and Random Forest architectures successfully mapped distinct thresholds in exogenous variables—such as global supply chain disruptions (GSCPI) and oil price spikes. This allowed the machine learning models to anticipate sudden inflationary spikes and achieve significantly lower forecasting error during periods of peak volatility, proving that multivariate threshold-based models are vastly superior for macroeconomic shock forecasting.






## 📂 Repository Structure

codeML&ARIMA.ipynb: The core end-to-end Python pipeline (Data Ingestion -> Cleaning -> Feature Engineering -> GridSearchCV -> Evaluation).

MAS Core Inflation.xlsx: Raw inflation dataset.

NNSGBIS.csv & POILBREUSDM.csv: Exogenous macroeconomic indicators.

gscpi_data.xls: Global supply chain pressure data.
