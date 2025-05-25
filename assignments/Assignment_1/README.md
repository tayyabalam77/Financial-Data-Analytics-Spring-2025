# Assignment 1: Linear & Multiple Linear Regression


This folder contains all files related to Assignment 1, including:
- Jupyter Notebooks (.ipynb)
- Question documents
- Self-reflection
- Commentary and insights


##  Topics Covered
- Linear Regression (Salary Prediction)
- Multiple Linear Regression (Startup Profit)
- Student Performance Regression
- Interpretation of coefficients, outliers, overfitting, and train-test split
- Feature importance and impact analysis


## Submitted Files:
- [`Mohammad_Tayyab_Alam_24157_Assignment_1_Linear_Regression_Salary.ipynb`](Mohammad_Tayyab_Alam_24157_Assignment_1_Linear_Regression_Salary.ipynb)  
- [`Mohammad_Tayyab_Alam_24157_Assignment_1_MLR_Startup_Profit.ipynb`](Mohammad_Tayyab_Alam_24157_Assignment_1_MLR_Startup_Profit.ipynb)  
- [`Mohammad_Tayyab_Alam_24157_Assignment_1_Studentp_Regression_Applied.ipynb`](Mohammad_Tayyab_Alam_24157_Assignment_1_Studentp_Regression_Applied.ipynb)  
- [`Mohammad_Tayyab_Alam_24157_Assignment_1_Answers.docx`](Mohammad_Tayyab_Alam_24157_Assignment_1_Answers.docx): Detailed written answers to conceptual questions.


## Summary:
This assignment covered:
- Simple Linear Regression for salary prediction based on experience
- Multiple Linear Regression for startup profit prediction using R&D, admin, and marketing spend
- Interpretation of coefficients, role of outliers, model overfitting/underfitting
- Reflection on train-test split, model generalization, and extrapolation risks


#  Self-Reflection – Assignment 1: Linear & Multiple Linear Regression

## What I Learned

This assignment gave me hands-on experience with **Linear Regression** and **Multiple Linear Regression (MLR)**, helping me understand both theoretical concepts and practical applications of predictive modeling.

###  Linear Regression (Salary Prediction)
- **Coefficient interpretation** became intuitive as I realized that each unit increase in experience meant an average salary rise of around $5044.
- I learned how **train-test splits** are crucial to avoid overfitting, especially when the model appears to perform “too perfectly.”
- I understood the **risks of systematic bias** when predictions are consistently higher or lower, and how missing features or non-linearity might be responsible.
- The importance of checking **data distributions** and **outliers** became clear—ignoring them can lead to poor model performance and misleading results.

###  Multiple Linear Regression (Startup Profit Prediction)
- I saw the importance of **feature relevance** through the profit coefficients: R&D Spend was clearly the most impactful.
- **Correlations** provided strategic insight—only R&D had a strong relationship with profit, while Administration had nearly zero impact.
- I learned about **handling categorical variables** via encoding and saw the impact of **feature scaling** when features like Marketing Spend had large ranges.
- I applied **model evaluation techniques** like R² and understood that a drop in test accuracy might indicate overfitting.

## Skills Applied
- Data cleaning, exploratory data analysis
- Simple and multiple regression modeling using scikit-learn
- Train-test split, coefficient interpretation
- Outlier handling, feature encoding, and correlation analysis

## Takeaways
- **Not all features are valuable**—some (like Administration Spend) can be safely removed with little impact.
- **Model generalization matters more than training performance.**
- Good predictive models must balance **interpretability**, **robustness**, and **business understanding**.

This assignment strengthened my foundation in regression, enhanced my critical thinking around model design, and gave me a solid framework to approach real-world prediction problems.

---

