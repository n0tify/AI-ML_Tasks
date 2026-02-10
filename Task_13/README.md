# 📉 Task 13: PCA (Dimensionality Reduction)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Math](https://img.shields.io/badge/Linear_Algebra-Eigenvectors-red)

## 📌 Project Executive Summary
This project applies **Principal Component Analysis (PCA)** to the Handwritten Digits dataset (MNIST-like).

The goal is **Data Compression**: Can we reduce the image data from 64 dimensions (pixels) down to a smaller number without losing critical information? We successfully compressed the data by **~40%** while maintaining **96%+ model accuracy**, demonstrating the power of feature extraction.

## 📂 Dataset Overview
* **Source:** Scikit-Learn `load_digits`.
* **Original Dimensions:** 64 Features (8x8 pixel grid).
* **Target:** To reduce features while preserving "Variance" (Information).

## ⚙️ Technical Methodology

### 1. Preprocessing (Standardization)
* **Rule:** PCA is extremely sensitive to unscaled data because it seeks directions with maximum variance.
* **Action:** Applied `StandardScaler` to normalize pixel intensity distributions ($\mu=0, \sigma=1$).

### 2. Explained Variance Analysis
We plotted the **Cumulative Explained Variance** to determine the optimal number of components.
* **Findings:**
    * 10 Components explain ~60% of the data.
    * 40 Components explain ~95% of the data.
    * **Decision:** We selected the number of components required to retain **95%** of the variance.

### 3. Model Performance Test
We trained a Logistic Regression classifier on both datasets to compare efficiency.

| Metric | Original Data (64 Features) | PCA Reduced Data (~40 Features) |
| :--- | :--- | :--- |
| **Accuracy** | ~97.0% | ~96.5% |
| **Training Time** | Slower | **Faster** |
| **Storage** | 100% | **~60%** |

*Conclusion:* PCA sacrificed negligible accuracy (<0.5%) for a significant reduction in computational complexity.

## 📊 Visual Analytics

### 1. 2D Projection
We projected the 64-dimensional data onto a 2D plane (Principal Component 1 vs. Principal Component 2).
* **Observation:** Distinct clusters of digits (like '0' and '1') formed naturally, proving that PCA captures the fundamental structure of the data even in just 2 dimensions.

### 2. Image Reconstruction
We visualized the "Lossiness" of the compression.
* **Top Row:** Original 8x8 Images.
* **Bottom Row:** Images reconstructed from PCA components.
* **Result:** The reconstructed images are slightly blurry but the digits are still clearly readable.

## 🧠 Interview Q&A (Concepts)

**Q: What problem does PCA solve?**
*A: The "Curse of Dimensionality." It reduces noise, speeds up training, and allows visualization of high-dimensional data.*

**Q: What is Explained Variance?**
*A: A measure of how much "information" (spread of data) is captured by each Principal Component.*

**Q: Why is scaling required?**
*A: PCA maximizes variance. If one feature has a range of 0-1000 and another 0-1, PCA will only focus on the large feature unless they are scaled equally.*

## 🚀 How to Run
1.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/your-username/pca-digits.git](https://github.com/your-username/pca-digits.git)
    ```
2.  **Run the Script:**
    ```bash
    python mnist_pca_reduction.py
    ```
3.  **Output:**
    * Variance Plot.
    * 2D Scatter Plot.
    * Reconstruction Comparison.
    * Accuracy/Time Comparison Report.

---
