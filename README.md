# Business Analysis of Telecom Customer Churn

## 1. Business Problem
A leading telecom company is facing a significant customer churn rate of nearly 27%, resulting in substantial revenue loss. This project performs a deep-dive analysis to identify the key drivers of churn and develops a predictive model to flag at-risk customers. The final goal is to propose a set of data-driven, actionable recommendations for a targeted customer retention strategy.

---

## 2. Exploratory Data Analysis (EDA) & Key Findings
Initial analysis of the customer data revealed several strong indicators of churn:

#### Finding 1: Month-to-Month Contracts are a Major Risk Factor
Customers on flexible month-to-month contracts are significantly more likely to churn compared to those on one or two-year contracts.

![Churn by Contract Type](images/Churn_rate_by_contract.png)

#### Finding 2: New Customers are the Most Vulnerable
The churn rate is highest among new customers (tenure < 12 months) and decreases steadily as customer loyalty builds over time.

---

## 3. Predictive Model & Business Evaluation
A neural network was built to predict the likelihood of a customer churning. While the model achieved a technical accuracy of ~80%, the business value lies in its ability to correctly identify customers who will churn (True Positives).

The model's performance allows the business to move from a reactive to a proactive retention strategy. By focusing on the customers the model flags as "at-risk," the retention team can allocate their resources more effectively.

![Confusion Matrix](images/Confusion_matrix.png)

---

## 4. Actionable Recommendations

Based on the analysis, the following recommendations are proposed:

1.  **Targeted Campaign for Contract Conversion:** Launch a marketing campaign for month-to-month customers with 2-12 months of tenure, offering a one-time discount to convert them to a more stable one-year contract.

2.  **Enhance New Customer Onboarding:** Implement a proactive support outreach program for all new customers within their first 60 days to address any early-stage issues and improve satisfaction.

3.  **Deploy the Predictive Model:** Use the trained model to generate a weekly "at-risk" customer list for the retention team, enabling them to make personalized offers before a customer decides to leave.

---

## 5. How to Use This Project
1. Clone the repository: `git clone https://github.com/YourUsername/Telco-Churn-Analysis.git`
2. Install the required libraries: `pip install -r requirements.txt`
3. Open and run the `Churn_Analysis_Report.ipynb` notebook in Jupyter.
