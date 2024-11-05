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

**a. Total Sales by Product**

![Screenshot 2024-11-05 073543](https://github.com/user-attachments/assets/98173c8b-f9b4-415f-b6eb-dcafabe5eb57)

- Shoes are the top-selling product: With sales of $3,087,500 million, shoes are significantly outperforming other products.
  
- Shirts follow closely behind shoes, with total sales of $2,450,000 indicating strong demand for this product category.
  
- Hats, gloves, jackets, and socks have significantly lower sales compared to shoes and shirts.
  
- While shoes and shirts are the top performers, exploring opportunities to boost sales of other products could be beneficial.

  **b. Total Sales by Region**

  ![Screenshot 2024-11-05 081123](https://github.com/user-attachments/assets/0f9442ce-e6f9-4294-9b59-ee459f058f54)

- The South region is the leading region with 44.16% in total sales , contributing significantly more than the other regions.
  
- The East region contributes 23.14% to the total sales.
  
- The North and West regions have relatively similar sales figures, each contributing 18.42% and 14.29% respectively to the total revenue.

**c. Total Sales by Month**

![Screenshot 2024-11-05 082152](https://github.com/user-attachments/assets/4cb21a59-f53f-4eee-ac03-bb9b9ec9c997)

- Sales experienced a significant spike in February, reaching a peak of $2.8 million in 2023 and $1.5 million in 2024
  
- Following the February peak, sales generally declined throughout the year, with a slight increase in August of 2023.
  
- There seems to be a seasonal pattern, with higher sales in the earlier months and lower sales towards the end of the year.

**d. Revenue per product per year**

![Screenshot 2024-11-05 084927](https://github.com/user-attachments/assets/47128b7a-a30e-41ea-9a5c-c3e4a334caad)

- The total revenue has increased significantly from 2023 to 2024, indicating strong sales performance.
  
- The company has a diversified product line, with each product contributing to overall revenue.
  
- Shoes and Shirt consistently generated the highest revenue in both years, making them key contributors to the overall sales.
  
- The Hat product experienced significant growth in 2024, indicating a potential shift in consumer preferences or successful marketing strategies.
  
- Gloves maintained a steady revenue in 2023 but experienced a decrease in 2024. This could be due to various factors such as reduced demand, increased competition, or pricing strategies.
  
- Socks and Jacket: These products had relatively lower sales compared to others, suggesting potential areas for improvement or niche market targeting.
  
**e. Top 5 Revenue generating Customers**

![Screenshot 2024-11-05 090207](https://github.com/user-attachments/assets/298e77a0-a71c-4ed0-950d-ae3321f9a44f)

- The chart highlights the top 5 customers based on their revenue contribution.
  
- Customers Cus1233 and Cus1354 are the top revenue generators, each contributing $25,000.
  
- The remaining customers (Cus1497, Cus1478, and Cus1408) have similar revenue contributions, falling within a slightly lower tier.


**f. Quantity Sold by product**

![Screenshot 2024-11-05 090421](https://github.com/user-attachments/assets/075913ae-3098-4487-90fb-8db8f8a50e31)

- The top-selling product is the Hat, selling 80,000 which accounts for 23.19% of the total quantity sold, closely followed by Shoes with 73,000 units sold, contributing 21.01% to total quantity sold.

- Gloves and Shirts have significantly lower sales compared to Hat sand Shoes but equally contributed 18.12% respectively to the total quantity sold.
  
- Socks and Jacket have lover sales volumes, contributing less than 12% to the overall sales mix.

**g. 

![Screenshot 2024-11-05 093009](https://github.com/user-attachments/assets/f92d4338-7724-4a41-b8c7-5e4267c11106)

- The chart reveals distinct seasonal patterns in average quantity sold.

- Sales peaked in February and June, indicating potential factors like seasonal promotions, holidays, or product launches driving these spikes.
  
- March, July and October show relatively stable performance, indicating consistent demand during these months.

- There was fluctutions in January, August,September, November, December sales

- April and May witnessed a significant drop in average quantity sold, suggesting a potential decline in demand or other factors influencing sales during these months.
