Bank Loan DB – Power BI Project

📌 Overview

The **Bank Loan DB** project analyzes loan performance and customer behavior using **Power BI** connected to **SQL Server**.
The goal was to help stakeholders gain actionable insights into loan approvals, repayments, and customer profiles.

🛠 Data Preparation

* Connected Power BI to SQL Server database.
* Cleaned and transformed data in Power Query:
  * Removed null values
  * Merged related tables
  * Changed data types
  * Created custom calculated columns
    
  Built a Star Schema:

  * Fact Table : Loan details
  * Dimension Tables: Customers, Loans, Repayment History, Regions, Loan Types

📊 Dashboards

1. Summary Dashboard

Focus: Classification of **Good Loans** vs **Bad Loans**

* Visuals :

  * Slicers for quick filtering
  * Donut charts for loan distribution
  * KPI cards for:
    * Total Loan Applications
    * Total Funded Amount
    * Total Amount Received
    * Average Interest Rate
    * Average DTI
  * Category-wise breakdown tables
  * Navigation buttons for better user experience
    
* Key DAX Measures:

  ```DAX
  Good Loan Amount Received = CALCULATE([Total Amount Received], bank_loan_data[Good vs Bad Loan] = "Good Loan")

  Good Loan Applications = CALCULATE([Total Loan Applications], bank_loan_data[Good vs Bad Loan] = "Good Loan")

  Good Loan Funded Amount = CALCULATE([Total Funded Amount], bank_loan_data[Good vs Bad Loan] = "Good Loan")

  Good Loan % = DIVIDE(
      CALCULATE([Total Loan Applications], bank_loan_data[Good vs Bad Loan] = "Good Loan"),
      [Total Loan Applications]
  )
  ```


2. Overview Dashboard

Focus: Regional and trend analysis

* Visuals:
  * Shape map: Region-wise loan distribution
  * Area chart: Loan trends over time
  * Stacked bar chart: Approved vs Rejected loans
  * Treemap: Loan types
  * Slicers & KPI cards for interactive filtering
    
* Key Measures:
  * Total Loan Applications
  * Total Funded Amount
  * Total Amount Received


3. Details Dashboard

Focus: Granular loan-level insights

* Visuals:

  * Detailed table with Customer ID, Loan Amount, Status, Credit Score, and Region
  Features:

  * Row-Level Security (RLS) to restrict access by region
  * Ability to drill down into individual loan records



🔐 Security

* Implemented Row-Level Security (RLS) to limit data access based on user region.

🔄 Automation
* Scheduled automatic data refresh in Power BI Service
* Shared reports with management for real-time insights

📈 Business Impact
* Improved visibility into loan performance
* Identified factors affecting **good vs bad loans**
* Enabled better decision-making for loan approvals
* Highlighted regional performance and trends



📂 Repository Structure

```
/BankLoanDB
│── README.md
│── DataModel.png
│── Dashboard_Screenshots/
│── SQL_Scripts/
│── PowerBI_File.pbix
```
