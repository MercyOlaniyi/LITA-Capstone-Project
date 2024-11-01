# LITA-Capstone-Project

# Sales Performance Analysis for a Retail Store
---
[Project Overview](#project-overview)

[Dataset Description](#dataset-description)

[Time Period](#time-period)

[EDA](#eda)

[Data Preprocessing](#data-preprocessing)

[Analytical Tools](#analytical-tools)


## Project Overview
---
### Objective: 
Analyze the sales performance of a retail store using the provided sales data to uncover insights such as top-selling products, regional sales performance, and monthly trends. Create visualizations and reports based on this analysis.

### Dataset Description
The dataset consists of information such as OrderID, Customer Id, Product, Region, OrderDate, Quantity, and UnitPrice.

### Data Source 
This is a public dataset that was freely provided by the facilitator.

### Data Fields
- **OrderID:** A unique identifier assigned to each order placed.
- **Customer ID:** A unique identifier associated with the customer who placed the order.
- **Product:** The specific item or product purchased in the order.
- **Region:** The geographic location where the order was placed or delivered.
- **OrderDate:** The date when the order was placed.

### Time Period
The dataset spans from 2023-2024

### EDA 
The following insights will be drawn from the dataset

1. Top-selling products
2. Regional performance
3. Monthly sales trends

### Data Preprocessing
- **Data loading and inspection**: To have a general overview of the data
- **Data Cleaning**: Data was complete and clean.

### Analytical Tools 
- Microsoft Excel was used in analysis and summarization of the dataset
- SQL was used to query the data for further insights
- PowerBI was used to visualize the insight drawn from the dataset.
  
Analysis Breakdown


#### 1a. Use pivot tables to summarize 
**i. Total sales by product**

![Total Sales by Product](https://github.com/user-attachments/assets/0133a7a6-2378-4aca-9455-6f892e425157)

**ii. Total Sales by region**

![Total Sales by Region](https://github.com/user-attachments/assets/e402bb6f-fe5d-4578-b1ae-fdf83ce9d1ca)

**iii. Total Sales per Month**

![Quantity Sold per Month](https://github.com/user-attachments/assets/1621c07a-0538-4952-95b7-5a8e9d001464)

#### 1b. Use Excel formulas to calculate metrics such as;

**i. Average sales per product**

![Avg Sales per product](https://github.com/user-attachments/assets/17a15c47-cdc7-445f-a650-0fbb3e84c9b6)

**ii. Total revenue by region and Top 10 Revenue Generating Customers**

![Top 10 Revenue Gerating Customers](https://github.com/user-attachments/assets/fcbba7ca-c2ab-42d5-a0b3-df2ad0383261)

#### 2. Using SQL write queries to extract key insights 

**i.  Total sales for each product category**

```
--Retrieve the total sales for each product category.
SELECT 
	DISTINCT(Product),SUM(Revenue_Quantity_Unit_Price) as Total_Sales
FROM New_Sales_File
GROUP BY Product
````

![SQL -- Total sales for each product category](https://github.com/user-attachments/assets/291d04bb-ea11-4bec-a295-0626b4da7773)


**ii. Number of sales transactions in each region**
```
--Find the number of sales transactions in each region.
SELECT
	DISTINCT(Region), SUM(Quantity) as Sales_Transactions
FROM New_Sales_File
GROUP BY Region
```

![SQL -- Number of Sales Transaction per Region](https://github.com/user-attachments/assets/94423070-7e6b-429e-ab5e-3bb97eda62e0)


**iii. Highest-selling product by total sales value**
```
--Find the highest-selling product by total sales value. 
SELECT 
	DISTINCT(Product),SUM(Revenue_Quantity_Unit_Price) as Total_Sales
FROM New_Sales_File
GROUP BY Product
ORDER BY Total_Sales desc
```

![SQL -- Highest Selling Product by Sales](https://github.com/user-attachments/assets/8671794a-d9a5-4674-b2f6-d50cdf4e392a)


**iv.Total revenue per product**
```
-- calculate total revenue per product
SELECT 
	DISTINCT(Product),SUM(Revenue_Quantity_Unit_Price) as Total_Revenue
FROM New_Sales_File
GROUP BY Product
```

![SQL -- Total Revenue by Product](https://github.com/user-attachments/assets/53ab5bba-db33-48d7-a292-47906443689b)


**v.Top 5 customers by total purchase amount**
```
-- calculate monthly sales totals for the current year. 
SELECT * FROM New_Sales_File

-- Find the top 5 customers by total purchase amount. 
SELECT TOP 5 Customer_Id, SUM(Revenue_Quantity_Unit_Price) as Total_Sales
FROM New_Sales_File
GROUP BY Customer_Id
ORDER BY Total_Sales DESC;
```

![SQL -- Top 5 customers by total purchase](https://github.com/user-attachments/assets/eb96f701-143a-44ad-a840-1ea019bfbb07)


**vi. Percentage of total sales contributed by each region**
```
--calculate the percentage of total sales contributed by each region. 
SELECT 
    Region,
    SUM(Revenue_Quantity_Unit_Price) AS Region_Sales,
    (SUM(Revenue_Quantity_Unit_Price) * 100.0 / (SELECT SUM(Revenue_Quantity_Unit_Price) FROM New_Sales_File)) AS Percentage_Of_Total_Sales
FROM New_Sales_File
GROUP BY Region
ORDER BY Percentage_Of_Total_Sales DESC;
```

![SQL -- Percentage of Sales per Region](https://github.com/user-attachments/assets/f628267d-a59b-4ad8-949e-a37566b0f79f)


#### 3. Using Power Bi to Create a dashboard that visualizes the insights found in Excel and SQL.
