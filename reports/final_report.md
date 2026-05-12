# Retail Demand Forecasting Using Historical Sales Patterns
## A Machine Learning Approach
**Author:** Naveed Nihan  
**Dataset:** Walmart M5 Competition (Kaggle)  
**Date:** May 2026

---

## Abstract
This project develops a machine learning pipeline to forecast retail product demand 
using historical sales data from Walmart. Three models were evaluated — Linear 
Regression, Random Forest, and Gradient Boosting. Gradient Boosting achieved the 
best performance (MAE: 1.24, RMSE: 2.34, R²: 0.70), demonstrating strong predictive 
capability for inventory optimisation.

---

## 1. Introduction
### 1.1 Background
Retail demand forecasting is a critical operational challenge. Overstocking increases 
holding costs; understocking leads to lost sales and poor customer experience. 
Accurate forecasting enables retailers to optimise inventory levels, reduce waste, 
and improve service levels.

### 1.2 Research Question
*"Can historical sales data predict weekly product demand across retail categories, 
and which ML model performs best for inventory optimisation?"*

### 1.3 Objectives
1. Forecast demand using historical Walmart sales data
2. Compare ML models: Linear Regression, Random Forest, Gradient Boosting
3. Identify key demand drivers (seasonality, promotions, lag features)
4. Translate model outputs into actionable inventory recommendations

---

## 2. Dataset
### 2.1 Source
Walmart M5 Forecasting Competition dataset (Kaggle, 2020).

### 2.2 Files Used
| File | Description | Size |
|------|-------------|------|
| sales_train_validation.csv | Daily unit sales per product | 30,490 rows × 1,919 cols |
| calendar.csv | Dates, events, SNAP days | 1,969 rows |
| sell_prices.csv | Weekly prices per store/item | 6,841,121 rows |

### 2.3 Scope
Filtered to Store CA_1, Category FOODS — 1,437 products over 1,913 days.

---

## 3. Methodology
### 3.1 Exploratory Data Analysis
- Sales trend analysis over 5-year period
- Category and state-level breakdown
- Seasonality and event impact analysis

### 3.2 Feature Engineering
| Feature | Description |
|---------|-------------|
| year, month, week, dayofweek | Time-based features |
| is_weekend | Binary weekend indicator |
| is_event | Binary event/holiday indicator |
| snap_CA | SNAP benefit day indicator |
| lag_7, lag_14, lag_28 | Previous sales at 7/14/28 day lags |
| rolling_mean_7/14/28 | Rolling average sales |

### 3.3 Train/Test Split
Time-based split: train ≤ 2015-12-31, test > 2015-12-31.
No random shuffle — preserves temporal order.

### 3.4 Models
1. **Linear Regression** — baseline model
2. **Random Forest** — ensemble, 100 trees
3. **Gradient Boosting** — sequential ensemble, 100 estimators

---

## 4. Results
### 4.1 Model Comparison
| Model | MAE | RMSE | R² |
|-------|-----|------|----|
| Linear Regression | 1.29 | 2.40 | — |
| Random Forest | 1.30 | 2.38 | — |
| **Gradient Boosting** | **1.24** | **2.34** | **0.70** |

### 4.2 Key Findings
- Gradient Boosting outperforms all models on MAE and RMSE
- R² of 0.70 indicates model explains 70% of sales variance
- Lag features (lag_7, lag_28) are strongest predictors
- Rolling means capture trend momentum effectively
- Events and SNAP days show measurable sales uplift

---

## 5. Business Interpretation
- Average forecast error: **1.24 units per item per day**
- Recommended safety stock buffer: **~1.9 units/item/day**
- Model identifies high-demand periods aligned with events/promotions
- Enables proactive replenishment vs reactive ordering

---

## 6. Conclusion
This project demonstrates an end-to-end ML pipeline for retail demand forecasting. 
Gradient Boosting achieves strong predictive performance (R²=0.70) on real Walmart 
data. Lag and rolling features prove most valuable, confirming that recent sales 
history is the strongest predictor of future demand.

Future work could include: XGBoost/LightGBM models, store-level cross-validation, 
price elasticity features, and deep learning approaches (LSTM).

---

## 7. References
- Makridakis, S., Spiliotis, E., & Assimakopoulos, V. (2022). M5 accuracy competition
- Walmart M5 Dataset — Kaggle (2020)
- Scikit-learn Documentation — https://scikit-learn.org
- Pandas Documentation — https://pandas.pydata.org

---

## Appendix
- `notebooks/01_EDA.ipynb` — Exploratory Data Analysis
- `notebooks/02_features.ipynb` — Feature Engineering
- `notebooks/03_models.ipynb` — Model Training
- `notebooks/04_evaluation.ipynb` — Evaluation
- `reports/` — All charts and visualisations