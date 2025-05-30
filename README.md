# 🏠 House Price Prediction

**An end-to-end machine learning pipeline that forecasts home sale prices with high accuracy, empowering stakeholders to make data-driven decisions.**

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Installation](#installation)
4. [Workflow](#workflow)

   * [Data Cleaning & Exploration](#data-cleaning--exploration)
   * [Feature Engineering](#feature-engineering)
   * [Feature Selection](#feature-selection)
   * [Model Training & Comparison](#model-training--comparison)
5. [Results](#results)
6. [Dependencies](#dependencies)
7. [Next Steps](#next-steps)
8. [License](#license)
9. [Contact](#contact)

---

## 🔍 Project Overview

Predict sale prices of houses using regression models trained on a comprehensive dataset of 21,613 records and 21 features. This pipeline covers data preprocessing, feature engineering, model building, and evaluation.

---

## 🗄️ Dataset

* **File:** `data/HousingDataSet.csv`
* **Records:** 21,613
* **Key Features:**

  * **Numeric:** `bedrooms`, `bathrooms`, `sqft_living`, `sqft_lot`, `floors`, `grade`, `price` (target)
  * **Categorical:** `waterfront`, `view`, `condition`
  * **Temporal:** `date` (expanded to year, month, day, quarter, is\_weekend)

---

## ⚙️ Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/abhishek-yadav/house-price-prediction.git
cd house-price-prediction
python3 -m venv venv
source venv/bin/activate    # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `notebooks/House_Price_Prediction.ipynb` to follow along.

---

## 📝 Workflow

### 1. Data Cleaning & Exploration

* Imputed missing `sqft_above` values with median.
* Winsorized outliers in `sqft_lot` and `sqft_living` using the IQR method.
* Visualized distributions (histograms) and correlations (heatmaps) to understand feature relationships.

### 2. Feature Engineering

* Extracted temporal features: year, month, day, quarter, is\_weekend.
* Derived metrics: **HouseAge** (current year − `yr_built`), **RoomsPerSqft** (`bedrooms + bathrooms` / `sqft_living`).
* One-hot encoded categorical fields: `waterfront`, `view`, `condition`.

### 3. Feature Selection

* Applied **SelectKBest**, **RFE**, **SelectFromModel**, and **SequentialFeatureSelector** to identify top predictors.
* Final top features: `sqft_living`, `grade`, `lat`, `sqft_lot`, `view`, and others.

### 4. Model Training & Comparison

Trained and evaluated multiple regressors:

| Model                   |  R² Score  | RMSE (USD) |  MAE (USD) |
| ----------------------- | :--------: | :--------: | :--------: |
| Linear Regression       |    0.69    |   115,430  |   78,112   |
| Random Forest Regressor |    0.88    |   87,102   |   60,350   |
| **CatBoost Regressor**  | **0.8915** | **83,429** | **57,425** |
| XGBoost Regressor       |    0.89    |   84,200   |   58,000   |
| LightGBM Regressor      |   0.8838   |   86,334   |   59,513   |

* Used randomized search and grid search with 5-fold cross-validation for hyperparameter tuning.

---

## 📈 Results

* 🎯 **Top Performer:** CatBoost Regressor (R² = 0.8915, RMSE = \$83k, MAE = \$57k).
* 🔑 **Key Drivers:** `sqft_living`, `grade`, `lat`, `sqft_lot` explain the majority of price variance.
* 🚀 **Performance Boost:** Achieved a \~5% R² uplift over baseline models.

---

## 🛠️ Dependencies

* Python 3.8+
* pandas, numpy, matplotlib, seaborn
* scikit-learn, catboost, xgboost, lightgbm
* jupyter, yellowbrick

Install all dependencies via:

```bash
pip install -r requirements.txt
```

---

## 🚀 Next Steps

1. **Deployment:** Serve the best model with FastAPI for real-time predictions.
2. **Dashboard:** Create an interactive Power BI or Tableau dashboard to visualize predictions and feature impacts.
3. **Enrichment:** Integrate external data (e.g., crime rates, school ratings) to improve accuracy.
4. **Automation:** Schedule periodic retraining and monitor model drift.

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## 📫 Contact

Abhishek Kumar Yadav – [abhishekyadav23122002@gmail.com](mailto:abhishekyadav23122002@gmail.com)
[LinkedIn](https://www.linkedin.com/in/abhishek-yadav-52b346201)
[GitHub Portfolio](https://github.com/abhishek-yadav)
