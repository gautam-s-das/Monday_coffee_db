# ☕ Monday Coffee — India Expansion Analysis

> **Identifying the top 3 cities in India for new Monday Coffee store locations** based on consumer demand, sales performance, and market potential — using SQL-driven analysis of online sales data from January 2023 to December 2023.

---

## 📌 Project Overview

Monday Coffee has been selling its products online since January 2023. This project analyses transactional sales data to answer key business questions and produce data-backed recommendations for physical store expansion across major Indian cities.

---

## 🎯 Objective

Analyse sales data and recommend the **top 3 Indian cities** for opening new coffee shop locations based on:
- Consumer demand and estimated coffee-drinking population
- Revenue performance and sales growth
- Rent-to-revenue efficiency
- Customer base size and engagement

---

## 📁 Project Structure

```
monday-coffee-expansion/
│
├── datasets/
│   ├── city.csv               # City demographics and rent data
│   ├── customers.csv          # Customer records with city mapping
│   ├── products.csv           # Coffee product catalogue and pricing
│   └── sales.csv              # Transactional sales data (Jan–Dec 2023)
│
├── queries/
│   ├── 01_coffee_consumers.sql
│   ├── 02_total_revenue_q4.sql
│   ├── 03_sales_count_by_product.sql
│   ├── 04_avg_sales_per_city.sql
│   ├── 05_city_population_consumers.sql
│   ├── 06_top_products_by_city.sql
│   ├── 07_customer_segmentation.sql
│   ├── 08_avg_sale_vs_rent.sql
│   ├── 09_monthly_sales_growth.sql
│   └── 10_market_potential_analysis.sql
│
├── dashboard/
│   └── monday_coffee_dashboard.html   # Interactive expansion dashboard
│
└── README.md
```

---

## ❓ Key Business Questions

| # | Question |
|---|----------|
| 1 | How many people in each city are estimated to consume coffee (25% of population)? |
| 2 | What is the total revenue from coffee sales in Q4 2023? |
| 3 | How many units of each coffee product have been sold? |
| 4 | What is the average sales amount per customer in each city? |
| 5 | What are the city populations and estimated coffee consumer counts? |
| 6 | What are the top 3 selling products in each city by sales volume? |
| 7 | How many unique customers per city have purchased coffee products? |
| 8 | What is the average sale per customer vs average rent per customer for each city? |
| 9 | What is the monthly sales growth rate across the year? |
| 10 | Which are the top 3 cities by market potential (sales, rent, customers, consumers)? |

---

## 🗃️ Dataset Schema

### `city`
| Column | Type | Description |
|--------|------|-------------|
| city_id | INT | Unique city identifier |
| city_name | VARCHAR | Name of the city |
| population | BIGINT | Total city population |
| estimated_rent | DECIMAL | Average monthly rent (₹) |
| city_rank | INT | Tier ranking |

### `customers`
| Column | Type | Description |
|--------|------|-------------|
| customer_id | INT | Unique customer identifier |
| customer_name | VARCHAR | Customer full name |
| city_id | INT | FK → city.city_id |

### `products`
| Column | Type | Description |
|--------|------|-------------|
| product_id | INT | Unique product identifier |
| product_name | VARCHAR | Coffee product name |
| price | DECIMAL | Unit price (₹) |

### `sales`
| Column | Type | Description |
|--------|------|-------------|
| sale_id | INT | Unique sale identifier |
| sale_date | DATE | Date of transaction |
| product_id | INT | FK → products.product_id |
| customer_id | INT | FK → customers.customer_id |
| total | DECIMAL | Transaction total (₹) |
| rating | INT | Customer rating (1–5) |

---

## 📊 Key Findings

### Total Revenue — Q4 2023
**₹24,89,820** in total revenue across all 6 cities in the last quarter of 2023.

### Top Products by Units Sold
1. Cold Brew Pack
2. Latte
3. Espresso

### Average Sale vs Rent per Customer

| City | Avg Sale/Customer | Avg Rent/Customer |
|------|:-----------------:|:-----------------:|
| Pune | ₹7,234 | ₹294 |
| Delhi | ₹4,850 | ₹330 |
| Jaipur | ₹11,600 | ₹156 |
| Bengaluru | ₹8,640 | ₹400 |
| Mumbai | ₹9,150 | ₹450 |
| Chennai | ₹7,780 | ₹350 |

---

## ✅ Recommendations

### 🥇 City 1 — Pune
- Highest total revenue across all cities
- Very low average rent per customer (₹294)
- Strong average sales per customer

### 🥈 City 2 — Delhi
- Largest estimated coffee consumer base at **7.7 million**
- Highest total customer count (**68 unique buyers**)
- Average rent per customer is ₹330 — comfortably under the ₹500 threshold

### 🥉 City 3 — Jaipur
- Most unique customers in the dataset (**69 buyers**)
- Lowest average rent per customer at just **₹156**
- Strong average sales per customer at **₹11,600**

---

## 🛠️ Tools & Technologies

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-005C84?style=for-the-badge&logo=sqlite&logoColor=white)

- **Database:** PostgreSQL
- **Language:** SQL
- **Dashboard:** HTML / Chart.js

---

## 🚀 Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/monday-coffee-expansion.git
   cd monday-coffee-expansion
   ```

2. **Set up the database**
   ```sql
   CREATE DATABASE monday_coffee;
   ```

3. **Import the datasets**
   ```bash
   psql -d monday_coffee -f datasets/schema.sql
   psql -d monday_coffee -c "\COPY city FROM 'datasets/city.csv' CSV HEADER"
   psql -d monday_coffee -c "\COPY customers FROM 'datasets/customers.csv' CSV HEADER"
   psql -d monday_coffee -c "\COPY products FROM 'datasets/products.csv' CSV HEADER"
   psql -d monday_coffee -c "\COPY sales FROM 'datasets/sales.csv' CSV HEADER"
   ```

4. **Run the analysis queries**
   ```bash
   psql -d monday_coffee -f queries/10_market_potential_analysis.sql
   ```

---

## 📬 Contact

**Author:** [Your Name](https://github.com/your-username)  
**LinkedIn:** [linkedin.com/in/your-profile](https://linkedin.com/in/your-profile)

---

> *This project was created for portfolio and learning purposes. All data is used strictly for analytical demonstrations.*
