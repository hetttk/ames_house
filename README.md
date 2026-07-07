# 🏠 House Price Prediction — Ames Housing Dataset


A complete, well-documented feature engineering + baseline modeling pipeline built on the famous **Ames Housing Dataset**, designed to predict `SalePrice`. This project is a great hands-on exercise for practicing real-world data cleaning, feature creation, encoding strategies, outlier handling, and scaling — the core skills every ML practitioner needs before modeling.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Feature Engineering Pipeline](#-feature-engineering-pipeline)
- [Getting Started](#-getting-started)
- [Results](#-results)
- [Tech Stack](#-tech-stack)
- [Next Steps](#-next-steps)

---

## 🔎 Overview

This notebook takes the raw Ames Housing dataset and transforms it into a model-ready dataset through a structured feature engineering workflow, then trains and compares two baseline regression models (**Linear Regression** and **Random Forest**) to predict house sale prices.

---

## 📊 Dataset

- **Source:** Ames Housing Dataset (Iowa residential home sales, 2006–2010)
- **Size:** ~2,930 rows × 82 columns
- **Target Variable:** `SalePrice`

> ⚠️ Place `AmesHousing.csv` in the same folder as the notebook before running it.

---

## 📁 Project Structure

```
house_price_project/
│
├── House_Price_Prediction.ipynb   # Main Jupyter notebook
├── AmesHousing.csv                 # Dataset (add this yourself)
└── README.md                       # You are here 📍
```

---

## 🛠 Feature Engineering Pipeline

| Step | Technique | Applied To |
|------|-----------|------------|
| 1️⃣ Missing Values | Median (numeric) / Mode / "None" (categorical) | All columns with NaNs |
| 2️⃣ Log Transformation | `log1p` to fix right-skew | `SalePrice`, `Lot_Area` |
| 3️⃣ New Features | Derived engineered columns | `HouseAge`, `TotalBathrooms`, `TotalPorchArea` |
| 4️⃣ Ordinal Encoding | Ordered integer mapping (Po→Ex) | `Exter_Qual`, `Kitchen_Qual` |
| 5️⃣ One-Hot Encoding | `pd.get_dummies` | `Neighborhood`, `House_Style` |
| 6️⃣ Outlier Detection | Z-Score (\|z\| > 3) & IQR (1.5×IQR) | `SalePrice`, `Gr_Liv_Area`, `Lot_Area`, etc. |
| 7️⃣ Feature Scaling | `StandardScaler` | All key numeric features |

### 🧮 New Feature Formulas

```python
HouseAge        = Yr_Sold - Year_Built
TotalBathrooms  = Full_Bath + 0.5*Half_Bath + Bsmt_Full_Bath + 0.5*Bsmt_Half_Bath
TotalPorchArea  = Open_Porch_SF + Enclosed_Porch + 3Ssn_Porch + Screen_Porch + Wood_Deck_SF
```

---

## 🚀 Getting Started

### 1. Clone / Download this project

### 2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

### 3. Add the dataset
Download the **Ames Housing Dataset** and place `AmesHousing.csv` in the project folder.

### 4. Run the notebook
```bash
jupyter notebook House_Price_Prediction.ipynb
```

Run all cells top to bottom — the notebook is fully self-contained.

---

## 📈 Results

The notebook trains and compares two baseline models on log-transformed `SalePrice`:

| Model | Metric Reported |
|-------|-----------------|
| Linear Regression | RMSE, MAE, R² |
| Random Forest Regressor | RMSE, MAE, R² |

It also visualizes:
- 📉 Missing value breakdown
- 📊 Before/after skew correction histograms
- 🔥 Correlation heatmap of engineered features vs. target
- 🎯 Actual vs. Predicted scatter plot
- 🏆 Top 15 feature importances (Random Forest)

---

## 🧰 Tech Stack

![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Numerical%20Computing-013243?logo=numpy&logoColor=white)
![Scikit--learn](https://img.shields.io/badge/scikit--learn-ML%20Models-F7931E?logo=scikit-learn&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Viz-3776AB)

---

## 🔭 Next Steps

- 🔧 Hyperparameter tuning with `GridSearchCV` / `RandomizedSearchCV`
- 🚀 Try Gradient Boosting models: **XGBoost**, **LightGBM**, **CatBoost**
- 🧪 K-Fold Cross-Validation for more robust evaluation
- 🧹 Feature selection to reduce dimensionality (Lasso, RFE)
- 🧬 Model ensembling / stacking

---

## 📄 License

This project is intended for educational and portfolio purposes. The Ames Housing Dataset is publicly available for research and educational use.

---

<p align="center">Made with ❤️ for learning practical Data Science & Machine Learning</p>
