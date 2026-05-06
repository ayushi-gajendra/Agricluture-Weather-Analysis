# 🌾 Agricultural Weather Analysis: Temperature Forecasting

This repository contains a time-series analysis and predictive modeling project focused on weather patterns in **Boitenberg, Germany**. The goal was to develop a model to assist an agricultural consulting firm in planning growing seasons and predicting harvest profits by forecasting weekly temperatures.

## 📊 Project Overview
The project evolves from basic data exploration to a sophisticated **Multiple Linear Regression** model that accounts for both long-term trends and cyclical seasonality.

### Key Features
* **Time-Series Resampling:** Converted hourly raw data into weekly snapshots to reduce noise and handle independence issues.
* **Feature Engineering:** Created a numerical time index (`idx`) and utilized One-Hot Encoding for seasonal categorical data.
* **Statistical Modeling:** Leveraged `statsmodels` for OLS (Ordinary Least Squares) regression.
* **Model Evaluation:** Applied residual analysis and calculated Mean Absolute Error (MAE) to validate predictive power.

---

## 🛠️ Workflow

### 1. Data Pre-processing
* **Datetime Transformation:** Set `date_time` as the index to enable time-aware operations.
* **Downsampling:** Aggregated data from hourly to weekly frequency using `.resample('W').first()`.
* **Numeric Indexing:** Created a linear integer index to represent the progression of time for the regression algorithm.

### 2. Simple vs. Multiple Regression
* **Phase I:** A simple linear model (Time vs. Temp) showed that time alone explains less than 1% of temperature variance ($R^2 < 0.01$).
* **Phase II:** Introduced **Seasonal Dummy Variables** (Summer, Winter, Spring). This improved the model significantly, explaining over **57%** of temperature fluctuations ($R^2 = 0.575$).

### 3. Model Insights
* **Seasonality:** The model identified that Summer adds $\approx 8.1°C$ to the baseline, while Winter subtracts $\approx 6.4°C$.
* **Trend:** After accounting for seasons, the time index (`idx`) remained statistically insignificant ($p > 0.05$), suggesting no strong long-term warming/cooling trend in this specific dataset.

---

## 📈 Evaluation Results
* **Mean Absolute Error (MAE):** ~3.6°C
* **Interpretation:** On average, the model's predictions are within 3.6°C of the actual temperature.
* **Residuals:** Analysis showed a maximum error of ~14°C, likely corresponding to extreme, non-seasonal weather events.

---

## 🚀 How to Use
1.  **Dependencies:** Ensure you have `pandas`, `seaborn`, `matplotlib`, and `statsmodels` installed.
2.  **Data:** Place `weather_data.csv` in the root directory.
3.  **Run:** Open `Agriculture-Weather-analysis.ipynb` in Jupyter Lab or Notebook.

## 📝 Conclusion
While the seasonal model provides a strong baseline for general planning, the 3.6°C error margin suggests that for sensitive agricultural applications (like frost protection), additional features such as humidity, air pressure, or non-linear models (like Random Forest or LSTM) should be explored.

---

### 📂 Repository Structure
* `Agriculture-Weather-analysis.ipynb`: The complete analysis and code.
* `weather_data.csv`: Historical weather records for Boitenberg.
* `README.md`: Project documentation.
