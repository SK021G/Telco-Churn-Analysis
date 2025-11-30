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
Despite being higher-value customers, those with Fiber Optic service showed a higher propensity to churn, indicating potential dissatisfaction with price or service quality in that specific segment.

---

## 3. Model Selection: Neural Network vs. Logistic Regression
This project explores two modeling approaches to solve the business problem.

### Approach A: Neural Network (Deep Learning)
* **Goal:** Maximize raw predictive accuracy.
* **Result:** Achieved high accuracy but acted as a "black box," offering limited visibility into *which* specific features were driving the churn.

### Approach B: Logistic Regression (Statistical Modeling) — *Selected for Final Deployment*
* **Goal:** Balance predictive power with **interpretability**.
* **Why it was chosen:** For a business stakeholder, knowing *why* a customer is leaving is as important as knowing *if* they will leave. Logistic Regression provided coefficients that quantified the impact of specific features (e.g., Fiber Optic, Contract Type).
* **Performance:** The model was tuned with `class_weights='balanced'` to prioritize **Recall** (capturing as many churners as possible) over raw accuracy. While overall accuracy settled at ~73-80%, the model successfully identifies the majority of at-risk customers, minimizing the "cost of missed opportunities."

![Confusion Matrix](images/Confusion_matrix.png)

---

## 4. Actionable Recommendations

Based on the model's coefficients and probability scores, the following recommendations are proposed:

1.  **Targeted Campaign for Contract Conversion:**
    * **Action:** Launch a campaign for month-to-month customers with 2–12 months of tenure.
    * **Offer:** A one-time "Loyalty Lock-in" discount (e.g., 15% off for 6 months) for switching to a 1-Year Contract.
    * **Business Impact:** Neutralizes the #1 driver of churn identified by the model.

2.  **Enhanced Fiber Optic Onboarding:**
    * **Action:** Implement a proactive "Service Health Check" for new Fiber Optic customers within their first 60 days.
    * **Business Impact:** Mitigates early-stage churn in this high-value but high-risk segment.

3.  **Proactive Retention using Probability Scores:**
    * **Action:** Use the model to generate a weekly "At-Risk List" of customers with a churn probability > 70%.
    * **Business Impact:** Enables the retention team to make personalized offers *before* the customer calls to cancel.

