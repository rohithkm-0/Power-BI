🛒 E-COMMERCE BUSINESS PERFORMANCE & ANALYTICS DASHBOARD
SQL | Microsoft Power BI | Power Query | DAX
📌 Project Overview

The E-Commerce Business Performance & Analytics Dashboard is a data analytics and business intelligence project developed to analyze e-commerce sales, profitability, product performance, customer behavior, and order-level metrics.

The project combines SQL for data cleaning and preparation with Microsoft Power BI for interactive dashboard development and business analysis.

SQL is used to handle missing values, standardize data, and correct inconsistencies in the dataset. Power BI transforms the prepared data into interactive visualizations that help users monitor business performance, compare products and brands, evaluate payment methods, and explore sales and profitability trends.

The dashboard consists of three main pages:

Executive Overview – Overall sales, profit, tax, and financial performance.
Product Performance – Product costs, brand comparisons, supplier analysis, and product ratings.
Order Analytics – Order-level profitability, sales metrics, discounts, and product pricing.

This project demonstrates practical skills in data cleaning, SQL querying, business intelligence, KPI reporting, and interactive data visualization.

🎯 Project Objectives
Clean and prepare raw e-commerce data using SQL.
Handle missing, blank, and inconsistent values.
Analyze gross sales, net sales, profit, and tax.
Evaluate country-wise profitability.
Compare product costs across brands and suppliers.
Analyze payment methods and discount distributions.
Explore product ratings and brand performance.
Analyze order-level sales and profitability.
Develop interactive Power BI dashboards using slicers and visualizations.
Generate meaningful business insights to support data-driven decision-making.
🛠️ Tools & Technologies
Tool / Technology	Purpose
MySQL / SQL	Data cleaning, data validation, filtering, and querying
Microsoft Power BI	Interactive dashboard development
Power Query	Data transformation and preparation
DAX	Calculated measures and KPI development
Data Visualization	Presenting business metrics through charts and graphs
Data Analysis	Identifying trends, patterns, and performance differences
GitHub	Project documentation and portfolio management
🗄️ 1. SQL Data Cleaning & Preparation

Before developing the Power BI dashboard, SQL was used to clean and prepare the e-commerce dataset for analysis.

The data preparation process focused on handling missing values, standardizing text fields, correcting data inconsistencies, and validating records.

🔹 Data Cleaning Tasks

1. Handling Missing Campaign Names

Blank, whitespace-only, and NULL values in the campaign_name column were replaced with insta_reel.

UPDATE ecommerce_sales_customer_analytics_150k
SET campaign_name = 'insta_reel'
WHERE campaign_name IS NULL
   OR TRIM(campaign_name) = '';

2. Handling Missing Coupon Codes

Missing coupon codes were replaced with SAVE50.

UPDATE sales
SET coupon_code = 'SAVE50'
WHERE coupon_code IS NULL
   OR TRIM(coupon_code) = '';

3. Handling Missing Customer Ratings

Missing customer ratings were replaced with 0.

UPDATE sales
SET customer_rating = 0
WHERE customer_rating IS NULL;

4. Handling Missing Customer Reviews

Missing customer review values were standardized to None.

UPDATE sales
SET customer_review = 'None'
WHERE customer_review IS NULL
   OR TRIM(customer_review) = '';

5. Handling Missing Review Sentiments

Missing review sentiment values were standardized to None.

UPDATE sales
SET review_sentiment = 'None'
WHERE review_sentiment IS NULL
   OR TRIM(review_sentiment) = '';

6. Correcting Product Categories

The product_category value for a selected product record was corrected to Electronics.

UPDATE product_catalog
SET product_category = 'Electronics'
WHERE product_id = 'ORD-694188';

Note: Verify that ORD-694188 is actually stored in the product_id column before running this statement. The identifier resembles an order ID, so confirm the record and column to avoid modifying the wrong product.

7. Verifying Data After Cleaning

The following query can be used to check whether missing campaign names remain:

SELECT *
FROM sales
WHERE campaign_name IS NULL
   OR TRIM(campaign_name) = '';

To review the distribution of campaign names:

SELECT
    campaign_name,
    COUNT(*) AS total_records
FROM sales
GROUP BY campaign_name
ORDER BY total_records DESC;
🔹 SQL Skills Demonstrated
SELECT, UPDATE, and WHERE statements.
Handling NULL values.
Identifying blank and whitespace-only values using TRIM().
Standardizing missing categorical values.
Correcting inconsistent product information.
Grouping records using GROUP BY.
Validating data after updates.
Preparing datasets for business intelligence reporting.

Data preparation note: These queries document the cleaning operations performed or planned in the project. Use the actual table names in your database. If you have renamed ecommerce_sales_customer_analytics_150k to sales, use sales consistently in subsequent queries.

📊 2. Power BI Dashboard Development

The cleaned data is used to develop an interactive, three-page Power BI dashboard.

📍 Page 1: Executive Overview

The Executive Overview provides a consolidated view of the e-commerce business's financial performance.

Key Performance Indicators (KPIs)
Total Profit: Overall profit generated from business transactions.
Total Tax: Total tax amount.
Net Sales: Sales value after applicable adjustments.
Gross Sales: Sales value before applicable deductions.
Visualizations
Visualization	Business Purpose
Country-wise Profit Bar Chart	Compare profitability across countries
Product Cost by Payment Method	Analyze product costs across payment methods
Profit Margin Area Chart	Examine profit margin trends over time
Discount Amount Treemap	Compare discount amounts across payment methods
Tax Distribution Doughnut Chart	Explore tax distribution across currencies
Sales and Profit Comparison	Compare gross sales, net sales, and profit
Interactive Filters
Country
Payment Method
Gender
Business Questions
Which countries generate the highest profit?
Which payment methods account for the highest product costs?
How does the profit margin change over time?
How are discounts distributed across payment methods?
How does profit compare with gross sales and net sales?
📍 Page 2: Product Performance

The Product Performance page focuses on understanding product costs, supplier contributions, brand comparisons, and product ratings.

Key Performance Indicators (KPIs)
Total Unit Price: Aggregated unit price metric.
Total Cost: Combined product cost.
Most Used Brand: Brand highlighted by the dashboard's measure.
Product Rating: Aggregated product rating metric.
Visualizations
Visualization	Business Purpose
Brand-wise Cost Bar Chart	Compare product costs across brands
Supplier-wise Unit Price Chart	Analyze unit prices across suppliers
Product Subcategory Funnel-Style Chart	Compare unit prices across product subcategories
Product Rating by Brand	Examine rating differences between brands
Interactive Filters
Brand
Supplier
Business Questions
Which brands contribute the highest product costs?
Which suppliers have the highest aggregate unit prices?
How do product prices differ across subcategories?
Which brands have higher product ratings?
How does selecting a particular brand or supplier change the analysis?
📍 Page 3: Order Analytics

The Order Analytics page provides a detailed view of selected orders, product prices, sales metrics, and profitability.

Key Performance Indicators (KPIs)
Total Unit Price
Net Sales
Gross Sales
Additional unit-price summary metric

The dashboard currently displays two cards labelled Total Unit Price. Their titles and underlying measures should be reviewed to ensure that each card communicates a distinct and meaningful metric.

Visualizations
Visualization	Business Purpose
Profit by Order ID	Compare profit across selected orders
Net Sales Gauge	Compare net sales against a reference scale
Financial Performance Bar Visualization	Compare discount amount, unit price, and profit
Currency Distribution Pie Chart	Examine the distribution of selected records across currencies
Product Price Treemap	Compare unit prices across selected products
Interactive Filters
Currency
Product ID
Order ID
Business Questions
Which selected orders generate the highest profit?
How do net sales compare with the gauge's reference value?
How do discounts, unit prices, and profits compare?
How are selected records distributed across currencies?
Which selected products contribute the highest aggregate unit prices?
📈 3. Key Performance Indicators

The dashboard uses several financial and product metrics to monitor business performance.

KPI	Description
Gross Sales	Sales value before applicable deductions
Net Sales	Sales value after applicable deductions or adjustments
Total Profit	Total profit generated from transactions
Total Tax	Total tax amount
Total Cost	Combined product cost
Total Unit Price	Aggregated unit-price metric
Profit Margin	Profitability expressed as a percentage
Discount Amount	Total discounts applied to transactions
Product Rating	Product rating metric used in the dashboard

The precise calculation of each KPI depends on the underlying dataset and the measures configured in Power BI.

💡 4. Key Business Insights

The dashboard enables users to investigate important business performance questions.

🌍 Geographic Performance

Compare profitability across countries to identify strong-performing markets and markets that may require further investigation.

💳 Payment Method Analysis

Explore product costs and discount distributions across Debit Card, Credit Card, PayPal, Cash on Delivery, Digital Wallet, and Buy Now Pay Later.

🏷️ Brand Performance

Compare product costs across brands such as Samsung, LG, HP, Sony, OnePlus, Apple, and others.

🚚 Supplier Analysis

Examine aggregate unit prices across suppliers to understand differences in supplier-related pricing metrics.

⭐ Product Ratings

Explore how product ratings vary across brands and identify products that may warrant additional customer feedback analysis.

💰 Sales and Profitability

Compare gross sales, net sales, and total profit to understand the relationship between revenue and profitability.

🛍️ Order-Level Analysis

Filter individual orders and products to investigate their contribution to selected sales, pricing, and profit metrics.

Important: These are analytical questions supported by the dashboard, not claims that specific business outcomes have already been established. Final conclusions should be drawn from validated calculations and filtered data.

🎨 5. Dashboard Features
Three interactive Power BI report pages.
KPI cards for financial and product performance.
Country-wise profitability analysis.
Brand-wise and supplier-wise comparisons.
Payment method and discount analysis.
Product rating analysis.
Order-level filtering.
Currency-based analysis.
Interactive slicers and cross-filtering.
Multiple chart types, including bar charts, area charts, treemaps, doughnut charts, pie charts, and gauges.
Page navigation buttons for moving between report sections.
📂 6. Project Structure

The following structure is recommended for your GitHub repository.

E-Commerce-Business-Performance-Analytics/
│
├── README.md
│
├── SQL/
│   └── data_cleaning.sql
│
├── PowerBI/
│   └── E-Commerce_Business_Performance.pbix
│
├── Screenshots/
│   ├── Executive_Overview.png
│   ├── Product_Performance.png
│   └── Order_Analytics.png
│
└── Dataset/
    └── README.md

Note: Replace the example filenames with your actual files. Add the dataset only if you have permission to share it. If you cannot distribute the dataset, use Dataset/README.md to describe its source and how others can obtain access.


🧠 7. Skills Demonstrated

Through this project, I developed and applied practical skills in:

SQL

Data cleaning and validation.
Handling NULL and blank values.
Text standardization.
Updating inconsistent records.
Aggregation and data verification.

Power BI

Interactive dashboard development.
KPI visualization.
Report navigation.
Slicers and cross-filtering.
Business performance reporting.

Power Query and DAX

Data transformation and preparation.
Creating calculated measures.
Developing business metrics.
Supporting interactive analytical reports.

Business Analytics

Sales and profitability analysis.
Product and brand performance analysis.
Supplier and payment method comparisons.
Order-level analysis.
Converting business questions into meaningful visualizations.
🔮 8. Future Enhancements

Potential improvements to the project include:

Adding month-over-month and year-over-year sales comparisons.
Developing customer segmentation and purchasing behavior analysis.
Adding product category profitability analysis.
Implementing drill-through pages for detailed order investigations.
Creating sales forecasting and profit trend projections.
Adding customer acquisition and marketing campaign performance analysis.
Introducing automated data refresh and scheduled reporting.
Enhancing KPI cards with percentage growth and variance indicators.
👨‍💻 9. Author

Rohith K Mohan

B.Sc. Artificial Intelligence
Aspiring Data Analyst

Technical Skills: SQL | Microsoft Power BI | Excel | Tableau | Python | Data Visualization | Business Intelligence
