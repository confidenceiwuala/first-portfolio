# PROJECT 1 - Performance Analysis for Cee Super Store
---

## Table Of Content
---

1. [Project Overview](#project-overview)
2. [Introduction](#introduction)
3. [data source](#data-source)
4. [Methodology and Tools Used](#methodology-and-tools-used)
5. [Data Exploration](#data-exploration)
6. [Microsoft Excel](#microsoft-excel)
7. [SQL Queries](#sql-queries)
8. [PowerBI Dashboard](#powerbi-dashboard)
9. [Insights and Recommendations](#insights-and-recommendations)
10. [Conclusion](#conclusion)
11. [Appendices](#appendices)
    

## Project Overview
---
This project seeks to generate insights into the performance of Cee Super Store. By analyzing the data set, we seek to uncover insight to enhance decision making


## Introduction
---
Cee Super Store, is a leading retail store with multiple locations across the region, In order to enhance decision-making, the management seeks to optimize its sales performance and improve customer engagement, in order to stay at the top of their game.


* Problem Statement
  
The store's current sales analysis process is manual, time-consuming, and limited in scope. The management team lacks a comprehensive understanding of across the different products, and even region hence, hindering strategic decision-making.

* Project Objectives
  
1. Analyze sales data to identify key insights such as best performing sub-category, regional performance, yearly sales trends and customer behaviour
2. Develop a data-driven framework for sales performance evaluation.
3. Provide actionable insights to inform product optimization, regional sales strategies, and customer engagement initiatives.
4. Create a scalable and interactive sales dashboard for ongoing monitoring and analysis.

* Dataset Description
  
The project utilizes a comprehensive sales dataset spanning [January 2014- December 2017], encompassing:
- Order ID
- Order Date
- Ship Date
- Ship Mode
- Customer ID
- Customer Name
- Segment
- Country
- City
- State
- Postal Code
- Region
- Product ID
- Category
- Sub-Category
- Product Name
- Sales
- Quantity
- Discount
- Profit
- Total Sales

## Data Source
-----

The primary source of this data is kaggle which is an onlline open source

## Methodology and Tools Used
---

This project employs a combination of data cleaning, SQL querying, and data visualization techniques using:

- Microsoft Excel for data cleaning and visualization
- SQL Server for data querying and analysis
- Power BI for interactive dashboard creation

#### Data Exploration
___

#### Microsoft Excel
- EXCEL PIVOT TABLE AND CHARTS


 - Total profit by sub-category.

   
![profit by sub-category](https://github.com/user-attachments/assets/269e4994-499e-4644-8cd4-aadce3749530) ![total profit by sub-category graph](https://github.com/user-attachments/assets/d76b83e1-6b4a-4831-8754-b4584868dac0)


This image shows the result of total profit by sub-category.

  - Total sales by Region

![Sales by Region](https://github.com/user-attachments/assets/0e103ede-aaef-4b75-9ce1-361e4bb5969a) ![Sales by Region graph](https://github.com/user-attachments/assets/87683d38-4cac-423a-9139-daeb16fe6b37)



This image shows the result of total sales by region.

   - Total sales and profit by year.
     
![Annual sales and Profit](https://github.com/user-attachments/assets/fd645fc8-8122-47a2-bbe0-13b13825cc2f) ![Annual Sales and Profit Graph](https://github.com/user-attachments/assets/0fa1a4bb-23ec-49b3-ba79-8b0028d30c75)

This image shows the Annual Sales and Profit

#### SQL Queries
---

 Query 1: Customer Purchase Frequencey
```
SELECT 
    customer_id, customer_name,
    COUNT(order_id) AS purchase_frequency,
    CASE 
        WHEN COUNT(order_id) >= 20 THEN 'High Frequency'
        WHEN COUNT(order_id) BETWEEN 10 AND 19 THEN 'Medium Frequency'
        ELSE 'Low Frequency'
    END AS frequency_segment
FROM 
    [Sample - Superstore 1]
GROUP BY 
    customer_id, Customer_Name
	order by 3 desc
```


 Query 2: Total revenue generated per customer by sales amount.
 ```
select customer_name, sum(Sales*Quantity) as total_revenue_customer
from [Sample - Superstore 1]
group by Customer_Name
order by 2 desc
```


 Query 3: Total Sales over time.
```
SELECT Order_Date, SUM(sales) AS revenue
FROM [Sample - Superstore 1]
GROUP BY Order_Date
ORDER BY Order_Date
```

 Query 4: Percentage of Total Sales by Region.
```
SELECT Region, SUM(sales*Quantity)/SUM(Quantity)*0.1 AS Percentage_of_Total_Sales
FROM [dbo]. [Sample - Superstore 1]
GROUP BY Region
ORDER BY Percentage_of_Total_Sales
```

 Query 5: Least selling Product in 20217
```
	SELECT Product_Name,SUM(Quantity) AS Sales
FROM [Sample - Superstore 1]
WHERE year(Order_Date)='2017'
GROUP BY Product_Name
HAVING SUM(Quantity)=1
```


