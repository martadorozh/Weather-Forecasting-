**Weather Forecasting Analysis Report**

## **1. Introduction**
This report presents a comprehensive analysis of weather data for Ukraine, including data preprocessing, exploratory data analysis (EDA), anomaly detection, and time-series forecasting using the Seasonal ARIMA (SARIMA) model. The goal is to clean, analyze, and forecast temperature trends based on historical data.

---
## **2. Data Preprocessing**
### **2.1 Data Loading**
Frome the dataset are selected the following numerical weather variables:
- **Temperature (°C)**
- **Precipitation (mm)**
- **Wind Speed (kph)**
- **Pressure (mb)**
- **Humidity (%)**
- **UV Index**

### **2.2 Filtering Data for Ukraine**
The dataset is filtered to focus only on Ukraine. The necessary columns are selected and converted to a datetime format for time-series analysis.

### **2.3 Anomaly Detection & Handling Outliers**
The Interquartile Range (IQR) method is used to remove anomalies in temperature data:
- Values outside the range \[Q1 - 1.5*IQR, Q3 + 1.5*IQR\] are clipped to maintain data integrity.

### **2.4 Data Aggregation**
- Data is resampled by day using the.
- Missing values are filled using **linear interpolation** to maintain smooth trends in the time series.

---
## **3. Exploratory Data Analysis (EDA)**
### **3.1 Boxplots for Outliers**
Boxplots are generated for each numerical column to visualize potential outliers and distribution trends.

### **3.2 Daily Temperature Trend**
A time-series plot is generated to visualize temperature variations over time for Ukraine.

**Insights:**
- Temperature shows seasonal fluctuations, indicating clear summer and winter trends.
- Occasional missing data points are handled via interpolation.

---
## **4. Time-Series Forecasting Using SARIMA**
### **4.1 Parameter Selection for SARIMA Model**
- The SARIMA model parameters \(p, d, q\) and seasonal \((P, D, Q, s)\) are chosen using grid search.
- Different parameter combinations are tested, and the **Akaike Information Criterion (AIC)** is used for model selection.

### **4.2 Model Training & Evaluation**
The best-selected SARIMA model is trained:
- **Order:** (1,1,1)
- **Seasonal Order:** (0,1,1,12)
- Model summary statistics are presented to assess stationarity and fit quality.

### **4.3 Model Diagnostics**
SARIMA model residuals are analyzed through diagnostic plots:
- **Autocorrelation function (ACF) plot** confirms stationarity.
- **Histogram of residuals** checks normality.
- **Q-Q plot** verifies distribution assumptions.

---
## **5. Forecasting & Performance Evaluation**
### **5.1 Short-Term Forecasting (One-Step Ahead Prediction)**
- Forecasting is performed for the period starting **January 21, 2025**.
- The forecast is compared with actual data to measure performance.

### **5.2 Forecast Confidence Intervals**
- The 95% confidence interval for predicted values is plotted.

### **5.3 Performance Metrics**
Model accuracy is evaluated using:
- **Mean Squared Error (MSE)**: Measures average squared errors.
- **Root Mean Squared Error (RMSE)**: Measures standard deviation of prediction errors.

**Results:**
- **MSE:** 4.41
- **RMSE:**  2.0991563491100886

### **5.4 Long-Term Forecasting**
- Forecast for the next **10 days** is generated and visualized.
- Predictions are plotted along with historical data for trend comparison.

---
## **6. Conclusion & Future Work**
### **6.1 Summary of Findings**
- Seasonal variations are evident in temperature trends.
- SARIMA model effectively captures temperature seasonality.
- Forecasts show reasonable accuracy but can be further improved with additional data and alternative models (e.g., LSTMs).

### **6.2 Future Enhancements**
- Incorporation of external factors such as wind speed, humidity, and atmospheric pressure.
- Application of deep learning techniques like LSTMs or Prophet models.
- Real-time weather prediction system development.

