#  Power BI Project – Shopify Business Performance Analysis
- By: Thi Doan
- Date: 10/2025
- Tool Used: `Power Query`, `DAX`, `PowerBi`

# 🧾Table Of Contents (TOCs)
1. [Background & Overview]()
2. [Dataset Description]()
3. [Key Insights & Visualization]()

# 📌Background & Overview
## Objective:
📖What is this project about?
The purpose of this project to build a dashboard using PowerBI to deliver comprehensive view of Shopify sales performance, customer retention, geographic demand, payment behavior, and product mix to support data-driven business decisions.

📖Who is this project for? 
- Business Analysts/ Data Analysts: Using the dashboard to monitor and report KPIS, identify trends and support data-driven recommendations.
- E-commerce/ Operations Managers: Tracking sales performance, customer retention, product mix, and regional demand to optimize operations and inventory.
- Marketing & Growth Teams: Analyzing customer behavior, repeat rates, top regions, and product categories to guide campaigns and retention strategies.
- Finance/ Revenue Teams: Monitoring net sales, AOV, LTV, and payment method mix for revenue planning and forecasting.
- Executives:  Gaining a high-level view of overall business health through executive-ready KPIs and trends.

❓Business Questions:
1. How is overall revenue performing, and are we on track with sales targets over time?
2. What is the most and least used payment methods?
3. What is customer preferences across regions or campaigns?
4. Determine which product types generate the highest revenue and order volume?
5. How customer engagement varies across different product categories?

# Dataset Description

## 📌 Data Source

- **Source:** Google Sheets (Shopify Sales Data)  
  https://docs.google.com/spreadsheets/d/1GeIgZ9hepgFbj4A9y8Szp9CwUPBc6RZx/edit?gid=2091921388
- **Dataset Size:** 7,432 rows
- **Format:** xlsx 

## Data Processing Using DAX and Power Query
1. Using Power Query to clean and make sure dataset is ready.
2. DAX Calculations & Formulas
- **`DAX formulas used for some KPIs requirement calculations`**
<details>
  <summary>CLICK TO VIEW</summary>
  
  <br>
  
**1. Transaction Performance**

- **Net Sales**:
```dax
Net Sales = sum(shopify_sales[Subtotal Price])
```
- **Total Quantity**:
```dax
Total Quantity = sum(shopify_sales[Quantity])
```
- **Net Average Order Value**:
```dax
Net Avg Order Value = AVERAGE(shopify_sales[Subtotal Price])
```

**2. Customer Behavior**

- **Total Customer**:
```dax
Total Customer = DISTINCTCOUNT(shopify_sales[Customer Id])
```
- **Single Order Customer**:
``` dax
Single Order Customer = 

        CALCULATE(COUNTROWS(VALUES(shopify_sales[Customer Id])), 
                FILTER(VALUES(shopify_sales[Customer Id]), 
                        CALCULATE(DISTINCTCOUNT(shopify_sales[Order Number]))= 1
                ))
```
- **Repeat Customer**:
```dax
Repeat Customer = 

        CALCULATE(COUNTROWS(VALUES(shopify_sales[Customer Id])),
                FILTER(VALUES(shopify_sales[Customer Id]),
                        CALCULATE(DISTINCTCOUNT(shopify_sales[Order Number]))>1))
```

**3. Retention & Value KPIs**

- **Life Time Value**:
```dax
Life Time Value = [Net Sales]/ [Total Customer]
```

- **Repeat Rate**:
```dax
Repeat Rate = [Repeat Customer]/[Total Customer]
```

- **Purchase Frequency**:
```dax
Purchase Frequency = DISTINCTCOUNT(shopify_sales[Order Number])/[Total Customer]
```
</details>
# 📊Key Insights & Visualizations
## I. Overview
<img width="1380" height="807" alt="image" src="https://github.com/user-attachments/assets/0d28a534-1e06-4cba-967a-592df9a8a82b" />

**From 03/18/2025 to 03/24/2025:**
- Generated **$4.18M in net sales** from **7,534 units sold**, reflecting strong overall sales performance.
- Achieved a **high average order value (AOV) of $562.63**, indicating customers purchase higher-value baskets.
- Served **4,431 customers**, with **46% repeat customers**, demonstrating solid customer retention.
- Customer value metrics show an **LTV of $943.55** and **purchase frequency of 1.68**, highlighting meaningful long-term customer value.
- Identified a sizable base of **single-order customers (2,392)**, representing an opportunity to increase repeat purchases and revenue efficiency.

<img width="591" height="266" alt="image" src="https://github.com/user-attachments/assets/148cb51e-d5d0-45b9-aa52-c9da847ae316" />












