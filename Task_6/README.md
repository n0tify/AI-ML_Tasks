# 🏡 Task 6: Linear Regression (California House Pricing)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-Data_Analysis-150458?style=for-the-badge&logo=pandas)

## 📌 Project Overview
This project implements a **Linear Regression** model to predict housing prices in California. The goal is to analyze how features such as **Median Income**, **House Age**, and **Location (Latitude/Longitude)** influence the market value of a home.

> **Note on Data Source:** This script is optimized for **Google Colab**. It utilizes the local `sample_data` directory to bypass external HTTP restrictions often encountered with the Scikit-Learn fetchers.

## 📂 Dataset Details
* **Source:** Google Colab Local Sample Data (`/content/sample_data/california_housing_train.csv`)
* **Rows:** ~17,000 samples
* **Features:** 8 numerical features (longitude, latitude, housing_median_age, total_rooms, etc.)
* **Target Variable:** `median_house_value` (Continuous numeric value)

## ⚙️ Methodology & Implementation

### 1. Data Loading (Colab-Specific Fix)
Standard `fetch_california_housing` calls often fail in cloud environments due to connection timeouts (HTTP 403).
* **Solution:** The script is hardcoded to load the pre-installed CSV file found in every Colab instance:
    ```python
    pd.read_csv("/content/sample_data/california_housing_train.csv")
    ```

### 2. Preprocessing
* **Feature Separation:** The dataset is split into `X` (Features) and `y` (Target: `median_house_value`).
* **Train-Test Split:**
    * **Training Set (80%):** Used to fit the linear equation line.
    * **Testing Set (20%):** Kept unseen to objectively measure the model's accuracy.
    * *Random State:* Fixed at `42` to ensure reproducibility.

### 3. Model Training
* **Algorithm:** Ordinary Least Squares (Linear Regression).
* **Library:** `sklearn.linear_model.LinearRegression`.
* **Process:** The model calculates the optimal weights (coefficients) for each feature to minimize the residual sum of squares between the observed and predicted targets.

## 📊 Evaluation Metrics
We use two key metrics to quantify the model's error margins:

| Metric | Value (Approx) | Interpretation |
| :--- | :--- | :--- |
| **MAE (Mean Absolute Error)** | `~0.53` | On average, our prediction is off by ~\$53,000 (since units are in $100k). |
| **RMSE (Root Mean Sq Error)** | `~0.74` | Penalizes large errors more heavily than MAE. A lower value indicates a better fit. |

## 📈 Visualizations
The script generates a dashboard with two critical plots:

### 1. Actual vs. Predicted (Scatter Plot)
* **X-Axis:** Actual Prices | **Y-Axis:** Predicted Prices
* **The Red Line:** Represents "Perfect Prediction".
* **Insight:** The closer the blue dots cluster around the red dashed line, the more accurate the model.
    * *Observation:* You may notice a "ceiling" effect at the top value (500,000). This indicates the data was capped during collection.

### 2. Feature Importance (Coefficients)
* **Green Bars:** Positive correlation (e.g., Higher Income → Higher Price).
* **Red Bars:** Negative correlation (e.g., Further Inland → Lower Price).
* **Insight:** **Median Income** is typically the strongest predictor of house prices.

## 🚀 How to Run in Google Colab
1.  Create a new Notebook.
2.  Copy the code from `linear_regression_house_fixed.py`.
3.  Run the cell.
    * *No external file uploads required.*
    * *No internet download permissions required.*

---
