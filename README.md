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
SELECT Order_Date, sum(sales*Quantity) AS revenue
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

![Screenshot 2024-12-20 090213](https://github.com/user-attachments/assets/14c7eaf1-6aaf-4b55-8796-94144c5027d9)
![Screenshot 2024-12-20 090935](https://github.com/user-attachments/assets/00c2c35a-e974-4fd6-ab69-634ac1982671)
![Screenshot 2024-12-20 091542](https://github.com/user-attachments/assets/8fa14069-bb7c-40db-8f86-c947b7336e4f)
![Screenshot 2024-12-20 091658](https://github.com/user-attachments/assets/8dd72574-c08d-464e-819f-0860f71d5e05)
![Screenshot 2024-12-20 091743](https://github.com/user-attachments/assets/d089407d-7577-423a-90e7-40c5c3104246)

The images above shows how results of the data queried into the SQL Server database.

#### Insights and Recommendations 
___
Insights:
1. Product Performance
    - Best performing Sub_category: [Binders, Machine and Phone]
    - Least performing Sub_category: [Fastners, Supplies, Labels]
Analysis: Top 5 sub_categories contributed greatly to the total sale.
   
2. Regional Sales Trends
    - Regions with highest sales revenue : West(725,468) and East (678,781)
    - Regions with lowest sales revenue: Central(501,240) and South (391,722)
Analysis: Sales in the West and East region grew year-over-year, while the central and south Region had no significant increase.

Recommendations: 


1. Product Optimization
    - To clear out slow moving products, I recommended using discounts or creating a bundle of the products
    - Do not restock slow moving products.
    - Increase inventory of top-selling products
    
2. Regional Sales Strategies
    - Expand operations to regions with high growth potentials
    - Adjust pricing strategies for regions with low sales revenue
  
 
3. Customer Rentation
    - Implement loyalty program to increase the purchase frequency of high value customers
    - Create special offers for customers who has'nt purchased in a long time to increase frequency
    
2. Data-Driven Decision-Making
    - Establish regular sales data analysis and review processes
    - Develop predictive analytics capabilities
    - Integrate sales data with other business functions (e.g., marketing, supply chain)

* Long-Term (18+ months):
1. Strategic Partnerships
    - Explore partnerships with complementary businesses
    - Develop strategic relationships with key suppliers
    - Investigate opportunities for expansion into new markets
      
2. Innovative Sales Strategies
    - Explore emerging sales channels (e.g., AR/VR, social commerce)
    - Develop innovative sales formats (e.g., subscription services)
    - Invest in sales technology (e.g., AI-powered chatbots)

* Action Plan
1. Assign responsibilities to team members for implementation
2. Establish timelines and milestones for recommendations
3. Monitor progress and adjust strategies as needed


