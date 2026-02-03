# Churn-Analysis-PowerBI 📊

## Project Overview

This project is a high-fidelity **Customer Churn Analysis Dashboard** built to identify at-risk customers and quantify revenue loss. By analyzing a dataset of 7,000+ customers, I developed an interactive tool that translates raw telecom data into actionable business strategies.

## 🛠️ Tech Stack

* **Power BI:** Data visualization and dashboarding.
* **DAX (Data Analysis Expressions):** Advanced calculated measures for business logic.
* **Power Query:** Data cleaning, null handling, and feature engineering (binning).
* **Figma:** Custom UI/UX design for a "FinTech" dark-mode aesthetic.

## 📈 Key Insights

* **Contract Risk:** Identified that customers on **Month-to-Month** contracts represent the highest churn risk.
* **Revenue Impact:** Quantified the **Revenue at Risk**, enabling the business to prioritize high-value retention campaigns.
* **Tenure Correlation:** Discovered that customers in the **0-6 month tenure bin** are 3x more likely to churn, suggesting a need for better onboarding.

## 🧠 DAX Showcase

To demonstrate my technical proficiency, here is the logic used to calculate the dynamic **Churn Rate %**:

```dax
Churn Rate % = 
VAR TotalCustomers = COUNT(Data[customerID])
VAR ChurnedCustomers = CALCULATE(COUNT(Data[customerID]), Data[Churn] = "Yes")
RETURN
DIVIDE(ChurnedCustomers, TotalCustomers, 0)

Revenue at Risk = 
CALCULATE(
    SUM(Data[MonthlyCharges]), 
    Data[Churn] = "Yes"
)
```
High Risk Customers = 
CALCULATE(
    COUNT(Data[customerID]),
    Data[Contract] = "Month-to-month",
    Data[TechSupport] = "No"
)
YTD Churned Revenue = 
TOTALYTD(
    SUM(Data[MonthlyCharges]), 
    'DateTable'[Date], 
    Data[Churn] = "Yes"
)
## 📂 Project Structure

* `Telco_Churn_Data.csv`: The raw dataset used for analysis.
* `Dashboard_Background.png`: Custom UI background designed in Figma.
* `Report_Screenshots/`: A folder containing images of the final dashboard for quick viewing.

---

