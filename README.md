# Retail Demand Forecasting Using Machine Learning

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Status](https://img.shields.io/badge/Status-Complete-green)
![Dataset](https://img.shields.io/badge/Dataset-Walmart%20M5-orange)

## Overview
End-to-end machine learning pipeline to forecast retail product demand using 
historical Walmart sales data. Built as a portfolio project for MSc Data Analytics 
application at Dublin City University.

## Research Question
> *"Can historical sales data predict weekly product demand across retail categories, 
> and which ML model performs best for inventory optimisation?"*

## Results
| Model | MAE | RMSE | R² |
|-------|-----|------|----|
| Linear Regression | 1.29 | 2.40 | — |
| Random Forest | 1.30 | 2.38 | — |
| **Gradient Boosting** | **1.24** | **2.34** | **0.70** |

Gradient Boosting best performer — explains 70% of sales variance.

## Project Structure
```
retail-demand-forecasting/
├── 01_EDA.ipynb              # Exploratory Data Analysis
├── 02_features.ipynb         # Feature Engineering
├── 03_Models.ipynb           # Model Training & Comparison
├── 04_evaluation.ipynb       # Evaluation & Interpretation
├── reports/                  # Charts & final report
├── requirements.txt          # Dependencies
└── README.md
```

## Dataset
Walmart M5 Forecasting Competition — [Kaggle](https://www.kaggle.com/competitions/m5-forecasting-accuracy)
- 30,490 products × 1,913 days
- Scope: Store CA_1, Category FOODS
- Files: sales, calendar, sell_prices

## Features Engineered
- Time features: year, month, week, day of week, quarter
- Lag features: 7, 14, 28 days
- Rolling means: 7, 14, 28 day windows
- Event/promotion indicators
- SNAP benefit day flags

## Models Used
- Linear Regression (baseline)
- Random Forest (100 estimators)
- Gradient Boosting (100 estimators) ← best

## Tech Stack
Python · Pandas · NumPy · Scikit-learn · Matplotlib · Seaborn · Jupyter

## How to Reproduce

### 1. Clone the repo
```bash
git clone https://github.com/naveed8606/retail-demand-forecasting.git
cd retail-demand-forecasting
```

### 2. Create virtual environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Download data
1. Go to [Walmart M5 Competition](https://www.kaggle.com/competitions/m5-forecasting-accuracy/data)
2. Accept competition rules
3. Download all files
4. Place CSVs in `data/raw/`:
   - `calendar.csv`
   - `sales_train_validation.csv`
   - `sales_train_evaluation.csv`
   - `sell_prices.csv`

### 5. Run notebooks in order
| Notebook | Description |
|----------|-------------|
| `01_EDA.ipynb` | Exploratory Data Analysis |
| `02_features.ipynb` | Feature Engineering |
| `03_Models.ipynb` | Model Training |
| `04_evaluation.ipynb` | Evaluation & Results |

> Update `DATA_PATH` and `PROCESSED` variables in each notebook to match your local path.


## Author
**Naveed Nihan** 