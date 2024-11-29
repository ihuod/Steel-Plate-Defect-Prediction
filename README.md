# Steel Plate Defect Prediction

## **Overview**

This project focuses on building and optimizing machine learning models to predict the probabilities of 7 binary defect categories in steel plates. The dataset used for this project was derived from a deep learning model trained on the **Steel Plates Faults dataset** from UCI. The main objective is to maximize the **area under the ROC curve (AUC)** for the predictions of each defect category, averaged across all 7 targets.

The competition dataset (both train and test) is similar, but not identical, to the original UCI dataset. Participants are encouraged to explore the original dataset to analyze differences and potentially improve performance by incorporating it into the training process.

---

## **Dataset Details**

### **Files**

- **`train.csv`**: The training dataset containing features and 7 binary target columns:
  - `Pastry`
  - `Z_Scratch`
  - `K_Scatch`
  - `Stains`
  - `Dirtiness`
  - `Bumps`
  - `Other_Faults`
- **`test.csv`**: The test dataset where predictions for the probabilities of the 7 binary targets are required.

---

## **Evaluation**

Submissions are evaluated using the **area under the ROC curve (AUC)** for each defect category. The final score is calculated as the average of the individual AUC scores across the 7 defect categories.

---

## **Project Workflow**

### **1. Import Packages**
The project begins by importing all necessary libraries and dependencies for data processing, visualization, modeling, and evaluation.

---

### **2. Data Exploration**
Exploratory Data Analysis (EDA) is performed to understand the dataset, including:
- Checking for missing values.
- Analyzing the distribution of features and targets.
- Identifying potential issues such as class imbalance or collinearity.

---

### **3. Data Visualization**
Visualization techniques are used to gain deeper insights into the dataset:
- **Plot Numerical Columns**: Visualizing the distribution of numerical features.
- **Plot Target Columns**: Analyzing the distributions of the 7 binary target columns.
- **Plot Collinearity**: Exploring feature relationships and detecting multicollinearity.

---

### **4. Preprocessing & ML Packages**
Data preprocessing steps are applied to prepare the dataset for machine learning:
- **SMOTE Transform**: Synthetic Minority Oversampling Technique (SMOTE) is used to handle class imbalance by generating synthetic samples for minority classes.
- **Log Transform**: Logarithmic transformation is applied to reduce skewness in feature distributions.
- **Standard Scale Transform**: StandardScaler is applied to normalize numerical features.
- **Ordinal Encode**: Encoding categorical features for compatibility with machine learning algorithms.

---

### **5. Pipeline**
A machine learning pipeline is constructed to streamline preprocessing, model training, and evaluation steps. This ensures reproducibility and simplifies hyperparameter tuning.

---

### **6. Feature Importance**
Feature importance is analyzed to identify the most impactful features for predicting defects:
- **Plot Feature Importance**: Visualizing the contribution of each feature to the model's predictions.

---

### **7. Modeling**
Multiple machine learning models are trained and evaluated to identify the best-performing algorithms. The models include:

- **Tree-based Models**:
  - `DecisionTreeClassifier`
  - `RandomForestClassifier`
  - `GradientBoostingClassifier`
  - `ExtraTreesClassifier`
  - `AdaBoostClassifier`
  - `LGBMClassifier`
- **Linear Model**:
  - `LogisticRegression`
- **Boosting Models**:
  - `XGBClassifier`
  - `CatBoostClassifier`

Each model is evaluated using the ROC AUC metric for all 7 defect categories.

---

### **8. Final Model**
The **CatBoostClassifier** is selected as the final model based on its superior performance during evaluation. The final steps include:
- **Hyperparameter Optimization**: Using **Optuna**, an automated hyperparameter optimization library, to find the best parameters for the `CatBoostClassifier`.
- **ROC AUC Evaluation**: The final model is evaluated on the test dataset, calculating the ROC AUC score for each defect category.
- **Confusion Matrix**: Confusion matrices are plotted to analyze the performance of the final model on each defect category.

---

## **Technologies Used**

- **Python**: Primary programming language for the project.
- **Pandas & NumPy**: Data manipulation and analysis.
- **Matplotlib & Seaborn**: Data visualization.
- **Scikit-learn**: Machine learning models, preprocessing, and evaluation metrics.
- **CatBoost**: Final model for classification.
- **Optuna**: Hyperparameter optimization.
- **Imbalanced-learn (SMOTE)**: Handling class imbalance in the dataset.

---

## **How to Run the Project**

1. Open the attached Python notebook (.ipynb) in Kaggle.

2. Run all code blocks.

---

## **Submission Format**

The submission file must contain predictions for each `id` in the test set, with probabilities for all 7 defect categories:
- `Pastry`
- `Z_Scratch`
- `K_Scatch`
- `Stains`
- `Dirtiness`
- `Bumps`
- `Other_Faults`

---

## **Conclusion**

This project demonstrates a complete machine learning pipeline for defect detection in steel plates. Through careful preprocessing, feature engineering, and model selection, the final **CatBoostClassifier** achieves strong predictive performance, making it a reliable solution for fault detection tasks.

--- 
