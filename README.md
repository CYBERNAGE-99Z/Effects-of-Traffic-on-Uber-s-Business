# Effects of Traffic on Uber's Business

## 🚦 Peak Hour Traffic Analysis & Prediction
### 📌 Introduction

This project presents a comprehensive analysis of peak hour traffic patterns in New York City, considering the influence of weather conditions and special events. The primary objective is to understand key factors affecting congestion and develop predictive models to support better traffic management, planning, and business operations (e.g., Uber surge pricing).

### 📊 Data Sources

- Traffic Data: Hourly traffic counts at multiple junctions

- Weather Data: Temperature, precipitation, wind speed (from National Weather Service)

- Event Data: Concerts, festivals, public holidays, product launches, etc. (with exact timings)

- Uber Case Study: Analysis of how traffic affects Uber’s pricing, driver earnings, availability, and customer satisfaction

### 🧹 Data Merging & Cleaning

- Merged datasets on DateTime basis

- Missing values imputed with suitable methods

- Focused on peak hours only for targeted analysis

### 🤖 Machine Learning Models
Model Development
Multiple models were developed and evaluated using MSE, MAE, and R².
- Grid Search Best Parameters
  - learning Rate: 0.1, Max Depth: 5, Estimators: 100, Subsample: 0.8
  - Performance → MSE: 52.986, MAE: 0.214, R²: 0.999
- Random Search Best Parameters
  - Learning Rate: 0.177, Max Depth: 6, Estimators: 184, Subsample: 0.88
  - Performance → MSE: 0.027, R²: 0.936
- ARIMA → MSE: 477.219
- XGBoost → MSE: 0.0073

XGBoost Model Refinement

- Features included: hour_of_day, day_of_week, month, is_weekend, is_special_event, lag variables, weather features, and location-specific event markers
- Hyperparameter tuning with RandomizedSearchCV (n_estimators, learning_rate, max_depth, subsample, colsample_bytree, gamma)
- Evaluated with time series cross-validation (5 splits)

📈 Aggregated Metrics:

- Mean MAE
- Mean RMSE
- Mean R²

📈 Data Visualization

- Traffic Patterns under Weather → Clear variations observed
- Impact of Events → Significant increases in traffic during special events
- Average Vehicle Count per Hour → 12th, 19th, and 20th hours identified as peak times
- Hourly Congestion:
  - By Hour: Peak at 20th and 21st
  - By Day: Mondays worst; weekends lowest
  - By Month: October–November busiest; January–March lightest

- Residual Analysis (XGBoost)

- Residuals distribution centered at zero → strong predictive performance
- Residual vs. predicted plots show minimal bias
- Temporal residuals confirm stability over time

### 🚖 Uber Case Study: Traffic & Pricing

- Traffic congestion plays a dual role in Uber’s business:
  - Increases Demand: More riders during heavy congestion
  - Decreases Supply: Drivers stuck in longer trips
  - Triggers Surge Pricing: Prices can rise up to 300% during peak congestion
  - Impacts Drivers: Higher fares per trip, but fewer total trips and risk of fatigue
  - Affects Customers: Higher fares + longer wait times → dissatisfaction, alternatives considered

Uber’s response: real-time traffic data integration and predictive analytics for demand forecasting, driver incentives, and strategic positioning.

#### ✅ Conclusion

- Weather and events significantly affect traffic congestion.
- XGBoost delivered the best predictive performance for vehicle counts.
- Business case study (Uber) shows how traffic insights directly influence operations and pricing strategies.

#### ⚙️ How to Run
    # Clone repository
    git clone https://github.com/yourusername/peak-hour-traffic.git
    cd peak-hour-traffic

    # Install dependencies
    pip install -r requirements.txt

    # Run training
    python train.py

    # Run prediction
    python predict.py --input test_data.csv
#### 📌 Tech Stack
- Python (Pandas, NumPy, Scikit-learn, XGBoost, Statsmodels)
- Matplotlib & Seaborn (visualizations)
- Time Series Cross-Validation
