
# Key Findings – Final Project (Nova Credit Replication)

This document summarizes the modeling strategies, data preparation techniques, evaluations, and final insights of our final project. Our goal was to replicate Nova Credit’s alternative credit scoring methodology using publicly available datasets, and evaluate the feasibility of proposing a similar initiative in Pakistan through a conceptual startup, "CreditDekho".

---

## 1. Models Used and Compared

We evaluated and tuned **7 classification models**, including:

- `RandomForestClassifier`
- `XGBoostClassifier`
- `CatBoostClassifier`
- `LightGBMClassifier`
- `LogisticRegression` (with regularization)
- `KNeighborsClassifier (KNN)` (baseline)
- `Support Vector Classifier (SVC)` (baseline)

All models were tuned using `RandomizedSearchCV` with 3-fold cross-validation and scoring set to `neg_log_loss` to optimize for probabilistic accuracy.

---

## 2. Feature Engineering

Several engineered features were introduced to better capture user behavior and financial health beyond traditional credit variables:

- **TotalDelinquencies**: Sum of 30, 60, and 90-day past due counts.
- **IncomeToDebtRatio**: Monthly income divided by the debt ratio.
- **AppUsagePerApp**: Normalized metric showing average app engagement per app installed.
- **One-hot encoding**: Applied to categorical features like device model, OS, and gender.

These features were designed to mimic the kinds of "alternative data" that Nova Credit uses in the U.S. and provided significant predictive lift.

---

## 3. Outlier Handling Strategies

We tested the following strategies:

- **None**: Retained all data.
- **IQR Removal**: Removed rows with outliers using the Interquartile Range.
- **Mean Replacement**: Replaced outlier values with the mean of the feature.

Outlier strategies were especially effective on variables like `MonthlyIncome`, `App Usage Time`, and `DebtRatio`, which showed heavy right skew.

---

## 4. Missing Value Imputation

To deal with missing entries in numerical variables:

- **Mean Imputation**
- **Median Imputation**
- **Conditional Replacement of Outliers with Mean**

The combination of robust imputation and outlier removal ensured model stability and reduced bias.

---

## 5. Class Imbalance Strategies

The dataset had significantly more Class 1 (creditworthy) observations than Class 0. We tested:

- **No balancing**
- **Undersampling**
- **SMOTE** (Synthetic Minority Oversampling Technique)
- **SMOTEENN**
- **Class weights** for logistic regression and SVC

Balancing was critical for improving **Recall for Class 0**, ensuring fairness in predicting non-creditworthy individuals.

---

## 6. Pipeline Combinations and Configurations

We ran **over 30 unique pipeline combinations** across:

- **Dataset**: Raw vs. Feature Engineered
- **Outlier Handling**: None, Remove, Replace Mean
- **Imputation Strategy**: Mean, Median
- **Scaling**: None, MinMaxScaler, StandardScaler
- **Balancing**: None, SMOTE, Undersampling, SMOTEENN
- **Model + Hyperparameters**

This exhaustive grid was evaluated on both validation and blind test sets.

---

## 7. Evaluation Metrics Used

Each model was evaluated on:

- **LogLoss**: To penalize wrong predictions with high confidence.
- **ROC AUC**: For class separability.
- **Accuracy**
- **Recall**, **Precision**, **F1-score**: For both classes (0 and 1)

This helped identify not just accurate models, but **balanced and fair** classifiers.

---

## 8. Best Model Performance (Blind Test Set)

- **Model**: Random Forest Classifier
- **Preprocessing**: `Raw + NoOutlier + Mean + NoBalance + NoScale`
- **LogLoss**: 0.1669
- **ROC AUC**: 0.9716
- **Accuracy**: 95.2%
- **Recall (Class 0)**: 90.86%
- **F1 Score (Class 1)**: 96.71%

This configuration offered a strong trade-off between accuracy and fairness, and generalized very well on the blind test data.

---

## 9. Summary of Final Insights

- **Tree-based models** (Random Forest, CatBoost, LightGBM, XGBoost) performed best overall, with high recall and generalization.
- **Feature engineering** significantly improved model stability and recall, particularly when behavioral features were introduced.
- **Scaling** worsened performance for tree-based models, while it marginally helped SVC and Logistic Regression.
- **Imbalance correction techniques** like SMOTE and SMOTEENN improved recall for minority class, though sometimes at the cost of precision.
- **CatBoost and LightGBM** showed strong performance across both raw and feature-engineered datasets.

---

This experimentation reflects a rigorous attempt to simulate the logic behind Nova Credit’s approach and prepares the foundation for our proposed Pakistan-specific initiative, **CreditDekho**.
