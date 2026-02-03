# 🛒 Task 12: Customer Segmentation (K-Means Clustering)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-blue?style=for-the-badge&logo=pandas)

## 📌 Project Executive Summary
This project uses **Unsupervised Machine Learning** to identify distinct customer groups in a mall dataset.

By analyzing **Annual Income** and **Spending Score**, we utilized **K-Means Clustering** to separate customers into 5 unique segments. This segmentation allows the marketing team to target specific groups (e.g., "High Spenders") with personalized offers, rather than using a generic "one size fits all" strategy.

## 📂 Dataset Overview
* **Source:** Mall Customer Segmentation Data (Kaggle).
* **Key Features:**
    * `Annual Income (k$)`: Theoretical yearly income.
    * `Spending Score (1-100)`: A score assigned by the mall based on customer behavior and spending nature.

## ⚙️ Technical Methodology

### 1. Determining 'K' (The Elbow Method)
* **Challenge:** K-Means requires us to specify the number of clusters ($K$) beforehand.
* **Solution:** We plotted the **Within-Cluster Sum of Squares (WCSS)** against cluster counts ($1-10$).
* **Result:** The "Elbow Point" (where the decrease in inertia slows down) was clearly visible at **K=5**, indicating 5 natural customer groups.

### 2. Model Training
* **Algorithm:** K-Means++ (Optimized initialization).
* **Validation:** We calculated the **Silhouette Score** to verify that the clusters were dense and well-separated.

## 📊 Business Insights (The 5 Personas)

The model identified 5 distinct customer personas:

1.  **The "Target" (High Income, High Spend):** These are the VIPs. Marketing should target them with luxury items and exclusive membership offers.
2.  **The "Sensible" (Low Income, Low Spend):** These customers are budget-conscious. They prefer discounts, coupons, and sales.
3.  **The "Careless" (Low Income, High Spend):** Often younger customers. They spend impulsively despite lower income.
4.  **The "Frugal" (High Income, Low Spend):** Wealthy but conservative. They need "Value Proposition" marketing to be convinced to buy.
5.  **The "Standard" (Mid Income, Mid Spend):** The average customer. Standard promotions work best here.

### Visual Analytics
* **Scatter Plot:**  Displays the 5 clusters with their centroids (yellow dots), visualizing the clear separation between spending habits.

## 🚀 How to Run
1.  **Run the Script:**
    ```bash
    python customer_segmentation_kmeans.py
    ```
2.  **Output:**
    * Displays the Elbow Plot.
    * Displays the Cluster Scatter Plot.
    * Prints the "Business Labels" for each group.
    * Saves `segmented_customers.csv` with the new Cluster ID attached to each customer.

---
