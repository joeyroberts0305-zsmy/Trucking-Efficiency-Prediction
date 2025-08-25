
# 📌 Improving Dock Efficiency and Predicting Delivery Delays in Logistics
### 🚛 Project: Trucking-Efficiency-Prediction

## 🧠 Project Overview: This project analyzes shipment trip data to improve dock scheduling and reduce delivery delays. By using route, time, and location data, we predict which shipments are likely to be delayed and identify inefficient docks and time windows. The goal is to help logistics operations become more efficient through data insights.
## 🔍 Problem Statement: In trucking and logistics, poor dock scheduling and route planning can lead to delays, increased costs, and lower customer satisfaction. This project addresses two challenges: 
1. Predicting whether a delivery will be delayed based on pre-trip data.
2. Identifying bottlenecks at specific docks (origin and destination) to improve scheduling efficiency.
## 📊 Data
**Source**: Kaggle Dataset  
Santanu Kundu. (2025). Delhivery Dataset. [Kaggle](https://doi.org/10.34740/KAGGLE/DSV/10795688)
**Total records:** ~145,000
**Target Variable:** `delay_minutes` (log-transformed)

## 🧠 Modeling Approach & Current Results

### Baseline Model: Linear Regression
I trained a linear regression model on engineered features to predict `delay_minutes` (log-transformed). Initial performance metrics on the test set:
- **MAE:** 0.73  
- **RMSE:** 0.89  
- **R²:** 0.62  
These results indicate the model captures 62% of the variance in delivery delays, which is a strong start given the natural variability in logistics data.

### Key Features Driving Delays
The model relied on operationally meaningful features such as:
- Differences between planned and actual route time (`time_diff_vs_osrm`)
- Discrepancies in estimated vs. actual distance (`distance_diff_vs_osrm`)
- Speed efficiency via `time_per_km` and `osrm_time_ratio`
- Time-of-day and month effects
These features were selected after extensive EDA, transformation, and multicollinearity analysis.

### Residual Diagnostics
Residual plots revealed underestimation of extreme delays and mild heteroscedasticity, both signs that the linear model may not fully capture the complexity of delivery behavior.
---

## 🚧 Next Steps
I observed non-linear patterns and interaction effects that linear regression cannot capture well. To address this:
- I will implement a **hybrid ensemble model**, combining the interpretability of linear models with the flexibility of tree-based models.
- The goal is to improve predictive accuracy, especially for extreme or variable delay scenarios.

This hybrid approach will help operations teams proactively identify high-risk deliveries and respond more effectively.

## 🚀 How to Run the Project

```bash
# Clone this repo
git clone https://github.com/joeyroberts-zsmy/trucking-efficiency-prediction.git

# Install dependencies
pip install -r requirements.txt

# Launch notebook or app
jupyter notebook
```

## 👤 Author
**Joey Roberts, MSDA**  
[GitHub](https://github.com/joeyroberts0305-zsmy) | [LinkedIn](https://www.linkedin.com/in/joey-roberts-msda-aaa919179)
