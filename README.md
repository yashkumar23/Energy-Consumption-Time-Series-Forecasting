
# 🔋 Energy Consumption Time Series Forecasting

## 📌 Project Overview & Objective

This project aims to forecast **household electricity consumption** using historical energy usage data. The notebook builds a forecasting pipeline that cleans the data, engineers time-related features, applies multiple models, and evaluates them to predict future energy demand.

## 🗂️ Dataset Information

The dataset contains minute-level electricity usage data collected from a single household. For modeling purposes, this data is resampled to **hourly** resolution, and only the `Global_active_power` variable is used as the forecasting target.

**Key Preprocessing Steps:**
- Combined `Date` and `Time` columns into a single datetime index.
- Converted data from minute-level to **hourly averages**.
- Removed irrelevant columns to reduce memory usage.
- Handled missing values and non-numeric entries.

## ✨ Key Features

- Data cleaning and resampling
- Time-based feature engineering (hour, day of week, weekend)
- Exploratory analysis of usage patterns
- Multiple forecasting models: ARIMA, Prophet, and XGBoost
- Visual and statistical comparison of forecast accuracy

## 🛠️ Installation

Ensure the following Python libraries are installed:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels prophet xgboost
```

> ⚠️ Note: You may need to install `pystan` or configure `prophet` depending on your system setup.

## 🚀 Workflow Summary

- **Import Libraries**: Essential tools for time series analysis and modeling.
- **Load & Parse Data**:
  - Create datetime index
  - Resample to hourly data
- **Clean Data**:
  - Handle missing/zero values
  - Optimize memory usage
- **EDA**:
  - Plot time series
  - Check distributions and identify seasonality/spikes
- **Feature Engineering**:
  - Extract features like hour, day of week, weekend indicator
- **Train-Test Split**:
  - 80/20 time-based split to ensure realistic evaluation
- **Modeling**:
  - **ARIMA**: For trend and seasonality modeling
  - **Prophet**: Facebook’s additive time series model
  - **XGBoost**: Uses lag and calendar features for regression
- **Evaluation**:
  - Metrics: MAE, RMSE, MAPE
  - Visualization of predictions vs actuals

## 📊 Results and Insights

### 🔎 Key Findings

- Energy usage is **seasonal and periodic**, with daily and weekly cycles.
- The most frequent usage is around **0.4 kW**, with occasional spikes over **6 kW**.
- XGBoost and Prophet models captured trends better than ARIMA for this dataset.

### 🧪 Model Evaluation (Example Results)

| Model     | MAE        | RMSE     | 
|-----------|------------|----------|
| ARIMA     | 0.596989   | 0.799895 |
| Prophet   | 0.654794   | 0.821185 | 
| XGBoost   | 0.498660   | 0.666894 |
 
## 📉 Visualizations

- **Line plots showing hourly energy usage over years.**
  <img width="832" height="270" alt="image" src="https://github.com/user-attachments/assets/46b24c44-ffee-4e1e-9efe-d55b207ba5c3" />

  **Insights:**
  The graph shows:
  - How power use changes over time (2007–2010).
  - We can see regular up-and-down patterns — maybe due to seasons or habits.
  - There are spikes where usage goes really high — likely during heavy appliance use.
  - Some gaps or dips (near 0) might be due to missing data or times when no power was used.

- **Histograms revealing distribution skewness.**
  <img width="529" height="345" alt="image" src="https://github.com/user-attachments/assets/166be42c-08bb-49d1-8a3f-d937de1912d6" />

**Insights:**
  - Most energy usage values are low (below 1.5 kW).
  - A sharp peak is seen around 0.4 kW, showing it's the most common usage.
  - A few high values (above 4 kW) occur rarely – these are spikes.
  - A small second bump around 1.3 kW may show higher usage during busy hours.
  - The data is not normally distributed, so it may need transformation before modeling.
  - Models like ARIMA, Prophet, or XGBoost must handle the skewed shape and outliers well.

- **Actual vs predicted energy usage plots for each model.**
<img width="837" height="343" alt="image" src="https://github.com/user-attachments/assets/f736886e-c901-41ba-82d3-efc5be26f2c8" />

**Insights:**
- **ARIMA :**
    - Forecast is smoother and less reactive.
    - Fails to follow sudden changes in energy use.
    - Good for stable data, but weak for patterns with spikes.

- **Prophet :**

    - Captures overall trend and periodic patterns.
    - Slight delay in response to real peaks/valleys.
    - Performs better than ARIMA, but still misses fine details.

- **XGBoost :**

    - Closely follows the actual energy usage.
    - Accurately captures sudden rises and drops.
    - Best suited for this kind of fluctuating, high-variation data.

**Overall Conclusion:**

- **XGBoost** gives the most accurate forecast.
- Prophet is decent for general trend detection.
- ARIMA struggles with complex, spiky data.

## 🧪 Usage

```bash
# 1. Clone the repository
git clone https://github.com/Shilpachhatani/Energy-Consumption-Time-Series-Forecasting.git

# 2. Navigate to the project directory
cd Energy-Consumption-Time-Series-Forecasting

# 3. Open the notebook
jupyter notebook "Energy Consumption Time Series Forecasting_Main.ipynb"
```

## 🤝 Contributing

Have an idea or want to improve something? Contributions are welcome! Please open an issue or pull request.

## 📬 Contact

For questions or collaboration:
- GitHub: `Shilpachhatani`
- Email: shilpachhatani669@gmail.com
