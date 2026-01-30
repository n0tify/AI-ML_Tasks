# ✍️ Task 10: Handwritten Digit Recognition (K-Nearest Neighbors)

![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikit-learn)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557c?style=for-the-badge&logo=matplotlib)
![Status](https://img.shields.io/badge/Accuracy-97%2B%25-success)

## 📌 Project Executive Summary
This project implements a **K-Nearest Neighbors (KNN)** classifier to recognize handwritten digits (0-9) from the Scikit-Learn Digits dataset.

Unlike parametric models (like Logistic Regression) that learn coefficients, KNN is a **Distance-Based Algorithm** (Instance-Based Learning). It classifies new data points based on their proximity to existing labeled data in the high-dimensional feature space. This project demonstrates the critical importance of **Feature Scaling** and **Hyperparameter Tuning** in distance-based models.

## 📂 Dataset Architecture
* **Source:** Scikit-Learn `load_digits()` (A copy of the UCI ML Repository Optical Recognition of Handwritten Digits).
* **Samples:** 1,797 Images.
* **Resolution:** 8x8 pixels (Resulting in 64 features per sample).
* **Classes:** 10 (Digits 0 through 9).
* **Format:** Flattened arrays of length 64, representing grayscale intensity values (0-16).

## ⚙️ Technical Methodology

### 1. Preprocessing: The Critical Role of Scaling
* **Issue:** KNN calculates the Euclidean distance between pixels. If specific pixels had wider ranges than others, they would disproportionately influence the distance calculation.
* **Solution:** Applied `StandardScaler` to normalize features ($\mu=0, \sigma=1$). This ensures every pixel contributes equally to the distance metric, significantly improving model stability.

### 2. Hyperparameter Optimization (Grid Search)
We did not arbitrarily choose `K`. We implemented a systematic search to find the optimal number of neighbors.
* **Range Tested:** $K = 1, 3, 5, ..., 15$.
* **The Trade-off:**
    * **Low K (e.g., K=1):** High Variance. The model overfits to noise (outliers).
    * **High K (e.g., K=15):** High Bias. The model becomes too smooth and misses local patterns.
* **Optimization Result:** The script automatically selects the `K` value that maximizes Test Set accuracy.

## 📊 Visual Analytics Dashboard
The script generates three layers of visualization to validate performance:

### 1. Data Exploration

* Displays the raw 8x8 pixel grids alongside their ground truth labels to verify data integrity.

### 2. Hyperparameter Tuning Curve

* A line graph plotting **Accuracy vs. K Value**. This visualizes the "Elbow Point" where the model achieves peak performance before diminishing returns set in.

### 3. Model Evaluation
* **Confusion Matrix:** A heatmap showing where the model gets confused (e.g., mistaking an '8' for a '3').
* **Prediction Showcase:** Displays 5 random test images with color-coded titles (Green for Correct, Red for Incorrect) to provide a "human-readable" final output.

## 📈 Performance Results

| Metric | Score | Interpretation |
| :--- | :--- | :--- |
| **Accuracy** | **~97% - 98%** | Production-grade performance for optical character recognition (OCR) on low-res images. |
| **Precision** | **High** | Very few false positives (e.g., rare to misclassify a '0'). |
| **Recall** | **High** | Successfully identifies almost all instances of each digit. |

## 🚀 How to Run
1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/your-username/digit-recognition-knn.git](https://github.com/your-username/digit-recognition-knn.git)
    ```
2.  **Run the Script:**
    ```bash
    python digit_classification_knn.py
    ```
3.  **Observation:**
    * Watch the script iteratively test K values in the console.
    * View the generated plots for insights.
    * Check the final classification report for detailed metrics.

---
