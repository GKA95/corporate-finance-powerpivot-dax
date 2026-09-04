# 📊 Corporate Finance Performance & Profitability Dashboard

### Author: Gideon Kwesi Ansah
### Role: Data Analyst
### Project Status: Completed

### Dashboard Preview 

<img width="1664" height="709" alt="Screenshot 2026-09-04 121438" src="https://github.com/user-attachments/assets/cba87749-fc7e-4109-9c69-a54c5e05406b" />

## 📌 Executive Summary
An end-to-end financial analytics project evaluating company performance across **25,000+ transactions**. This dashboard provides leadership with real-time visibility into revenue streams, departmental cost structures, monthly profitability trends, and budget thresholds.

- **Total Revenue:** ~$15.81M
- **Total Expenses:** ~$7.93M
- **Net Profit:** ~$7.88M (~49.8% Net Margin)
- **Data Scope:** 25,000 line items across 4 quarters and 5 departments (Finance, HR, IT, Marketing, Operations)

---

## 🛠️ Tools & Technologies Used
- **Data Analysis & Modeling:** Microsoft Excel, Google Sheets, Power Pivot (Data Model & DAX Measures)
- **ETL & Data Cleaning:** Power Query (type casting, transaction sign standardization, date parsing)
- **Data Visualization:** KPI Scorecards, Dynamic Donut Charts, Dual-Axis Horizontal Bar Breakdown, Monthly Run-Rate Trendlines

---

## 🧠 Data Architecture & Power Pivot Modeling
Rather than relying on basic standard pivot tables and calculated fields, I built an analytical data model using **Power Pivot** to handle complex aggregations across 25k records efficiently.

### Key DAX Measures Created:
```dax
-- Total Revenue
Total Revenue := 
CALCULATE(
    SUM(data[Amount]), 
    data[Transaction Type] = "Revenue"
)

-- Total Expense
Total Expense := 
CALCULATE(
    SUM(data[Amount]), 
    data[Transaction Type] = "Expense"
)

-- Net Profit / Loss
Net Profit := [Total Revenue] - [Total Expense]

-- Profit Margin %
Profit Margin % := 
DIVIDE([Net Profit], [Total Revenue], 0)

-- Maximum Departmental / Category Spend
Max Expense := 
MAXX(
    VALUES(data[Department]), 
    [Total Expense]
)

-- Maximum Revenue Peak
Max Revenue := 
MAXX(
    VALUES(data[Category]), 
    [Total Revenue]
)
