# Assignment 2: Logistic Regression for Fraudulent Insurance Claims

**Name:** Mohammad Tayyab Alam  
**ERP:** 24157  

##  Objective

Build a logistic regression model to classify fraudulent (1) and non-fraudulent (0) insurance claims using a highly imbalanced insurance dataset.

---

##  Tasks Performed

### 1. Data Preprocessing & EDA (1 Mark)
- Checked for missing values and duplicate entries (none found).
- Dropped high-cardinality and identifier columns.
- Visualized class imbalance and outliers using boxplots and heatmaps.
- Created one-hot encoded features for categorical variables.

### 2. Handling Class Imbalance (2 Marks)
- Applied multiple strategies:
  - **SMOTE**
  - **Automatic Undersampling**
  - **Manual Undersampling (Class Method)**
  - **Cost-Sensitive Learning (Manual weights and class_weight='balanced')**
- Compared their effects on recall, precision, and F1-Score.

### 3. Logistic Regression Model (2 Marks)
- Implemented logistic regression models using:
  - Raw data
  - Feature-engineered data
  - Each class imbalance technique

### 4. Model Evaluation (3 Marks)
- Computed **Accuracy, Precision, Recall, F1-score, AUC-ROC**
- Visualized **Confusion Matrices** for all models
- Evaluated models on full test set and summarized outcomes

### 5. Insights & Recommendations (2 Marks)
- Best model: **Undersampling FULL DATA - Class Method (Feature Engineered)**
- Recall improved to **70%** after **L1 Regularization**
- Tradeoff observed between precision and recall
- Threshold tuning demonstrated using multiple criteria (F1, Recall, False Positives)

---

## 📊 Key Results

| Method                                                | Recall | F1-Score | AUC-ROC |
|-------------------------------------------------------|--------|----------|---------|
| No Class Imbalance (Control)                          | 0.00   | 0.00     | 0.50    |
| SMOTE (Feature Engineered)                            | ~0.20  | ~0.03    | ~0.51   |
| Manual Undersampling (FULL DATA - Feature Engineered) | 0.67   | 0.025    | 0.575   |
| L1 Regularization Applied                             | 0.70   | 0.03     | 0.597   |

---

##  Self-Reflection

This assignment was a deep learning experience for me. Here's what I learned:

- **Understanding the Problem:** Fraud detection is a class imbalance problem where accuracy is misleading. I learned to focus more on recall and F1-score.
- **Modeling:** Logistic regression is powerful, but needs the right data balance and feature representation. I explored its limitations and how to extend its capabilities using class weighting and regularization.
- **Handling Class Imbalance:** I implemented and compared SMOTE, undersampling, and cost-sensitive techniques. The results showed clearly how each strategy trades off between precision and recall.
- **Feature Engineering:** With AI assistance, I created domain-relevant features that greatly improved the model’s understanding of fraud patterns.
- **Critical Evaluation:** This assignment trained me to evaluate models beyond surface metrics and to select them based on business needs (e.g., prioritizing fraud detection even at the cost of false positives).

---

##  AI Assistance & Academic Integrity

- Used **ChatGPT 4o**, **Claude**, and **DeepSeek** to:
  - Generate feature engineering ideas
  - Fix complex bugs and optimize loops
  - Understand the class imbalance strategies
- All **analysis, interpretation, and write-ups** are my own.
- Credit has been acknowledged in the code cells and in this README as per assignment guidelines.

---

##  Files

- `assignment_2.ipynb`: Jupyter Notebook with full code and results
- `assignment_2.py`: Python version for script-based execution
- `insurance_claims.csv`: Dataset used for training and evaluation

---


Thank you for reviewing my work!  
— *Mohammad Tayyab Alam (ERP 24157)*  
