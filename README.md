# Ecommerce_Sales_DashBoard_BI
# Overview
This analysis evaluates the overall performance of the e-commerce business by examining key metrics such as total orders, total sales, and total profit. In addition, it explores other important KPIs and insights that highlight customer behavior, sales trends, and operational efficiency. The objective is to provide a comprehensive view of current performance and support data-driven decision making for future growth.

# Business Problem and Objective
The company aims to drive sustainable growth by improving its overall sales performance and profitability. The key challenges include:

Increasing Sales and Total Profit – identifying strategies to boost revenue while controlling costs.

Enhancing Average Order Value (AOV) – encouraging customers to purchase more per transaction.

Optimizing Discount Strategy – maintaining attractive discounts that appeal to customers while ensuring overall profitability.

Improving Delivery Performance – reducing and standardizing average delivery time to enhance customer satisfaction.

#### Objective:
Leverage data-driven insights to optimize pricing, discounting, and operational efficiency while enhancing customer experience. This will enable the company to increase sales, maximize profit, and strengthen long-term competitiveness.

# Dataset Description
The dataset consists of four relational tables that collectively provide insights into customers, products, sales, and timelines.

### Customers Table

Columns: Customer ID, Customer Name, Segment, Country, City, State, Postal Code, Region

Provides demographic and segmentation details about each customer.

### Dates Table

Columns: Date, Day Name, Day, Week, Month, Quarter, Year

Acts as a date dimension to enable time-based analysis and trend identification.

### Products Table

Columns: Product ID, Category, Sub-Category, Product Name, List Price

Contains details about products, their classifications, and pricing.

### Sales Table

Columns: Row ID, Order ID, Order Date, Ship Date, Delivery Date, Ship Mode, Customer ID, Product ID, Quantity, Discount

Captures transactional information including order details, delivery timelines, and discounts applied.

The tables are not initially connected. By establishing appropriate relationships (e.g., linking Customer ID, Product ID, and Date fields across tables), a comprehensive data model can be built. This enables detailed insights into customer behavior, sales performance, product demand, and operational efficiency

# Methodology 
To ensure reliable and actionable insights, the following steps were followed in preparing and analyzing the dataset:

1. Data Cleaning & Preparation

Removed unwanted columns that were not relevant to analysis.

Handled missing data by removing blank rows and eliminating duplicates.

Standardized fields to ensure consistency across all tables.

2. Data Integration & Modeling

Merged data from all four tables (Customers, Dates, Products, Sales) into a unified model.

Established relationships between tables:

Sales → Products (Many-to-One)

Sales → Customers (Many-to-One)

Sales → Dates (Many-to-One)

Created a star schema to enable flexible and efficient reporting.

3. KPI Development (using DAX)

Key performance indicators (KPIs) were calculated to measure business performance, including:

Total Customers = DISTINCTCOUNT(Customers[Customer ID])

Total Orders = DISTINCTCOUNT(Sales[Order ID])

Total Sales = SUM(Sales[Sales Amount])

Total Quantity Sold = SUM(Sales[Quantity])

Total Profit = [Total Sales] - SUMX(Sales, Sales[Discount] * Sales[Product Amount])

Profit Margin = [Total Profit] / [Total Orders]

Average Revenue per Customer = DIVIDE([Total Sales], [Total Customers], 0)

Average Order Value (AOV) = DIVIDE([Total Sales], [Total Orders], 0)

Average Items per Order = DIVIDE([Total Quantity Sold], [Total Orders], 0)

Average Discount = AVERAGE(Sales[Discount])

Average Delivery Time = AVERAGE(Sales[Delivery Time])

4. Custom & Conditional Columns

Order Value Category: A conditional column classifying purchases based on item ranges and discount eligibility.

Delivery Time (Days): A calculated column measuring delivery duration (Delivery Date - Ship Date).
