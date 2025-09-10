## Project Title
Bank Customer Churn Analysis(Interactive Dashboard creation using Advanced Excel)
## Project Description
This project analyzes customer churn for a retail bank using **Excel dashboards** enhanced with **DAX measures**. The objective is to uncover insights into churn patterns across demographics, geography, satisfaction, and financial behaviors, and to propose actionable recommendations for retention strategies.
## Project Objectives
- Identify the churn rate and retention rate of customers.
- Analyze key drivers of churn such as age, gender, geography, product usage, and satisfaction.
- Compare customer balances and tenure between churned and retained customers.
- Provide actionable insights to reduce churn.
## Dataset Used
- <a href="https://github.com/Jonathan-Analyst/Bank-Customer-Churn-Analysis-Excel-Dashboard-DAX/blob/main/bank%20churn.xlsx">Dataset</a>
## Project Process
- Data Cleaning and Preparation in Excel.
- Data Modeling with customer churn records.
- DAX Measures were created to calculate KPIs such as churn rate, retention rate, averages, and balances.
- Dashboard Design using Excel charts and slicers for interactivity.
- Insights and Interpretation of visual trends and KPI metrics.
## KPI Questions
- What percentage of customers churned vs. retained?
- Which demographic groups (age, gender, geography) have the highest churn rate?
- How does churn vary by tenure, satisfaction score, and number of products?
- Do churned customers differ in terms of balance and credit score?
- What role do customer complaints play in churn?
  ## DAX Functions
  **Core Measures**
```DAX
Total Customer = COUNTROWS('Customer_Churn_Records_26')

Churned Customers = 
CALCULATE (
    [Total Customer],
    'Customer_Churn_Records_26'[Exited] = 1
)

Retained Customers = 
CALCULATE (
    [Total Customer],
    'Customer_Churn_Records_26'[Exited] = 0
)
```
**Rates**
```DAX
Churn Rate = DIVIDE([Churned Customers], [Total Customer], 0)

Retention Rate = DIVIDE([Retained Customers], [Total Customer], 0)
```
**Customer Attributes**
```DAX
Avg Age = AVERAGE('Customer_Churn_Records_26'[Age])

Avg Tenure = AVERAGE('Customer_Churn_Records_26'[Tenure])

Avg Satisfaction = AVERAGE('Customer_Churn_Records_26'[Satisfaction Score])
```
**Balance Analysis**
```DAX
Avg Balance (Retained) = 
CALCULATE (
    AVERAGE('Customer_Churn_Records_26'[Balance]),
    'Customer_Churn_Records_26'[Exited] = 0
)

Avg Balance (Churned) = 
CALCULATE (
    AVERAGE('Customer_Churn_Records_26'[Balance]),
    'Customer_Churn_Records_26'[Exited] = 1
)
```
**Alternative Measure (if Exited = "Yes"/"No")**
```DAX
Churn Customers = 
CALCULATE (
    [Total Customer],
    'Customer_Churn_Records_26'[Exited(Customer)] = "Yes"
)




