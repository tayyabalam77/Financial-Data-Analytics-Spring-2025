Assignment 2: Logistic Regression Model for Fraudulent Insurance Claims
Objective:
The objective of this assignment was to build a logistic regression model to classify fraudulent (1) and non-fraudulent (0) insurance claims. We aimed to evaluate the model’s performance using different techniques for handling class imbalance, model evaluation metrics, and feature engineering.

Steps Taken:
Data Preprocessing and Exploratory Data Analysis (EDA):

Data Loading: The dataset was loaded, and basic statistics were computed. This revealed no missing values, which streamlined preprocessing.

Exploratory Data Analysis:

Statistical Summary: Insights were gained into columns like PolicyholderAge, ClaimAmount, and Fraud distribution.

Class Imbalance: The Fraud class had a significant imbalance with only 1% fraudulent claims, emphasizing the need for methods to address this issue.

Visualization: Class distribution was plotted, and box plots helped identify outliers in numerical features like ClaimAmount and LossHour.

Correlation Heatmap: A heatmap was generated to visualize correlations between variables, aiding in feature selection.

Feature Engineering: Multiple features were created based on insights such as ClaimAgeRatio (policyholder age to vehicle age) and ClaimAmountPerPolicy to help improve the model’s predictive power.

Handling Class Imbalance:

Class Imbalance Issue: A severe imbalance was identified, with 99% of claims being non-fraudulent. This was addressed using techniques such as:

SMOTE (Synthetic Minority Over-sampling Technique) to create synthetic fraudulent samples and balance the dataset.

Undersampling: Reducing the number of non-fraudulent samples to match the number of fraudulent claims.

Cost-sensitive Learning: Adjusting the class weights in the logistic regression model to penalize misclassifying fraud cases more heavily.

Model Training:

Logistic Regression: A basic logistic regression model was trained on the data without addressing class imbalance, serving as a control model.

Stratified Train-Test Split: Ensured that both the training and testing datasets maintained the same class distribution using a 70:30 split.

Model Evaluation:

The model’s performance was evaluated using several key metrics:

Accuracy: General performance measure, although not suitable for imbalanced data.

Precision and Recall: Precision evaluates the correctness of predicted fraud cases, and recall measures the model’s ability to identify fraud cases.

F1-Score: A balance between precision and recall, especially important for class-imbalanced datasets.

AUC-ROC: Measures the model's ability to distinguish between classes.

Confusion Matrix: Analyzed false positives (FP) and false negatives (FN) for understanding model performance.

Model Performance Without Class Imbalance Handling:

The model without any class imbalance handling showed an accuracy of 99%, but failed to identify fraud cases, as evident from the confusion matrix where all fraudulent claims were misclassified as non-fraudulent.

Model Performance with SMOTE:

SMOTE improved recall, indicating better fraud detection, but the model still struggled with false positives, as it predicted a lot of non-fraud cases as fraudulent.

Evaluation metrics showed improvement in recall but a drop in precision, making it a better option for fraud detection but needing further refinement.

Model Performance with Undersampling:

Automatic Undersampling was applied to balance the classes. This method improved recall but at the expense of accuracy and increased false positives, indicating the trade-off between false negatives and false positives when dealing with imbalanced data.

Model Performance with Cost-Sensitive Learning:

The cost-sensitive model adjusted the misclassification penalties, which reduced false positives while maintaining recall, leading to a more balanced model.

Manual Undersampling and Feature Engineering:

Manual Undersampling was performed by balancing the dataset using fraud cases and non-fraud cases to match the number of fraud cases, followed by model training.

Feature Engineering improved the model’s performance by adding more informative features that helped the model better distinguish between fraudulent and non-fraudulent claims.

Final Model Selection and Evaluation:

The final selected model used manual undersampling and feature engineering. It achieved the best performance in terms of recall (67%) and F1-Score (2.5%). Although the accuracy was low, the recall was prioritized for fraud detection.

The model was further improved with L1 regularization (Lasso), which helped eliminate irrelevant features and slightly improved the AUC score.

Threshold Adjustment:

Multiple threshold adjustment techniques were explored to improve recall and precision while minimizing false positives. This involved varying the threshold to maximize the F1-score and recall, depending on the business requirement to either reduce false negatives or false positives.

Insights and Recommendations:
Class Imbalance: Handling class imbalance was crucial to improving fraud detection. Without techniques like SMOTE or undersampling, the model performed poorly on fraud cases.

Feature Engineering: Creating new features based on domain knowledge was vital to improving the model’s predictive power, especially for detecting fraud in an imbalanced dataset.

Model Evaluation: Metrics like recall and F1-Score were prioritized due to the importance of detecting fraudulent claims accurately.

Future Improvements:

More advanced models like XGBoost or CatBoost could improve detection further, as they are more robust in handling imbalanced datasets.

Anomaly detection techniques might be helpful in detecting rare fraud cases, as fraud is a rare event in this dataset.

Further parameter tuning for methods like SMOTE and undersampling could help fine-tune model performance.
