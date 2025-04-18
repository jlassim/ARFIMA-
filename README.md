# DDoS Attack Detection Using Time Series and ARFIMA Modeling

This project is focused on detecting and forecasting **DDoS attacks** using **time series analysis**. It applies the **ARFIMA model** and compares its performance with the classical **ARIMA** model. The work is based on the `CICDDoS2019` dataset.

---

## Dataset

* **Source**: [CICDDoS2019 - Canadian Institute for Cybersecurity]
* **Format**: `.csv`
* **Contents**: Network traffic flow data labeled as `BENIGN` or `Attack`

---

## Project Workflow

### 1. Data Preprocessing
* Removed whitespaces from column names
* Dropped identifier columns: `Flow ID`, `Src IP`, `Dst IP`, `Timestamp`, `Protocol`
* Replaced infinite values with `NaN`, then dropped all rows with missing values
* Filtered and encoded labels:
  * `BENIGN` → 0
  * All attack labels → 1

### 2. Feature Engineering
* Resampled flow data into time-based intervals (e.g., per 1 second)
* Aggregated features using `mean`, `sum`, `std`, etc.
* Selected a representative time series for modeling (e.g., `Flow Byts/s`, `Fwd Pkts/s`)

### 3. Stationarity Check
* Used **Augmented Dickey-Fuller (ADF) Test** to check stationarity
* Applied differencing if non-stationary

### 4. Granger Causality Feature Selection
* Performed pairwise Granger causality tests
* Selected variables significantly affecting the target series

### 5. Modeling
* Compared:
  * **ARIMA** model (AutoRegressive Integrated Moving Average)
  * **ARFIMA** model (AutoRegressive Fractionally Integrated Moving Average)
* Evaluated using:
  * RMSE (Root Mean Square Error)
  * MAE (Mean Absolute Error)
  * MAPE (Mean Absolute Percentage Error)

### 6. Forecasting & Evaluation
* Visualized prediction vs. actual values
* Compared long-range forecasting capabilities
* Highlighted ARFIMA’s performance on long-memory dependencies

---

## Libraries & Tools

* `pandas`, `numpy` – Data manipulation
* `matplotlib`, `seaborn` – Visualization
* `statsmodels` – Time series modeling, stationarity tests, Granger causality
* `pmdarima` – Auto ARIMA
* `arfima` – Fractional differencing and ARFIMA modeling

---


## Future Work

* Real-time detection system integration
* Deployment as a microservice with alert mechanisms
* Extension to multivariate ARFIMA or deep learning-based hybrid models

---

## Authors

*jlassi maram* 


