# Steel Plate Defect Prediction

## **Overview**

This project is dedicated to building and optimizing an ensemble of machine learning models to predict the probabilities of 7 binary defect categories in steel plates. The solution uses data from Kaggle and the original **Steel Plates Faults** dataset from UCI. The main goal is to maximize the **AUC ROC** for each defect category, averaged across all 7 targets.

Both datasets are combined to improve model quality, with thorough data cleaning and advanced feature engineering.

## **Dataset Details**

### **Files**

- **`train.csv`**: Training dataset with features and 7 binary target columns:
  - `Pastry`
  - `Z_Scratch`
  - `K_Scatch`
  - `Stains`
  - `Dirtiness`
  - `Bumps`
  - `Other_Faults`
- **`test.csv`**: Test dataset for which probabilities for all 7 targets must be predicted.

## **Evaluation**

Submissions are evaluated using the **AUC ROC** for each defect category. The final score is the average AUC across all 7 classes.

## **Project Workflow**

### 1. Import Packages
All necessary libraries for data processing, visualization, modeling, and evaluation are imported.

### 2. Data Loading & Preparation
- Load training, test, and additional datasets.
- Combine datasets, remove multi-label rows, and create a unified target variable.
- Clean and perform basic feature processing.

### 3. Feature Engineering
- Create new features (e.g., ratio of length to thickness, normalized thickness, X range multiplied by pixel area).
- Remove irrelevant features.

### 4. Modeling & Ensembling
- Four models are used: **XGBoost**, **LightGBM**, **CatBoost**, and **HistGradientBoostingClassifier** (sklearn).
- Hyperparameters for each model can be tuned using **Optuna**.
- Out-of-fold (OOF) predictions are computed for each model.
- Final prediction is a weighted blend of all models, with weights for each class optimized by maximizing ROC-AUC.

### 5. Model Evaluation
- ROC-AUC is calculated for each model and for the ensemble using OOF predictions.
- Confusion matrices and optimal thresholds for each class are visualized.

### 6. Submission Preparation
- Final class probabilities are saved to a file for Kaggle submission.

## **Technologies Used**

- **Python**: Main programming language
- **Pandas & NumPy**: Data processing and analysis
- **Matplotlib & Seaborn**: Visualization
- **Scikit-learn**: Models, metrics, preprocessing
- **XGBoost, LightGBM, CatBoost**: Boosting models
- **Optuna**: Hyperparameter optimization


## **How to Run the Project**

1. Open the `.ipynb` notebook in Kaggle or Jupyter.
2. Run all cells in order.

## **Submission Format**

The submission file must contain probability predictions for each `id` in the test set for all 7 classes:
- `Pastry`
- `Z_Scratch`
- `K_Scatch`
- `Stains`
- `Dirtiness`
- `Bumps`
- `Other_Faults`


## **Conclusion**

This project implements a complete machine learning pipeline for steel plate defect detection: data merging, feature engineering, building an ensemble of modern boosting models, blending optimization, and result visualization. The final ensemble demonstrates high quality and robustness, making it a reliable solution for industrial diagnostics.
