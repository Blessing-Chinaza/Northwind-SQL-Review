# Northwind SQL Review

## Overview

**Northwind SQL Review** is a curated project that explores the classic **Northwind sample database** using SQL.  
The project goes beyond simple queries by combining **SQL scripts, analytical results, and detailed reviews** to answer real-world business questions and uncover meaningful insights.

Through this work, the project demonstrates how SQL can be applied to:

- **Customer Analysis**: Identifying high-value customers, loyalty patterns, and purchase behaviors.  
- **Employee Performance**: Ranking employees by sales contributions and order management efficiency.  
- **Product Insights**: Highlighting top revenue-generating products and categorizing them into performance tiers.  
- **Shipper Evaluation**: Comparing delivery times and efficiency across shipping providers.  
- **Sales Trends**: Analyzing yearly growth, regional performance, and market fluctuations.  

By integrating queries with narrative reviews, the project transforms raw data into **actionable business intelligence**.  
It serves as both a **learning resource** for SQL practitioners and a **strategic toolkit** for organizations seeking to leverage data for decision-making.
 

### Purpose & Objectives
The goal of this project is to go beyond running queries and create a structured, insightful exploration of the dataset. Specifically, it aims to:

- **Demonstrate SQL proficiency** by solving realistic business problems with clear, optimized queries.  
- **Build reusable analytics assets** such as views and CASE‑based classifications for streamlined reporting.  
- **Combine queries with results** to ensure transparency and reproducibility of analysis.  
- **Provide narrative reviews** that interpret the numbers, turning raw data into actionable insights.    

### Key Focus Areas
- Monthly and yearly sales trends  
- Top‑performing products and categories  
- Customer segmentation by average order value  
- Shipper efficiency and delivery performance  
- Revenue classification using CASE statements

---

## Database Schema

The **Northwind** sample database models a trading company’s operations.  
Below are the core tables included in the schema:

- **Customers** → stores client information such as company name, contact details, and location.  
- **Shippers** → contains shipping companies responsible for delivering orders.  
- **Categories** → defines product categories and descriptions.  
- **Employees** → holds employee records including names, titles, and reporting structure.  
- **EmployeeTerritories** → maps employees to the territories they manage.  
- **OrderDetails** → line‑item details for each order, including product, quantity, price, and discount.  
- **Orders** → records customer orders, linking to employees, shippers, and customers.  
- **Products** → catalog of items sold, including supplier, category, and stock information.  
- **Region** → defines geographical regions used to group territories.  
- **Suppliers** → contains supplier information such as company name, contact details, and location.  
- **Territories** → defines sales territories, linked to regions and employees.  

---

### Below is the Entity Relationship Diagram
*([![Image_ERD](./images/image_erd.png)].)*

---

## Analytical Questions

The following SQL questions form the core of **Northwind SQL Review**.  
Each query is designed to answer a realistic business problem using the Northwind dataset.

1. **Top Customers by Spending**  
   Write a query to identify the top 5 customers who have spent the most money across all orders.  
   Include the customer’s name, total amount spent, and rank them in descending order of spending.  

2. **Employee Sales Performance**  
   For each employee, calculate the total sales value they are responsible for (based on the orders they handled).  
   Display the employee’s full name and their total sales, sorted from highest to lowest.  

3. **Monthly Sales Trends**  
   Generate a report showing total sales per month for the last two years.  
   Include the year, month, and total sales amount. Order the results chronologically to visualize growth trends.  

4. **Top Product per Category**  
   For each product category, find the single product that generated the highest total sales.  
   Show the category name, product name, and total sales value.  

5. **Orders with Many Products**  
   Identify all orders that contain more than 5 distinct products.  
   Display the order ID, customer name, and the count of distinct products in that order.  

6. **Average Order Value per Customer**  
   Compute the average order value for each customer.  
   Display the customer’s name, their average order value, and rank them from highest to lowest.  

7. **Shipper Delivery Comparison**  
   Compare shippers by their average delivery time.  
   Calculate the difference between OrderDate and ShippedDate for each order, then compute the average delivery time per shipper.  

8. **Employees Above Company Average**  
   Find employees whose total sales exceed the company’s overall average sales.  
   Display the employee’s name and their total sales, alongside the company average for comparison.  

9. **Sales by Year and Region**  
   Show total sales grouped by year and customer region (based on the Country field in the Customers table).  
   Display year, region, and total sales amount.  

10. **Frequent Customers per Year**  
    Identify customers who placed more than 3 orders in a single year.  
    Display the customer’s name, the year, and the number of orders they placed.  

11. **Top Products per Year**  
    For every year, list the top 3 products ranked by total sales revenue.  
    Include year, product name, and revenue.  

12. **Customer Lifetime Value**  
    Calculate the total revenue generated by each customer across all orders.  
    Rank customers by lifetime value.  

13. **Employee Order Counts per Year**  
    Show how many orders each employee processed per year.  
    Include employee name, year, and order count.  

14. **Orders Without Discounts**  
    Find all orders where none of the order details had a discount applied.  
    Display order ID, customer name, and order date.  

15. **High Revenue, Low Order Products**  
    Which products have consistently generated high sales but received fewer orders compared to others?  
    Write a review highlighting these products, explaining why they might be strong performers despite lower order counts.  

16. **Customer Order Gaps**  
    Calculate the average number of days between orders for each customer.  
    Show customer name and average gap in days.  

17. **Above Average Orders**  
    Find orders whose total value is greater than the average order value across all orders.  
    Display order ID, customer, and total value.  

18. **Employee–Customer Relationships**  
    For each employee, list the customers they have served, along with the number of orders handled for each customer.  

19. **Yearly Sales Growth**  
    Compute total sales per year and calculate the percentage growth compared to the previous year.  

20. **Revenue Categories (CASE Statement)**  
    Use a CASE statement to classify revenue into categories (e.g., Low, Medium, High).  

---
## Queries And Reviews

## Query 1: Top 5 Customers by Spending

[![Image_1](./images/image_1.png)]

**Review**  The table shows that 'QUICK-Stop' has spent the most across all orders, followed closely by 'Save-a-lot Markets'.
This indicates that these customers are the highest contributors to revenue, making them prime candidates for loyalty programs, targeted promotions, or priority support. Their spending patterns highlight the importance of focusing on high-value customers to sustain business growth.

## Query 2: Employee Sales Performance

[![Image_2](./images/image_2.png)]

**Review** The results show that Peacock Margaret is the top performer, generating the highest total sales among all employees.
On the other end, Buchanan Steven recorded the lowest sales, indicating potential areas for improvement or differences in customer assignments.
This ranking provides valuable insight into employee performance, helping management identify top contributors, reward excellence, and support employees who may need additional training or resources.

## Query 3: Monthly Sales Trends

[![Image_3a](./images/image_3a.png)]

**Review** The results show monthly sales trends starting from 1996-07 through 1998-05.
This chronological breakdown highlights how sales evolved over time, making it possible to visualize growth patterns and seasonal fluctuations.
Such insights are useful for identifying peak months, planning inventory, and forecasting demand.
The steady progression across months also provides a foundation for year-over-year comparisons and growth analysis.

## Query 3b: Create View for Yearly Monthly Performance

 [![Image_3b](./images/image_3b.png)]

**Review** This query creates a view named YearlyMonthlyPerformance that stores monthly sales totals grouped by year and month.
By encapsulating the logic in a view, analysts can easily reuse this dataset for trend analysis, reporting, and forecasting without rewriting the query each time.
The results span from 1996-07 through 1998-05, providing a structured foundation for visualizing growth trends and comparing performance across months and years.

## Query 4: Top Product per Category

[![Image_4](./images/image_4.png)]

**Review** The query identifies the highest‑selling product in each category by ranking products based on total sales value.
The results show that:

- Beverages → Cte de Blaye with a total sales value of 149,984.20 was the top performer.

- Condiments → Vegie-spread followed with 17,696.30 in sales.

This analysis highlights which products dominate their categories, providing valuable insights for inventory management, marketing focus, and strategic promotions.
Products like Cte de Blaye demonstrate strong demand and profitability, making them critical to sustaining category performance.

## Query 5: Orders with Many Products

 [![Image_5](./images/image_5.png)]

**Review** The query identifies orders that contain more than 5 distinct products.
The results show that 4 rows were affected, with the standout being:

- OrderID 11077 → Rattlesnake Canyon Grocery containing 25 distinct products.

This indicates that certain customers place large, diverse orders, which may reflect bulk purchasing behavior or special events.
Such insights can help in customer segmentation, identifying wholesale buyers, and tailoring marketing or logistics strategies to support high‑volume, multi‑product orders.


## Query 6: Average Order Value per Customer

[![Image_6](./images/image_6.png)]

**Review** This query calculates the average order value per customer and ranks them from highest to lowest.
The results show that QUICK-Stop consistently tops the chart with an average order value of 4,195.84, making it the most valuable customer in terms of order size.

This insight is crucial for identifying high-value customers who contribute significantly to revenue per transaction.
Such customers may benefit from personalized loyalty programs, premium offers, or dedicated account management to strengthen relationships and maximize retention.

## Query 7: Shipper Delivery Comparison

[![Image_7](./images/image_7.png)]

**Review** This query calculates the average delivery time per shipper by measuring the difference between the order date and the shipped date.
The results show:

-United Package → 9.23 days (highest average delivery time)

-Speedy Express → 8.57 days

-Federal Shipping → 7.47 days (fastest among the three)

This comparison highlights differences in shipper efficiency.
United Package, while reliable, takes longer on average, whereas Federal Shipping demonstrates quicker turnaround.
Such insights can guide logistics decisions, helping the company prioritize faster shippers for urgent deliveries and negotiate service improvements with slower ones.

## Query 8: Employees Above Company Average Sales

[![Image_8](./images/image_8.png)]

**Review** This query compares each employee’s total sales against the company’s overall average sales.
The results show that the following employees exceeded the company average of 150,495.40:

-Davolio Nancy → 202,143.71

-Fuller Andrew → 177,749.26

-Leverling Janet → 213,051.30

-Peacock Margaret → 250,187.45

These employees represent the top performers in the company, consistently generating sales above the organizational benchmark.
This insight is valuable for recognizing high achievers, designing incentive programs, and identifying best practices that can be shared across the sales team.

## Query 9: Sales by Year and Region

[![Image_9](./images/image_9.png)]

**Review** This query groups total sales by year and customer region (country), providing a breakdown of revenue across different geographies over time.
The results highlight the top regions per year:

-1996 → Austria with 29,352.00

-1997 → Argentina with 1,816.60

-1998 → Argentina with 6,302.50

This analysis reveals how sales performance varies across regions and years. It can be used to identify emerging markets, regional strengths, and opportunities for expansion. For example, Austria was a strong contributor in 1996, while Argentina showed consistent activity in subsequent years, suggesting potential for growth in that market.


## Query 10: Frequent Customers per Year

[![Image_10](./images/image_10.png)]

**Review** This query identifies customers who placed more than 3 orders in a single year, highlighting repeat buyers and loyal customers.
The results show that Save-a-lot Markets dominated the list with:

-1997 → 17 orders

-1998 → 11 orders

This demonstrates strong customer loyalty and frequent purchasing behavior. 
Such insights are valuable for customer relationship management, as frequent buyers like Save-a-lot Markets can be prioritized for loyalty programs, exclusive deals, or personalized marketing campaigns to further strengthen engagement and maximize revenue.


## Query 11: Top Products per Year

[![Image_11](./images/image_11.png)]

**Review** This query ranks products by total sales revenue per year and selects the top 3 products annually.
The results show that Chartreuse verte consistently topped the chart across three years:

-1996 → 108,000.00 (Rank 1)

-1997 → 175,500.00 (Rank 1)

-1998 → 121,500.00 (Rank 1)

This consistency highlights Chartreuse verte as a high-performing product with strong demand year after year. 
Such insights are valuable for strategic product planning, ensuring that top performers receive adequate marketing, inventory prioritization, and continued support to sustain their dominance in the market.


## Query 12: Customer Lifetime Value

 [![Image_12](./images/image_12.png)]

**Review** This query calculates the total lifetime revenue generated by each customer across all orders and ranks them accordingly.
The results show that:

- QUICK-Stop → 117,483.39 (Rank 1)

- Save-a-lot Markets → 115,673.39 (Rank 1)

These two customers consistently top the list, confirming their status as the highest lifetime value customers. 
Such insights are critical for customer retention strategies, as high‑value customers should be prioritized for loyalty programs, personalized offers, and premium services to ensure long‑term engagement and maximize profitability.

## Query 13: Employee Order Counts per Year

[![Image_13](./images/image_13.png)]

**Review** This query ranks employees by the number of orders handled per year, showing who processed the most orders annually.
The results highlight Peacock Margaret as the consistent top performer across three years:

- 1996 → 31 orders (Rank 1)

- 1997 → 81 orders (Rank 1)

- 1998 → 44 orders (Rank 1)

This demonstrates her strong contribution to order management and customer service. 
Such insights are useful for performance evaluation, recognizing employees who consistently manage high workloads, and identifying potential leaders within the team.


## Query 14: Orders Without Discounts

[![Image_14](./images/image_14.png)]

**Review**  This query retrieves all orders that had no discounts applied to any of their products.
The results show that 830 rows were returned, meaning a significant number of customers placed orders at full price.

This insight is useful for understanding discount utilization patterns. 
A high number of non‑discounted orders suggests strong demand and customer willingness to pay full price. It also helps evaluate the effectiveness of discount strategies, showing whether promotions are widely used or if customers often purchase without incentives. 
Such analysis can guide pricing strategies, promotional planning, and revenue optimization.


## Query 15: Product Sales Contribution

[![Image_15](./images/image_15.png)]

**Review**  This query calculates the number of orders and total sales value per product, ranking them by revenue contribution.
The results show:

- ProductID 38 → Cte de Blaye with 24 orders and 149,984.20 in total sales (top performer).

- ProductID 29 → Thüringer Rostbratwurst with 32 orders and 87,736.40 in total sales (second highest).

This analysis highlights which products generate the most revenue, regardless of order frequency.
Products like Cte de Blaye demonstrate high value per order, while Thüringer Rostbratwurst shows strong demand with more frequent purchases.
Such insights are crucial for inventory prioritization, marketing focus, and supplier negotiations to maximize profitability.

## Query 16: Average Days Between Customer Orders

[![Image_16](./images/image_16.png)]

**Review** This query calculates the average number of days between consecutive orders for each customer, providing insight into purchasing frequency.
The results show:

- La corne d'abondance → 36 days (least average gap)

- GROSELLA-Restaurante → 506 days (highest average gap)

This analysis highlights differences in customer buying behavior:

Customers like La corne d'abondance order frequently, suggesting strong ongoing demand and loyalty.

Customers like GROSELLA-Restaurante order infrequently, which may indicate seasonal demand, special events, or weaker engagement.

Such insights are valuable for customer segmentation, targeted marketing, and demand forecasting, helping the company tailor strategies to both frequent and occasional buyers.


## Query 17: High-Value Orders Above Company Average

[![Image_17](./images/image_17.png)]

**Review**  This query identifies orders whose total value exceeds the company’s average order value, spotlighting exceptionally high-value transactions.
The results show:

- OrderID 10865 → QUICK-Stop → 17,250.00 compared to the company average of 1,631.88.

- OrderID 11030 → Save-a-lot Markets → 16,321.90 also far above the average.

These standout orders demonstrate bulk or premium purchases that significantly impact revenue.
Such insights are useful for recognizing big-ticket customers, tailoring special offers, and ensuring operational readiness to handle large, high-value orders efficiently.

## Query 18: Employee-Customer Sales Contribution

[![Image_18](./images/image_18.png)]

**Review** This query examines the relationship between employees and customers, showing how many orders each employee handled for specific customers.
The results highlight Davolio Nancy as the top contributor:

- Rattlesnake Canyon Grocery → 36 orders

- Save-a-lot Markets → 25 orders

This demonstrates her strong engagement with key customers, suggesting she plays a pivotal role in maintaining high-value client relationships.
Such insights are useful for performance evaluation, customer relationship management, and resource allocation, ensuring that employees who manage critical accounts receive recognition and support to sustain their success.


## Query 19: Yearly Sales Growth Analysis

[![Image_19](./images/image_19.png)]

**Review**  This query calculates yearly total sales and compares each year’s performance with the previous year, showing both the absolute difference and percentage growth.
The results reveal:

- 1996 → 226,298.50 (baseline, no prior year comparison).

- 1997 → 658,388.75 vs 1996, showing a +190.9% growth.

- 1998 → 469,771.34 vs 1997, showing a -28.6% decline.

This analysis highlights significant fluctuations in yearly sales:

1997 was a boom year, with nearly triple the sales of 1996.

1998 saw a sharp contraction, suggesting market saturation, reduced demand, or external factors impacting sales.

Such insights are critical for trend analysis, forecasting, and strategic planning, helping the company understand growth cycles and prepare for downturns.

## Query 20: Product Revenue Categorization

[![Image_20](./images/image_20.png)]

**Review** This query categorizes products into High, Medium, and Low Revenue groups based on their total sales contribution.
The classification provides a clear segmentation of product performance:

- High Revenue products (above 50,000) are the company’s strongest drivers of profitability.

- Medium Revenue products (20,000–50,000) represent steady contributors with potential for growth.

- Low Revenue products (below 20,000) may require reevaluation, targeted marketing, or discontinuation if they underperform consistently.

This analysis is valuable for portfolio management, helping the company prioritize resources toward high-performing products while identifying opportunities to improve or streamline lower-performing ones.

---

## Tools and Technologies

This project was built using the following tools and technologies:

- **SQL (Structured Query Language)**  
  Used for querying relational databases, aggregating data, and performing analytical operations.

- **Relational Database (e.g., MySQL / SQL Server)**  
  The dataset is stored in a relational database with tables such as `Customers`, `Orders`, `OrderDetails`, `Employees`, `Products`, and `Shippers`.

- **Window Functions (RANK, DENSE_RANK, LAG)**  
  Applied for ranking, comparisons, and growth analysis.

- **Aggregate Functions (SUM, AVG, COUNT)**  
  Used to compute totals, averages, and counts for business insights.

- **Joins (INNER JOIN, CROSS JOIN)**  
  To combine data across multiple tables for comprehensive analysis.

- **Markdown Documentation**  
  For presenting queries, results, and reviews in a structured, readable format.

---

## Project Learnings

Key learnings from this project include:

1. **Customer Insights**  
   - Identification of high-value customers (QUICK-Stop, Save-a-lot Markets).  
   - Analysis of order frequency and loyalty patterns.

2. **Employee Performance**  
   - Ranking employees by order counts and sales contributions.  
   - Highlighting consistent top performers like Peacock Margaret and Davolio Nancy.

3. **Product Analysis**  
   - Recognizing top revenue-generating products (Cte de Blaye, Chartreuse verte).  
   - Categorizing products into high, medium, and low revenue groups.

4. **Shipper Efficiency**  
   - Comparing average delivery times across shippers.  
   - Identifying the fastest and slowest delivery services.

5. **Sales Trends**  
   - Yearly growth analysis showing boom (1997) and decline (1998).  
   - Regional sales distribution highlighting Austria and Argentina.

6. **Business Strategy Applications**  
   - Insights can guide marketing, inventory prioritization, loyalty programs, and operational improvements.

---

## Author

**Blessing-Chinaza**   
*Data Analyst | Medical Laboratory Scientist | Virtual Assistant*  

I specialize in leveraging data-driven insights to support business decision-making, applying analytical expertise from both healthcare and corporate domains. My multidisciplinary background allows me to combine technical proficiency with practical problem-solving skills, delivering value across diverse industries.  

**Contact:** [![LinkedIn](https://www.linkedin.com/in/blessing-nwokike/)] 
*For any inquiries regarding this project, please feel free to reach out. I am open to collaboration, networking, and professional opportunities.*

