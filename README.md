# 📊 Insurance Analytics Dashboard

> Transforming Insurance Data into Actionable Business Insights

An end-to-end analytics solution that consolidates fragmented insurance business data into interactive, real-time dashboards — enabling branch performance monitoring, policy analytics, and data-driven decision-making across Power BI, Tableau, and Excel.

---

## 🎯 Project Overview

Insurance branch and policy data was spread across multiple disconnected sources — Excel sheets, CRM systems, and transaction logs — making it difficult for leadership to track performance, monitor targets, and identify growth opportunities in real time.

This project addresses that gap by building a centralized, interactive analytics solution covering:

- **Branch Performance & Sales Dashboard** — tracks revenue, targets, opportunities, and account executive performance across New, Cross-Sell, and Renewal business
- **Insurance Policy Dashboard** — tracks policy distribution, claims, premiums, and customer demographics

---

## ❓ Problem Statement

The organization lacked a unified view to track and compare branch-level performance in real time. Key challenges included:

- Fragmented data across Excel sheets and CRM systems
- No clear alignment between individual targets and actual achievements
- Inability to track meetings, opportunities, and win ratios at a granular level
- Limited visibility into branch-level and individual-level KPIs (invoice count, opportunity stage, conversion ratio)
- Difficulty identifying top performers and lagging opportunities for coaching
- Delayed reporting and misaligned goals, resulting in lost performance improvement opportunities

**Goal:** Build an interactive dashboard solution using Power BI, Tableau, and Excel to centralize data, automate performance tracking, and provide real-time decision support — driving accountability and growth across branches.

---

## 🛠 Tech Stack

| Layer | Tools |
|-------|-------|
| Data Source | Excel (7 business datasets) |
| Database | MySQL (normalized schema) |
| Data Prep | Excel, Power Query |
| Analytics | SQL, DAX |
| Visualization | Power BI, Tableau, Excel |

---

## 📂 Datasets

The solution integrates **7 business datasets**:

| Dataset | Purpose | Business Value |
|---------|---------|-----------------|
| Brokerage | Policy information | Customer tracking |
| Fees | Revenue data | Profit analysis |
| Individual Budget | Targets | Performance monitoring |
| Invoice | Transactions | Revenue tracking |
| Meeting | Customer engagements | Conversion analysis |
| Opportunity | Sales pipeline | Growth analysis |
| Policy | Policy details | Retention analysis |

---

## 🏗️ Data Pipeline
### Data Preparation Process
1. **Data Validation** — checked data types and consistency
2. **Duplicate Check** — removed duplicate records
3. **Missing Value Analysis** — handled missing values and outliers
4. **Relationship Verification** — validated table relationships and integrity
5. **KPI Calculation** — created calculated fields and KPI measures

---

## 📊 Dashboards

### Power BI

**Branch Dashboard**
- Revenue achievement %, total target, invoice sales (KPI cards)
- Account executive performance scorecard
- Revenue breakdown by New / Cross-Sell / Renewal
- Opportunity pipeline by stage
- Top open opportunities (drill-down)

**Policy Dashboard**
- Total policies, customers, claim amount (summary cards)
- Policy distribution by age bucket, gender, policy type
- Premium growth rate (YoY)
- Claims and payment status breakdown
- Policies expiring this year

### Tableau

**Branch Performance Dashboard**
- Target vs. revenue vs. achievement %
- Cross-sell / new / renewal pie charts
- Brokerage vs. fees comparison
- Sales stage funnel
- Deep-dive: product group, income class, sales rep performance

**Insurance Policy Dashboard**
- Claim status and payment status analysis
- Gender-wise and age-bucket-wise policy distribution
- Premium growth trend by month
- Policy expiration forecast (12-month view)

### Excel

**Branch Dashboard**
- Pivot-table-driven KPI summary
- Executive-level performance breakdown
- Stage funnel by revenue
- Meeting and invoice counts by account executive

**Policy Dashboard**
- Policy and customer summary metrics
- Premium trends by year
- Claims status and lapsed policy tracking
- Risk type distribution

---

## 📈 KPI Framework

### Financial KPIs
- Total Revenue
- Total Target
- Achievement Percentage
- Invoice Sales

### Sales KPIs
- New Business Revenue
- Cross-Sell Revenue
- Renewal Revenue
- Open / Closed Opportunities

### Activity KPIs
- Meeting Count (overall and by Account Executive)
- Invoice Count

### Pipeline KPIs
- Conversion Ratio
- Stage Funnel by Revenue
- Top Opportunities by Revenue

### Policy KPIs
- Total Policies & Customers
- Age Bucket Distribution
- Premium Growth Rate (YoY)
- Claim Status & Payment Status Distribution
- Policies Expiring This Year

---

## 💻 SQL Highlights

20+ optimized SQL queries power the KPI layer. Example:

```sql
-- Conversion Ratio
SELECT
    CONCAT(
        ROUND(
            ((SELECT COUNT(stage) FROM opportunity
              WHERE stage NOT IN ("Qualify Opportunity", "Propose Solution"))
             / (SELECT COUNT(stage) FROM opportunity)) * 100, 2),
        "%") AS Conversion_Ratio;
```

```sql
-- Premium Growth Rate (YoY)
SELECT
    Year,
    premium_amount,
    ROUND(LAG(premium_amount, 1) OVER (ORDER BY Year), 2) AS Py_PA,
    CONCAT(
        ROUND(((premium_amount - LAG(premium_amount,1) OVER (ORDER BY Year))
               / LAG(premium_amount,1) OVER (ORDER BY Year)) * 100, 2),
        '%') AS Growth_Rate
FROM (
    SELECT YEAR(`Policy Start Date`) AS Year,
           ROUND(SUM(`Premium Amount`), 2) AS premium_amount
    FROM policy_details
    GROUP BY YEAR(`Policy Start Date`)
) t1;
```

Full query set available in [`Code/SQL_Queries/`](Code/SQL_Queries/).

---

## 📌 Key Insights

- Branch-level performance can be monitored in real time instead of waiting on manual monthly reports
- Revenue trend analysis surfaces growth opportunities by business stream
- Opportunity-stage analysis highlights pipeline bottlenecks for coaching
- Policy analytics improve visibility into claims, premiums, and customer demographics
- Centralized KPI tracking enables faster, more confident decision-making

---

## 📁 Repository Structure
---

## 📸 Screenshots

Dashboard previews are available in [`Dashboards/Screenshots/`](Dashboards/Screenshots/).

---

## 🎓 Skills Demonstrated

**Data Analysis** — Data cleaning, EDA, KPI design, business analysis  
**Data Visualization** — Power BI, Tableau, Excel dashboard development  
**SQL** — Joins, aggregations, window functions, KPI calculations  
**Business Intelligence** — Performance monitoring, reporting, data storytelling

---

## 🚀 Deliverables

- ✅ Power BI Dashboards (Branch & Policy)
- ✅ Tableau Dashboards (Branch & Policy)
- ✅ Excel Dashboards (Branch & Policy)
- ✅ SQL KPI Query Library
- ✅ Full Documentation & Data Dictionary
- ✅ Project Presentation

---

## 👩‍💻 Author

**Saniya Dantal**
Data Analyst | Power BI · Tableau · Excel · SQL

GitHub: [github.com/Saniyadantal](https://github.com/Saniyadantal)
LinkedIn: [linkedin.com/in/saniya-dantal](https://linkedin.com/in/saniya-dantal)

---

## 📄 License

This project is licensed under the MIT License.
