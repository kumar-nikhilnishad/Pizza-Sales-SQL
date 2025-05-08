## 🍕 Pizza Sales SQL Analysis
This project involves analyzing sales data from a fictional pizza restaurant using PostgreSQL. It demonstrates how SQL can be used to extract valuable business insights such as revenue trends, product performance, and customer behavior.

## 📁 Dataset
The dataset is made up of four CSV files:

•	orders.csv: Order timestamps

•	order_details.csv: Items ordered in each transaction

•	pizzas.csv: Pizza IDs and prices

•	pizza_types.csv: Pizza names, categories, and ingredients

## 🧰 Tools & Technologies

•	PostgreSQL

•	SQL (Joins, Aggregation, Subqueries, CTEs)

•	Excel (for raw data inspection)

## 🔍 Key Analyses Performed
### 1.	Monthly Revenue Trend
Identify revenue fluctuations across months to understand seasonality and sales growth.

### 2.	Top 5 Best-Selling Pizza Types
Find the most popular pizzas based on quantity sold.

### 3.	Peak Order Hours
Analyze the busiest hours of the day for operational planning.

### 4.	Ingredient Demand Analysis
Extract and rank the most frequently used ingredients.

### 5.	Daily Order Volume
Track how order frequency varies across days.

### 6.	Revenue Contribution by Pizza Type
Calculate the percentage of total revenue contributed by each pizza type.


## 📊 Sample SQL Query



SELECT 

    pt.name AS pizza_type,
    SUM(od.quantity * p.price) AS revenue,
    ROUND(
        (SUM(od.quantity * p.price) * 100.0 /
         (SELECT SUM(od2.quantity * p2.price)
          FROM order_details od2
          JOIN pizzas p2 ON od2.pizza_id = p2.pizza_id)
        )::numeric, 
        2
    ) AS revenue_percentage

FROM pizza_types pt

JOIN pizzas p 

ON pt.pizza_type_id = p.pizza_type_id

JOIN order_details od
 ON od.pizza_id = p.pizza_id

GROUP BY pt.name

ORDER BY revenue_percentage DESC;

## 📈 Insights
•	The Classic Deluxe Pizza and The Barbecue Chicken Pizza are top-selling pizzas.

•	Most orders occur between 6 PM and 8 PM.

•	Garlic and tomato are the most commonly used ingredients.

•	Some pizza types generate more revenue despite fewer sales due to pricing.


👤 Author
[NIKHIL KUMAR]
Data Analyst | SQL Enthusiast
https://www.linkedin.com/in/nikhil-kumar-3982a9348/

💬 Always happy to connect with fellow data enthusiasts and professionals!
