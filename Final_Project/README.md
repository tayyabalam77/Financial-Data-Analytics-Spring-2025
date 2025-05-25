# Final Project – Nova Credit Replication and CreditDekho Proposal

## Project Objective

The goal of this final project was to **replicate the machine learning pipeline behind Nova Credit**, a U.S.-based company that enables credit scoring for immigrants by using alternative data sources. Due to the absence of proprietary data from Nova Credit, we used publicly available Kaggle datasets to build a comparable scoring framework based on:

- Mobile usage behavior
- Device metadata
- Demographic profiles
- Financial indicators

After building and evaluating multiple machine learning models, we proposed a **Pakistan-specific startup concept** called **CreditDekho**, which would aim to replicate Nova Credit’s logic for local microfinance markets using demographic and mobile behavioral data. This proposal remains conceptual due to the lack of open Pakistani datasets.

---

## Project Components

| File | Description |
|------|-------------|
| `FDA_Final Project_Group 17.ipynb` | Main Jupyter notebook with all preprocessing, model training, evaluation, and insight extraction |
| `FDA_Final Project_Group 17.html` | Rendered notebook output with visuals, tables, and explanations |
| `FDA Final Presentation.pdf` | Summary of findings and proposal presentation |
| `Nova_credit_simulated_dataset_10000.csv` | Cleaned and feature-engineered training dataset (10,000 rows) |
| `nova_credit_blind_test_700.csv` | Blind test set (700 rows) used to validate generalizability |
| `Key_Findings.md` | Independent summary of insights, feature importance, top-performing models, and business implications |

---

## Data Sources and Justification

To simulate Nova Credit’s use of alternative data, we used the following three datasets:

### 1. [Give Me Some Credit Dataset (Kaggle Competition)](https://www.kaggle.com/c/GiveMeSomeCredit/data)
- Contains financial indicators such as monthly income, credit utilization, and delinquencies.
- Closely mirrors credit bureau-style data Nova Credit may use when available.
- Used to simulate the financial reliability and creditworthiness score (`SeriousDlqin2yrs`).

### 2. [Mobile Device Usage and User Behavior Dataset](https://www.kaggle.com/datasets/valakhorasani/mobile-device-usage-and-user-behavior-dataset)
- Provides metrics on app usage, screen time, and digital behavior.
- Used to simulate Nova Credit’s approach of analyzing device usage and app engagement.
- Behavioral features like `App Usage Time`, `Number of Apps`, and `Device Model` were extracted.

### 3. [US Census Demographic Data](https://www.kaggle.com/datasets/muonneutrino/us-census-demographic-data)
- Offers demographic variables including age, gender, income, and state of residence.
- Helped simulate the integration of socio-demographic attributes into the credit scoring model.

**Justification:**  
Nova Credit uses non-traditional, behavioral, and demographic data to assess the creditworthiness of people who lack credit history. Our selected datasets allowed us to replicate that logic using the best publicly available approximations.

---

## Modeling Overview

- Over 30 model-preprocessing combinations were tested.
- Algorithms used included Logistic Regression, XGBoost, CatBoost, LightGBM, and Random Forest.
- Evaluated across metrics such as LogLoss, Recall (Class 0 and 1), Precision, ROC AUC, and Accuracy.
- Imbalance techniques tested: SMOTE, undersampling, class_weight
- Outlier and missing value handling were tested using IQR filtering, median/mode replacement, and feature engineering.
- Blind test (700 rows) was used to ensure generalization of top models beyond the training set.

The best models consistently achieved:
- **LogLoss below 0.25**
- **Recall for Class 0 above 90%**
- **Overall accuracy above 95%** on the blind test.

See the `Key_Findings.md` file for detailed model comparison, strengths, and business implications.

---

## CreditDekho – Proposal for Pakistan

Following the replication of Nova Credit's concept, we developed a startup proposal for the Pakistani market:

**Startup Concept: CreditDekho**

- **Problem:** Millions of individuals in Pakistan lack formal credit history and are excluded from access to microloans and credit products.
- **Proposed Data Sources:**
  - PTA (Pakistan Telecommunication Authority): for SIM card usage, mobile behavior, app activity
  - PBS (Pakistan Bureau of Statistics): for demographic and socioeconomic data
- **Target Users:** First-time borrowers, low-income individuals, micro-entrepreneurs
- **Value Proposition:** Offer credit scores based on mobile and demographic signals, reducing reliance on traditional credit bureaus.

**Disclaimer:**  
CreditDekho is a conceptual proposal. No data from Pakistan was used. All work was conducted on U.S.-based datasets for the purpose of replication only.


