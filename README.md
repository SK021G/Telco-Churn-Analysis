# Business Analysis of Telecom Customer Churn

## 1. Business Problem
A leading telecom company is facing a significant customer churn rate of **27%**, resulting in substantial revenue loss. This project performs a deep-dive analysis to identify the *key drivers* of churn and develops a predictive model to flag at-risk customers.

**Goal:** Move from a reactive retention strategy to a proactive one by predicting who will leave and *why*.

---

## 2. Exploratory Data Analysis (EDA) & Key Findings
Initial analysis of the customer data revealed several strong indicators of churn:

#### Finding 1: Month-to-Month Contracts are a Major Risk Factor
Customers on flexible month-to-month contracts are significantly more likely to churn compared to those on one or two-year contracts.

![Churn by Contract Type](images/Churn_rate_by_contract.png)

#### Finding 2: New Customers are the Most Vulnerable
The churn rate is highest among new customers (tenure < 12 months). Loyalty increases significantly after the first year.

#### Finding 3: Fiber Optic Internet Users are High-Risk
Despite likely being higher-value customers, those with Fiber Optic service showed a higher propensity to churn compared to DSL users, indicating potential dissatisfaction with price or service quality in that specific segment.

---

## 3. Methodology & Model Performance
To solve this problem, I applied **Logistic Regression** (Statistical Modeling) rather than a "black box" machine learning model. This choice was strategic: for business stakeholders, understanding *why* a customer is leaving (interpretability) is just as critical as predicting *if* they will leave.

### Key Modeling Steps:
* **Data Preprocessing:** Handled categorical variables via One-Hot Encoding and scaled numerical features to ensuring accurate coefficient analysis.
* **Handling Class Imbalance:** The dataset was imbalanced (only ~27% churners). I addressed this by utilizing **balanced class weights** during model training. This prioritizes **Recall** (capturing as many churners as possible) over simple raw accuracy.

### Performance:
* **Accuracy:** ~73-80%
* **Business Value:** While a raw accuracy score might seem moderate, the model excels at identifying the *minority class* (churners). By sacrificing some precision to gain higher recall, we ensure the business doesn't miss the opportunity to save at-risk customers.
* **Interpretability:** The model successfully quantified the impact of key features. We found that **Month-to-Month contracts** and **Fiber Optic service** were the strongest positive coefficients (increasing churn risk), while **Tenure** was the strongest negative coefficient (decreasing risk).

![Confusion Matrix](images/Confusion_matrix.png)

---

## 4. Actionable Recommendations

Based on the model's coefficients and probability scores, the following recommendations are proposed:

1.  **Targeted Campaign for Contract Conversion:**
    * **Action:** Launch a campaign for month-to-month customers with 2–12 months of tenure.
    * **Offer:** A one-time "Loyalty Lock-in" discount (e.g., 15% off for 6 months) for switching to a 1-Year Contract.
    * **Business Impact:** Neutralizes the #1 driver of churn identified by the model coefficients.

2.  **Enhanced Fiber Optic Onboarding:**
    * **Action:** Implement a proactive "Service Health Check" for new Fiber Optic customers within their first 60 days.
    * **Business Impact:** Mitigates early-stage churn in this high-value but high-risk segment.

3.  **Proactive Retention using Probability Scores:**
    * **Action:** Use the model to generate a weekly "At-Risk List" of customers with a churn probability > 70%.
    * **Business Impact:** Enables the retention team to make personalized offers *before* the customer calls to cancel.

---
    ```
3.  Open and run the notebook:
    * `Churn_Analysis_Report.ipynb` contains the full EDA, Feature Importance analysis, and Business Recommendations.
