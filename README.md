# 📊 Superstore Sales & Profitability Analysis

An interactive Power BI dashboard designed to analyze sales performance, regional trends, and product profitability using the classic **Sample - Superstore** dataset.

## 🚀 Live Demo
*(If you have published to Power BI Service, paste the link here. Otherwise, delete this line.)*

## 📝 Project Overview
The goal of this project was to transform raw retail data into actionable business insights. I focused on identifying high-value customers, underperforming regions, and seasonal sales trends.

### Key Questions Answered:
- Which **Product Categories** are the most profitable?
- How do **Sales vs. Profit** trends look over time?
- Which **States/Regions** are missing their targets?
- Who are the **Top 10 Customers** by revenue?

## 🛠️ Tech Stack & Tools
- **Power BI Desktop**: Data Visualization & Modeling.
- **Power Query (M)**: Data Cleaning and Transformation.
- **DAX (Data Analysis Expressions)**: Creating calculated measures.
- **CSV Data Source**: Sample - Superstore dataset.

## 🧹 Data Cleaning Process
During the ETL (Extract, Transform, Load) phase, I performed the following:
- **Date Formatting**: Resolved "Locale" issues to ensure `Order Date` was correctly identified as a Date type.
- **Column Optimization**: Changed `Postal Code` to Text to prevent accidental summation.
- **Data Quality**: Removed null values and ensured currency columns were set to Fixed Decimal.

## 📈 Calculated Measures (DAX)
Some of the key metrics I created include:
```dax
// Total Revenue
Total Sales = SUM('Sample - Superstore'[Sales])

// Total Profit
Total Profit = SUM('Sample - Superstore'[Profit])

// Profit Margin %
Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)

// Year-over-Year Sales Growth
YoY Sales = 
VAR PreviousYear = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Calendar'[Date]))
RETURN
DIVIDE([Total Sales] - PreviousYear, PreviousYear)
