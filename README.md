# Pizza

Summary of the problem statement and the solutions for the pizza dataset analysis:

### Problem Statement

This analysis aims to gain insights from a pizza sales dataset through various SQL queries. The objective is to answer basic, intermediate, and advanced questions related to pizza orders, revenue, and distribution patterns. The analysis is divided into three levels of complexity:

**Basic:**
1. Retrieve the total number of orders placed.
2. Calculate the total revenue generated from pizza sales.
3. Identify the highest-priced pizza.
4. Identify the most common pizza size ordered.
5. List the top 5 most ordered pizza types along with their quantities.

**Intermediate:**
1. Find the total quantity of each pizza category ordered by joining necessary tables.
2. Determine the distribution of orders by the hour of the day.
3. Find the category-wise distribution of pizzas by joining relevant tables.
4. Group the orders by date and calculate the average number of pizzas ordered per day.
5. Determine the top 3 most ordered pizza types based on revenue.

**Advanced:**
1. Calculate the percentage contribution of each pizza type to total revenue.
2. Analyze the cumulative revenue generated over time.
3. Determine the top 3 most ordered pizza types based on revenue for each pizza category.

### Solution Summary

**Basic:**
1. **Total Orders:** Use `COUNT(*)` on the orders table.
2. **Total Revenue:** Use `SUM(price)` after joining orders and pizza prices tables.
3. **Highest-Priced Pizza:** Use `ORDER BY price DESC LIMIT 1` on the pizzas table.
4. **Most Common Pizza Size:** Use `GROUP BY size ORDER BY COUNT(*) DESC LIMIT 1`.
5. **Top 5 Most Ordered Pizzas:** Use `GROUP BY pizza_type ORDER BY COUNT(*) DESC LIMIT 5`.

**Intermediate:**
1. **Total Quantity by Category:** Join orders with pizza and category tables and use `SUM(quantity) GROUP BY category`.
2. **Order Distribution by Hour:** Extract hour from the order time and `GROUP BY hour ORDER BY hour`.
3. **Category-wise Distribution:** Similar to the total quantity by category but add a count for distribution.
4. **Average Pizzas per Day:** `GROUP BY date` and use `AVG(quantity)`.
5. **Top 3 Pizzas by Revenue:** Join orders with pizza prices, group by pizza type, sum revenue, and order by total revenue DESC LIMIT 3.

**Advanced:**
1. **Percentage Contribution to Revenue:** Calculate each pizza type's revenue, divide by total revenue, and multiply by 100.
2. **Cumulative Revenue Over Time:** Use a running total with `SUM(revenue) OVER (ORDER BY date)`.
3. **Top 3 Pizzas by Revenue per Category:** Join relevant tables, group by category and pizza type, sum revenue, and order by category and total revenue DESC LIMIT 3 per category.

This analysis will help in understanding the sales performance, customer preferences, and revenue patterns for the pizza business.
