# 📊 Task 3: Exploratory Data Analysis (Iris Dataset)

## 📌 Project Overview
This project focuses on **Exploratory Data Analysis (EDA)** using the classic **Iris Dataset**. The goal was to visualize data distributions, detect outliers, and identify correlations between features to understand which attributes are most valuable for species classification.

This analysis was performed as **Task 3** of the Python Developer Internship.

## 📂 Dataset Information
**Source:** Seaborn Built-in Dataset (`iris`)
**Description:** The dataset consists of 150 samples from three species of Iris (Iris setosa, Iris virginica, and Iris versicolor). Four features were measured from each sample:
* Sepal Length
* Sepal Width
* Petal Length
* Petal Width

## 🛠️ Technologies & Libraries
* **Python 3.x**
* **Pandas:** For data manipulation and structure.
* **Seaborn:** For advanced statistical data visualization.
* **Matplotlib:** For plot customization and layout.

## 📈 Visualizations & Analysis
The script `eda_analysis.py` performs the following steps:

### 1. Univariate Analysis (Histograms)
* **Goal:** To understand the distribution of each numerical feature.
* **Observation:** Petal Length and Petal Width show a **bimodal distribution** (two distinct peaks), suggesting a clear separation between species based on these dimensions.

### 2. Categorical Analysis (Count Plot)
* **Goal:** To check for class imbalance.
* **Observation:** The dataset is perfectly balanced with **50 samples** for each of the three species.

### 3. Outlier Detection (Box Plots)
* **Goal:** To identify anomalies in the data.
* **Observation:** **Sepal Width** contains the most notable outliers, particularly within the *Virginica* species. Other features have a relatively clean spread.

### 4. Multivariate Analysis (Correlation Heatmap)
* **Goal:** To quantify the relationships between features.
* **Observation:**
    * **Strong Positive Correlation:** Petal Length vs. Petal Width (~0.96).
    * **Weak/Negative Correlation:** Sepal Width generally correlates weakly with other features.

## 💡 Key Insights & Conclusion
Based on the visual analysis, the following conclusions were drawn:
1.  **Best Predictors:** **Petal Length** and **Petal Width** are the most critical features for distinguishing between Iris species. They show the clearest separation in histograms and box plots.
2.  **Redundancy:** Due to the extremely high correlation between Petal Length and Width, a model might only need one of these two features to perform well.
3.  **Data Quality:** The dataset is high-quality with no missing values and very few outliers, making it excellent for training basic classification models.

## 🚀 How to Run
1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
    ```
2.  **Install Dependencies:**
    ```bash
    pip install pandas seaborn matplotlib
    ```
3.  **Run the Script:**
    ```bash
    python eda_analysis.py
    ```
    *(Or open the file in Google Colab/Jupyter Notebook and run the cells)*

---
*Created by Anushka Srivastava for Python Developer Internship.*
