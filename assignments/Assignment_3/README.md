# Assignment 3: Customer Segmentation using K-Means Clustering

**Name:** Mohammad Tayyab Alam  
**ERP:** 24157  
**Course:** Financial Data Analytics – Spring 2025  

---

##  Objective

This assignment aimed to use K-Means clustering for customer segmentation, supported by behavioral feature engineering, to improve HSBC’s Customer Life Cycle Management (CLCM) strategy. The approach was extended to a Pakistani context using UBL Bank.

---

##  Question 1: Feature Creation & Model Evaluation

Several new features were created:

- **D2I (Debt-to-Income Ratio):** TRB / Income — flags financial stress.
- **DIG_ENG_SCORE (Digital Engagement Score):** Sum of digital actions (e.g., PAYME, FX transactions).
- **TECH_SAVVY:** Boolean flag for multi-service digital users.
- **HNWI (High-Net-Worth Individual):** Flags premium product usage.
- **Age Categories:** Buckets to capture life stage and digital comfort.

 **Model Result**  
- **Silhouette Score without features:** 0.178  
- **Silhouette Score with features (K=5):** 0.686  

---

##  Question 2: Clustering Results & CLCM Strategy

| Cluster | Description                                | Strategy                                                                 |
|---------|--------------------------------------------|--------------------------------------------------------------------------|
| 0       | Students (Low income, high D2I)            | Promote low-cost loans, digital activation drives                        |
| 1       | Affluent Professionals (High income/D2I)   | Offer financial advisory and investments                                 |
| 2       | Mid-Level Professionals                    | Introduce mobile-first banking with hybrid support                       |
| 3       | Financially Stable (Low D2I, High Digital) | Private equity access, wealth management                                 |
| 4       | High Earners with High Digital Use         | Robo-advisors, automation, budgeting tools                               |

---

##  Question 3: Top-Down vs. Bottom-Up Segmentation

| Top-Down                  | Bottom-Up                      |
|---------------------------|--------------------------------|
| Age, Income, Geography    | D2I, Digital Score, HNWI       |
| Broad and interpretable   | Granular and behavior-driven   |
| Easy to implement         | Better predictive power        |

 Bottom-up segmentation helped detect hidden behavioral groups, such as tech-savvy high-debt HNWIs — which top-down models would overlook.

---

##  Question 4: Application in Pakistan (UBL Bank)

- **Gen Z & Millennials:** Median age is 20.6. Aligns with Cluster 0.
- **Digital Strategy:** UBL should promote mobile-first banking with gamified features.
- **HNWIs:** Provide digital tools (e.g., robo-advisors) for personalized wealth growth.
- **Result:** Enhanced personalization for customer acquisition and retention.

---

##  Files Included

- [`Assignment3_KMeans_Clustering.ipynb`](https://github.com/your-username/your-repo/blob/main/Assignment3_KMeans_Clustering.ipynb): Complete Jupyter Notebook with feature engineering, clustering, and evaluation.

 **Citation:**  
*Choi, J.N., Kwon, O., & Fernandez, J. (2024). HSBC: Leveraging Data Analytics and AI to Enhance Customer Life Cycle Management (ST138). HKUST Business School, Thompson Center for Business Case Studies.*

**Note**: The case study and the data set file can be obtained from the HBS case study cited above. It has not been shared due to copyright.
---

##  Conclusion

K-Means clustering combined with behavioral features such as D2I and digital scores allowed for deeper and more actionable segmentation than traditional methods. These clusters can guide personalized strategies for different stages of a customer’s life cycle — both at HSBC and in Pakistan’s UBL Bank.

---

##  My Learnings

This assignment taught me how:
- **Feature engineering** can drastically improve unsupervised models.
- **Silhouette scores** and **cluster interpretability** are crucial in validating segmentation.
- **Top-down methods** lack the behavioral nuance needed in modern banking.
- **Data-driven segmentation** supports more tailored financial strategies.

Working with the HSBC case helped me bridge real-world finance with analytical modeling, reinforcing how banks like HSBC or UBL can use AI and clustering to transform customer relationships in emerging markets.

---
