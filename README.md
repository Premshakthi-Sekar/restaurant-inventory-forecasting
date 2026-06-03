# Restaurant Inventory Demand Forecasting & Reorder Recommendation System

## Project Overview
An end-to-end machine learning pipeline that forecasts daily restaurant inventory demand and generates automated reorder recommendations — replacing manual spreadsheet-based stock management with a data-driven decision system.

**Pipeline:**
Raw Data → Cleaning & EDA → Feature Engineering → Model Training → Evaluation → 7-Day Forecasting → Reorder Recommendations

---

## Problem Statement
Restaurants commonly manage stock manually using spreadsheets, leading to over-ordering (waste) or under-ordering (stockouts). This project builds an ML-based solution that predicts daily demand per item and tells the management team exactly when and how much to reorder.

---

## Tech Stack
- **Language:** Python 3
- **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib
- **Model:** Random Forest Regressor
- **Evaluation:** MAE, RMSE vs naive baseline

---

## Dataset
The dataset contains daily inventory records for a food service business with the following fields:

| Column | Description |
|--------|-------------|
| Date | Date of record |
| Item | Ingredient/product name |
| Daily_Usage | Units consumed per day (target variable) |
| Current_Stock | Available stock level |
| Lead_Time | Supplier delivery time in days |
| Seasonal_Factor | Demand multiplier based on season |
| Waste_Percentage | Inventory loss/spoilage rate |

---

## Feature Engineering
Time-series features created to capture demand patterns:

- **Lag features:** lag_1 (yesterday), lag_7 (last week), lag_14 (two weeks ago)
- **Rolling averages:** 7-day and 14-day rolling mean demand
- **Calendar features:** day of week, weekend flag, month, day of month

---

## Model
**Random Forest Regressor** was chosen because:
- Handles nonlinear demand relationships well
- Works effectively on structured tabular data
- Less prone to overfitting than a single decision tree
- Naturally incorporates multiple feature types

---

## Results
The model was evaluated against a naive baseline (using previous day demand as prediction):

| Metric | Random Forest | Baseline |
|--------|--------------|----------|
| MAE | See notebook output | See notebook output |
| RMSE | See notebook output | See notebook output |

---

## Reorder Logic
The reorder recommendation engine calculates:

```
Lead-time demand  = avg daily forecast × lead time days
Safety stock      = avg daily forecast × 1.5 (buffer)
Reorder point     = lead-time demand + safety stock
Reorder quantity  = reorder point − current stock (if stock ≤ reorder point)
```

---

## How to Run

1. Clone this repository
```bash
git clone https://github.com/Premshakthi-Sekar/restaurant-inventory-forecasting.git
cd restaurant-inventory-forecasting
```

2. Install required libraries
```bash
pip install pandas numpy scikit-learn matplotlib
```

3. Open the notebook
```bash
jupyter notebook restaurant_inventory_forecasting.ipynb
```

4. Run all cells from top to bottom

---

## Output Files Generated
- `7_day_forecast_output.csv` — 7-day demand forecast per item
- `reorder_recommendations_output.csv` — reorder action plan
- `daily_usage_trends.png` — usage trend charts
- `seasonal_pattern.png` — monthly demand pattern
- `feature_importance.png` — model feature importance
- `reorder_recommendations.png` — stock vs reorder point chart

---

## Author
**Premshakthi Sekar**  
MSc Artificial Intelligence — Northumbria University  
[LinkedIn](https://www.linkedin.com/in/premshakthi-sekar-a6a328156)
