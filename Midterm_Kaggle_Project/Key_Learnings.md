#  Key Learnings – Midterm Kaggle Competition (Spring 2025)

This document outlines the key takeaways from my experience participating in the Financial Data Analytics (FDA) Kaggle midterm competition. The competition tasked students with building the best possible machine learning model to predict customer overstress using a labeled dataset.

---

##  My Approach

As a student with a limited machine learning background before this course, my initial strategy focused on mastering data preprocessing and gradually layering complexity into my models. Here's how I structured my workflow:

### 1. **Start Simple, Then Iterate**
- I began with basic models like **Decision Trees** and **Logistic Regression** to understand the data and pipeline flow.
- As I learned new techniques in class, I implemented them immediately in my submissions.

### 2. **Model Expansion**
I tested **11 models** in total, of which the strongest contenders were:
- **XGBoost** (final submission)
- **LightGBM**
- **CatBoost**
- **Random Forest**

Others like KNN and Naive Bayes were discarded after early performance checks (low AUC, slow run-times, poor generalization).

### 3. **Handling Class Imbalance**
- Explored and implemented `class_weight='balanced'` and `scale_pos_weight` in gradient boosting models.
- Helped improve minority class prediction without sacrificing too much accuracy.

### 4. **Hyperparameter Tuning**
- Manually tuned key parameters like:
  - `n_estimators`
  - `max_depth`
  - `learning_rate`
  - `scale_pos_weight`
  - `colsample_bytree`, `subsample` (for XGBoost)
- Found that a balance between model complexity and generalization led to optimal AUC scores.

### 5. **Cross-Validation**
- Used **Stratified K-Fold Cross Validation** to ensure fair evaluation due to class imbalance.
- Helped avoid overfitting and provided reliable performance metrics.

### 6. **Stacking Attempts**
- I explored stacking ensemble models to combine the strengths of CatBoost, LightGBM, and XGBoost.
- Ultimately reverted to a tuned XGBoost due to better standalone performance.

---

##  What I Learned

###  Technical Learnings
- How to evaluate models with **AUC**, **F1**, and **precision-recall tradeoffs**.
- Importance of **feature scaling**, **one-hot encoding**, and consistent preprocessing.
- Learned trade-offs in tuning hyperparameters under time constraints.
- Recognized the **limits of stacking** when base models are already optimized.

###  Strategic Learnings
- **Leaderboard Strategy**: Avoided overfitting to leaderboard by testing changes on holdout sets.
- **Iteration and Logging**: Maintained a change log for each submission to track what worked and what didn’t.
- **Efficiency**: Prioritized models that ran fast locally while offering strong predictive power.

---

## 🏁 Outcome

- **Final Model**: Tuned **XGBoost**
- **Score**: 0.95338
- **Kaggle Leaderboard Rank**: **7th**

This competition was one of the most fulfilling academic exercises I’ve done—it challenged me to apply everything from data cleaning to ensemble modeling and helped me build real intuition for how to approach machine learning problems in a structured, competitive way.
