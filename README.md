# course-progress
This repository tracks my progress and assignments in FDA Course


## Assignments
- Assignment 1 was about linear regression , multiple linear regression and prediction profit of a startup
- Assignment 2 was about predicting fraud as per shift's case study
- Assignment 3 was about HSBC K means clustering.

## Weekly Updates
- **Week 1**: Completed initial data exploration and linear regression models.
- **Week 2**: Explored more complex regression models, such as multiple linear regression.
- **Week 3**: Focused on improving model accuracy with feature engineering.
- **Week 4**: Case study discussions to understand real world implications
- **Week 5**: Assignment 1 described separately
- **Weeek 6**: Decission trees, logisitc and other models
- **Week 7** : Presentations




---

### **Assignment 1: Linear Regression Analysis**

#### **Linear Regression for Salary Prediction**

In this assignment, you worked on predicting **salary** based on **years of experience** and explored several important aspects of **linear regression**.

### **Question 1: Interpreting the Coefficient of "Years of Experience"**

The coefficient of **years of experience** in a linear regression model represents the **change in salary** for each additional year of experience. In this case, the coefficient of **5044.76** means that for every additional year of experience, the salary increases by **$5044.76**.

```python
coefficients = model.coef_
print(f"Coefficients: {coefficients}")
```
- **Interpretation**: The positive coefficient indicates a direct relationship between years of experience and salary, meaning as experience increases, salary increases as well.

### **Question 2: Importance of Checking the Distribution of Salary and Years of Experience**

Before applying regression, checking the distribution of the data helps to:
1. **Identify skewness**: Skewed data can violate linear regression assumptions.
2. **Check for outliers**: Outliers can distort the regression model.
3. **Ensure linearity**: Linear regression assumes a linear relationship between independent and dependent variables. Visualizing the distribution ensures that this assumption holds.

### **Question 3: Using All Data for Training vs. Train-Test Split**

If all the data is used for training and none for testing, the model may **overfit** the training data, meaning it will perform well on the training set but poorly on unseen data. Using a **train-test split** allows the model to be evaluated on **unseen data**, providing a more accurate measure of its performance.

```python
X = df[['Years Experience']]
y = df['Salary']

# Scenario 1: Train-Test Split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model_split = LinearRegression().fit(X_train, y_train)
train_score_split = model_split.score(X_train, y_train)
test_score_split = model_split.score(X_test, y_test)
```
- The model trained on **100% of the data** (without splitting) gave a higher **R²** value, but this is misleading because it doesn't evaluate how well the model generalizes.

### **Question 4: Impact of Predicted Salaries Being Consistently Higher or Lower**

If the model’s predicted salaries are consistently lower or higher than actual salaries, it suggests **systematic bias**. This could be due to:
- Missing important features
- Using an incorrect functional form (e.g., assuming linearity when the relationship might be non-linear)
- Overfitting (if the model fits the training data too closely)

### **Question 5: Impact of Changing the Training Dataset Size**

Increasing the training dataset generally improves the model’s **generalizability**. It helps the model learn better patterns and reduces the risk of **overfitting**. Conversely, reducing the dataset size increases the risk of overfitting, where the model learns the noise in the data rather than actual patterns.

### **Question 6: Impact of Adding "Certifications" to the Model**

Adding a relevant feature, such as **certifications**, can improve the model’s **predictive power** if it significantly influences the salary. This would help the model explain more of the variation in salaries, making it more accurate.

### **Question 7: Effect of Outliers on the Model**

Outliers, such as a person with **50 years of experience** but a very low salary, can distort the regression line, leading to **biased predictions**. To handle this, robust regression techniques or outlier handling methods like **winsorization** can be applied.

### **Question 8: Problems with Small Dataset Size**

If the dataset contains a small number of observations, it may lead to:
1. **High variance** in model estimates.
2. **Unreliable coefficient estimates**.
3. **Overfitting**: The model might memorize the small dataset rather than learning general patterns.

### **Question 9: The Role of `LinearRegression().fit()`**

The `LinearRegression().fit()` function trains the model by calculating the **optimal coefficients** (i.e., the best-fit line) that minimize the **sum of squared errors** between the observed and predicted values.

### **Question 10: Effect of High Outliers on the Model**

Outliers, such as a **CEO** with 40 years of experience earning $1 million, can pull the regression line upwards, **skewing predictions** for lower-experience employees. This can be mitigated by using transformations like **log-salaries** or using **robust regression** methods.

### **Question 11: Predicting Salary for Interns (0 Years Experience)**

This model may not be reliable for predicting salaries for **interns (0 years of experience)**, as it was trained on data where all employees have some experience. Extrapolating to zero years of experience might lead to inaccurate predictions due to a possible non-linear relationship at the lower end.

To improve this, a separate dataset for **interns** could be used to predict their salaries more accurately.

---

### **MLR Startup Profit Analysis**

This section focused on **Multiple Linear Regression (MLR)** to predict the **profit** of a startup based on the **R&D Spend**, **Administration Spend**, and **Marketing Spend**.

#### **Question 1: Interpreting Coefficients and Impact on Investment**

The model shows the **coefficients** for each feature, which tell us how much each expenditure affects the profit:
- **R&D Spend**: Each dollar spent on R&D increases profit by **$0.84**.
- **Administration Spend**: Each dollar spent increases profit by **$0.02**.
- **Marketing Spend**: Each dollar spent increases profit by **$0.01**.

The company should focus more on **R&D** as it has the highest coefficient, contributing more to profit.

```python
coefficients = pd.DataFrame(model.coef_, X.columns, columns=['Coefficient'])
print(coefficients)
```

#### **Question 2: Mean and Standard Deviation of R&D Spend**

The **mean** of **R&D Spend** is **70,543.76**, indicating the average amount startups invest in R&D. The **standard deviation** of **43,042.35** shows that there's a significant variation in how much startups invest in R&D.

#### **Question 3: Impact of Large Range in Marketing Spend**

A large range in **Marketing Spend** can lead to **scaling issues** because features with larger ranges may dominate the model. **Normalization** or **standardization** can help mitigate these issues and improve model performance.

#### **Question 4: Handling Categorical Features (e.g., Startup Industry)**

If categorical features like **Startup Industry** were added to the dataset, they could be encoded using:
- **One-hot encoding**: This creates binary columns for each category.
- **Label encoding**: This assigns each category a unique integer, but it might introduce unwanted ordinal relationships.

#### **Question 5: Correlation Matrix and Profit**

The **correlation matrix** shows:
- **R&D Spend** has the strongest positive correlation with **Profit (0.87)**.
- **Marketing Spend** has a weaker positive correlation with **Profit (0.37)**.
- **Administration Spend** has almost no impact on profit (**0.005 correlation**).

#### **Question 6: Using `train_test_split()`**

The **`train_test_split()`** function ensures that the model is trained on one subset of the data and tested on another, which helps in evaluating the model’s performance on unseen data. The default split ratio is **80% training** and **20% testing**.

#### **Question 7: Removing Administration Spending**

Removing **Administration Spending** (which has almost zero correlation with profit) had a minimal impact on the model’s **R²** value. This suggests that **Administration Spend** does not significantly contribute to predicting **Profit**.

#### **Question 8: Test Accuracy Lower than Training Accuracy**

If the **test accuracy** is much lower than the **training accuracy**, it indicates **overfitting**. The model performs well on the training data but poorly on unseen data. To address this, techniques like **regularization** (Ridge/Lasso) and **feature selection** can help.

#### **Question 9: Predicting Profit with Zero Marketing Spend**

If a startup has **zero Marketing Spend** but high **R&D** and **Administration Spend**, the model will likely still make reasonable predictions since **Marketing Spend** has a moderate impact on **Profit**. However, if **Marketing Spend** is essential in the industry, the model might struggle to make accurate predictions.

#### **Question 10: Maximizing Profit with R&D or Marketing Spend**

To maximize profit, the company should focus on increasing **R&D spending**, as it has the highest positive impact on profit (with a coefficient of **0.84** and a correlation of **0.87**).

#### **Question 11: Using the Model for a Different Country**

This model may not be reliable for predicting the profit of a startup in a different country due to variations in economic conditions, cost structures, and market conditions. To improve accuracy, the model would need to be retrained with data from the target country.

#### **Question 12: Additional Variables for Better Predictions**

To improve predictions, the following additional variables could be included:
- **Geographic location** (country, city)
- **Industry sector** (e.g., tech, healthcare)
- **Company size** (number of employees)
- **Economic indicators** (e.g., GDP, inflation)

---

### **Conclusion**

This assignment provided valuable insights into **Linear Regression** and **Multiple Linear Regression (MLR)** for predicting salary and startup profit. By analyzing the **coefficients**, **correlations**, and the impact of different features, we were able to optimize the models and suggest improvements in feature selection, regularization, and data handling techniques.











---

### **Assignment 2: Logistic Regression Model for Fraudulent Insurance Claims**

#### **Objective:**
The objective of this assignment was to build a **logistic regression model** to classify fraudulent (1) and non-fraudulent (0) insurance claims. We aimed to evaluate the model’s performance using different techniques for handling class imbalance, model evaluation metrics, and feature engineering.

#### **Steps Taken:**

1. **Data Preprocessing and Exploratory Data Analysis (EDA):**
   - **Data Loading**: The dataset was loaded, and basic statistics were computed. This revealed no missing values, which streamlined preprocessing.
   - **Exploratory Data Analysis**: 
     - **Statistical Summary**: Insights were gained into columns like **PolicyholderAge**, **ClaimAmount**, and **Fraud** distribution.
     - **Class Imbalance**: The **Fraud** class had a significant imbalance with only 1% fraudulent claims, emphasizing the need for methods to address this issue.
     - **Visualization**: Class distribution was plotted, and box plots helped identify outliers in numerical features like **ClaimAmount** and **LossHour**. 
     - **Correlation Heatmap**: A heatmap was generated to visualize correlations between variables, aiding in feature selection.
     - **Feature Engineering**: Multiple features were created based on insights such as **ClaimAgeRatio** (policyholder age to vehicle age) and **ClaimAmountPerPolicy** to help improve the model’s predictive power.

2. **Handling Class Imbalance:**
   - **Class Imbalance Issue**: A severe imbalance was identified, with 99% of claims being non-fraudulent. This was addressed using techniques such as:
     - **SMOTE (Synthetic Minority Over-sampling Technique)** to create synthetic fraudulent samples and balance the dataset.
     - **Undersampling**: Reducing the number of non-fraudulent samples to match the number of fraudulent claims.
     - **Cost-sensitive Learning**: Adjusting the class weights in the logistic regression model to penalize misclassifying fraud cases more heavily.

3. **Model Training:**
   - **Logistic Regression**: A basic logistic regression model was trained on the data without addressing class imbalance, serving as a control model.
   - **Stratified Train-Test Split**: Ensured that both the training and testing datasets maintained the same class distribution using a 70:30 split.

4. **Model Evaluation:**
   - The model’s performance was evaluated using several key metrics:
     - **Accuracy**: General performance measure, although not suitable for imbalanced data.
     - **Precision and Recall**: Precision evaluates the correctness of predicted fraud cases, and recall measures the model’s ability to identify fraud cases.
     - **F1-Score**: A balance between precision and recall, especially important for class-imbalanced datasets.
     - **AUC-ROC**: Measures the model's ability to distinguish between classes.
     - **Confusion Matrix**: Analyzed false positives (FP) and false negatives (FN) for understanding model performance.

5. **Model Performance Without Class Imbalance Handling:**
   - The model without any class imbalance handling showed an **accuracy** of 99%, but failed to identify fraud cases, as evident from the confusion matrix where all fraudulent claims were misclassified as non-fraudulent.

6. **Model Performance with SMOTE:**
   - **SMOTE** improved recall, indicating better fraud detection, but the model still struggled with **false positives**, as it predicted a lot of non-fraud cases as fraudulent.
   - Evaluation metrics showed improvement in recall but a drop in precision, making it a better option for fraud detection but needing further refinement.

7. **Model Performance with Undersampling:**
   - **Automatic Undersampling** was applied to balance the classes. This method improved recall but at the expense of accuracy and increased false positives, indicating the trade-off between false negatives and false positives when dealing with imbalanced data.

8. **Model Performance with Cost-Sensitive Learning:**
   - The **cost-sensitive model** adjusted the misclassification penalties, which reduced false positives while maintaining recall, leading to a more balanced model.

9. **Manual Undersampling and Feature Engineering**:
   - **Manual Undersampling** was performed by balancing the dataset using fraud cases and non-fraud cases to match the number of fraud cases, followed by model training.
   - **Feature Engineering** improved the model’s performance by adding more informative features that helped the model better distinguish between fraudulent and non-fraudulent claims.

10. **Final Model Selection and Evaluation**:
    - The **final selected model** used **manual undersampling** and **feature engineering**. It achieved the best performance in terms of **recall (67%)** and **F1-Score (2.5%)**. Although the accuracy was low, the recall was prioritized for fraud detection.
    - The model was further improved with **L1 regularization** (Lasso), which helped eliminate irrelevant features and slightly improved the **AUC** score.

11. **Threshold Adjustment**:
    - Multiple threshold adjustment techniques were explored to improve **recall** and **precision** while minimizing false positives. This involved varying the threshold to maximize the F1-score and recall, depending on the business requirement to either reduce false negatives or false positives.

---

#### **Insights and Recommendations**:
- **Class Imbalance**: Handling class imbalance was crucial to improving fraud detection. Without techniques like SMOTE or undersampling, the model performed poorly on fraud cases.
- **Feature Engineering**: Creating new features based on domain knowledge was vital to improving the model’s predictive power, especially for detecting fraud in an imbalanced dataset.
- **Model Evaluation**: Metrics like **recall** and **F1-Score** were prioritized due to the importance of detecting fraudulent claims accurately.
- **Future Improvements**: 
  - More advanced models like **XGBoost** or **CatBoost** could improve detection further, as they are more robust in handling imbalanced datasets.
  - **Anomaly detection** techniques might be helpful in detecting rare fraud cases, as fraud is a rare event in this dataset.
  - Further **parameter tuning** for methods like SMOTE and undersampling could help fine-tune model performance.

---

This detailed explanation covers all the essential parts of your **Assignment 2**, which demonstrates your approach to solving the fraud detection problem using **logistic regression** with class imbalance handling, **model evaluation**, and **feature engineering**.







---

### **Assignment 3: Customer Segmentation using K-Means Clustering**

#### **Question 1: Feature Creation and Model Evaluation**
In this assignment, several **new features** were developed to capture more detailed customer behaviors and improve the segmentation accuracy. The features created include:

- **D2I (Debt-to-Income Ratio)**: This feature measures a customer's financial leverage by dividing their **Total Relationship Balance (TRB)** by their **Income**. A high D2I indicates a higher reliance on debt relative to income.
  
- **DIG_ENG_SCORE (Digital Engagement Score)**: This score was created by summing the activities a customer engages in, such as **DIG_ACTIVE** (digital activity), **FX_TRANS** (foreign exchange transactions), and **PAYME** (payments). This feature quantifies a customer's engagement with digital services.

- **TECH_SAVVY**: This feature flags customers who actively use multiple digital services, indicating their comfort with technology.

- **HNWI (High-Net-Worth Individual)**: This flag is set for customers who are high-net-worth individuals, based on their usage of **premium products**, such as **mortgages** and **bonds**.

- **Age Categories**: Customers were grouped into different age categories, recognizing that **age** correlates with different spending and saving habits. For instance, younger customers (in their 20s) might have lower savings but could be highly engaged in digital financial activities.

By adding these features, the model's performance significantly improved. Initially, the **silhouette score** (a measure of clustering quality) was **0.178** without the features, indicating poorly defined clusters. After incorporating the new features, the silhouette score improved to **0.686** at **K=5**, showing better-defined clusters and more accurate customer segmentation.

#### **Question 2: How Customer Segmentation Helps HSBC's Customer Life Cycle Management (CLCM)**
Using **K-Means clustering**, HSBC can refine its **Customer Life Cycle Management (CLCM)** strategy by segmenting customers into distinct groups based on their financial behaviors and engagement. The following clusters were identified:

- **Cluster 0: Students (Acquisition Phase)**
  - **Income**: 25,184 (Low)
  - **TRB**: 68,380 (Moderate)
  - **D2I**: 6.68 (High debt-to-income ratio)
  - **DIG_ENG_SCORE**: 1.51 (Moderate engagement)
  - **Strategy**: HSBC can target this group with **affordable loans** and **digital banking products**. In-person engagement can help activate these customers and increase their digital engagement.

- **Cluster 1: Affluent Professionals (Relationship Deepening Phase)**
  - **Income**: 33,282 (High)
  - **TRB**: 212,943 (High)
  - **D2I**: 8.39 (High debt-to-income ratio)
  - **DIG_ENG_SCORE**: 1.46 (Moderate engagement)
  - **Strategy**: HSBC should offer **financial planning** and **investment advice** to help these customers manage risk and deepen their relationship.

- **Cluster 2: Mid-Level Professionals (Relationship Deepening Phase)**
  - **Income**: 29,998 (Mid)
  - **TRB**: 153,498 (Moderate)
  - **D2I**: 5.40 (Moderate debt-to-income ratio)
  - **DIG_ENG_SCORE**: 1.51 (Moderate engagement)
  - **Strategy**: HSBC should introduce **mobile-first banking** services to cater to this group, enhancing engagement through digital platforms while offering in-person assistance to overcome lower digital engagement.

- **Cluster 3: Financially Stable Professionals (Relationship Deepening Phase)**
  - **Income**: 39,799 (Higher income)
  - **TRB**: 177,477 (Moderate)
  - **D2I**: 4.56 (Low debt-to-income ratio)
  - **DIG_ENG_SCORE**: 2.00 (High engagement)
  - **Strategy**: Offer **private equity investments** and **digital wealth management** services, providing more opportunities for these financially stable individuals to grow their wealth.

- **Cluster 4: High Income, High Debt, Very High Digital Engagement (Relationship Deepening Phase)**
  - **Income**: 38,809 (High income)
  - **TRB**: 225,590 (High)
  - **D2I**: 8.39 (High debt-to-income ratio)
  - **DIG_ENG_SCORE**: 3.00 (Very high engagement)
  - **Strategy**: This group requires **wealth management** services via **robo-advisors** and **app-based support**, helping them manage their finances more effectively through high-tech solutions.

The segmentation provided detailed customer profiles that HSBC can use to tailor their products and services at various stages of the customer life cycle, from acquisition to retention.

#### **Question 3: Key Differences Between Top-Down and Bottom-Up Market Segmentation**
- **Top-Down Segmentation**: This traditional segmentation approach uses **predefined categories** such as age groups, income levels, and geographic regions. For instance, you might create segments like **Young_Low_HK** (young, low income, domestic transactions) or **MidCareer_Low_HK** (mid-career, low income, moderate transaction behavior). While useful for broad categorizations, top-down segmentation lacks granularity in capturing customer behaviors.

- **Bottom-Up Segmentation**: This approach takes a **data-driven** path, focusing on customer **behaviors** and interactions. Features like **D2I**, **digital engagement**, and **tech-savviness** provide more detailed insights into customer habits. For example, **Cluster 4** represents high-net-worth individuals with high debt and high digital engagement, which top-down segmentation wouldn’t capture. This bottom-up approach leads to more precise customer profiles, especially for targeting specific financial behaviors like **digital engagement**.

In essence, top-down segmentation provides broad strokes, while bottom-up segmentation captures deeper, more actionable insights into customer behavior.

#### **Question 4: Application in Pakistani Financial Institutions**
In Pakistan, the median age is 20.6 years, and a large proportion of the population is **Gen-Z** and **Millennials**. These demographics align closely with the **customer profiles** identified in the case study. Here's how the findings could be applied in **UBL Bank**:

- **Young Customers**: The case study highlights the importance of **digital engagement** in the younger population, which is a significant part of Pakistan’s demographic. By creating features like **Debt-to-Income ratios**, **Digital Engagement Scores**, and identifying **HNWI customers**, UBL Bank can improve its customer segmentation and tailor offerings more effectively.

- **Digital Banking**: Offering digital banking products, such as **UBL Mobile Banking** for students or young professionals, would engage this tech-savvy generation. **Mobile-first services** should be a priority, especially since this group prefers digital solutions over traditional banking methods.

- **Personalized Wealth Management for HNWIs**: The case study shows that **HNWI** customers, especially those who are highly engaged digitally, need more personalized financial solutions. UBL Bank can create tailored wealth management services, offering these customers access to **investment products** and **digital tools** like robo-advisors.

By using **K-Means clustering** and behavioral feature engineering, UBL Bank can move away from **traditional segmentation models** and focus on delivering **personalized experiences** for **young, digitally active** customers while catering to **affluent clients** with premium financial products.

---

### **Conclusion**
In this assignment, the application of **K-Means clustering** provided valuable insights into customer segmentation. By creating **behavioral features** such as **Debt-to-Income ratios**, **digital engagement scores**, and identifying **high-net-worth individuals**, the segmentation became more detailed and accurate. This approach can be directly applied to enhance **customer life cycle management** strategies in **HSBC** and **UBL Bank**, enabling more personalized services and targeted marketing strategies.


By using K-Means clustering and behavioral feature engineering, UBL Bank can move away from traditional segmentation models and focus on delivering personalized experiences for young, digitally active customers while catering to affluent clients with premium financial products.

