# 🍕 Data Analysis Portfolio Project – Pizza Sales Dashboard

### By: Dimple Sharma

## 📌 Project Overview

This project analyzes pizza sales data using **MySQL** and **Power BI** to gain key insights into business performance. The goal is to uncover trends in revenue, order behavior, product performance, and seasonal patterns by calculating and visualizing key performance indicators (KPIs).

---

## 🛠 Tools & Technologies Used

- **MS Office / Excel** – Data review  
- **MySQL Server 19.0** – Database management and SQL querying  
- **Power BI** – Data visualization and dashboard creation

---

## 🧱 Project Structure

### 🔹 Part 1: MySQL Server

- Data Import  
- Database Creation  
- Writing SQL Queries  
- Building Report-ready Tables

### 🔹 Part 2: Power BI

- Connecting to MySQL  
- Data Cleaning & Preprocessing  
- Visualizations using DAX & Charts

---

## 📊 Key Metrics & Queries

### KPI Queries

- **Total Revenue**  
```sql
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
```

- **Average Order Value**  
```sql
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order FROM pizza_sales;
```

- **Total Pizzas Sold**  
```sql
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;
```

- **Average Pizzas per Order**  
```sql
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Avg_Pizzas_per_order FROM pizza_sales;
```

---

### 📈 Trend Analysis Queries

- **Daily Order Trend**  
```sql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders FROM pizza_sales GROUP BY DATENAME(DW, order_date);
```

- **Monthly Order Trend**  
```sql
SELECT DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders FROM pizza_sales GROUP BY DATENAME(MONTH, order_date);
```

---

### 🍕 Sales Performance Queries

- **% of Sales by Pizza Category**  
```sql
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT FROM pizza_sales GROUP BY pizza_category;
```

- **% of Sales by Pizza Size**  
```sql
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT FROM pizza_sales GROUP BY pizza_size ORDER BY pizza_size;
```

- **Pizzas Sold by Category (Feb)**  
```sql
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold FROM pizza_sales WHERE MONTH(order_date) = 2 GROUP BY pizza_category ORDER BY Total_Quantity_Sold DESC;
```

- **Top 5 Pizzas by Revenue**  
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Revenue DESC;
```

- **Bottom 5 Pizzas by Revenue**  
```sql
SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Revenue ASC;
```

---

## 📊 Power BI Dashboards

- Total Revenue & Order Trends  
- Monthly & Daily Sales Overview  
- Category & Size-wise Revenue Breakdown  
- Top vs Bottom Performing Pizza Products  
- Custom KPIs with DAX Measures

---

## ✅ Conclusion

By combining **SQL querying** and **interactive Power BI dashboards**, this project delivers actionable insights into pizza sales. It highlights:

- Strong product categories and sizes  
- Peak sales days and months  
- High-performing pizzas  
- Areas for product or marketing improvement

This hands-on experience has improved my skills in **data extraction**, **SQL**, **data modeling**, and **business intelligence visualization**.
