# ☕ Coffee Shop Sales — SQL + Power BI

An end-to-end **data analytics project** where I used **SQL (MySQL)** for data cleaning, KPI calculations, and trend analysis, and then built an **interactive Power BI dashboard** for visualization.

---

## 🔧 Project Workflow

**1. Data Preparation (SQL)**
- Cleaned raw dataset (`Coffee Shop Sales.xlsx`) and fixed issues:
  - Converted `transaction_date` & `transaction_time` into correct formats.
  - Renamed inconsistent column names (e.g., `transaction_id`).
- Created SQL queries for:
  - **KPIs:** Total Sales, Total Orders, Total Quantity Sold.
  - **MoM Growth:** Month-over-Month % change in Sales, Orders, and Quantity.
  - **Breakdowns:** By Store, Weekday vs Weekend, Product Category, Product Type.
  - **Trends:** Daily sales, sales by hour/day, and comparison against average.

**2. Dashboard (Power BI)**
- Imported cleaned dataset into **Power BI Desktop**.
- Created measures and visuals:
  - **Cards:** Total Sales ($76K), Orders (16K), Quantity (23K).
  - **Line/Bar Charts:** Daily sales trend with MoM growth.
  - **Donut/Bar Charts:** Sales by Store, Product Category, Weekday vs Weekend.
  - **Heatmap:** Sales by Day | Hours.
- Added slicers (Month filter) for interactivity.

---

## 📊 Dashboard Preview

Main Dashboard  
<img src="images/dashboard-main.png" alt="Coffee Shop Sales Dashboard" width="850"/>

Detail View  
<img src="images/dashboard-detail.png" alt="Coffee Shop Sales Dashboard 2" width="850"/>

---

## 📁 Project Structure
```
coffee-shop-sales-sql-powerbi/
├─ data/
│  └─ Coffee Shop Sales.xlsx
├─ images/
│  ├─ dashboard-main.png
│  └─ dashboard-detail.png
├─ sql/
│  ├─ queries.sql
│  └─ MY SQL Queries Project.docx
├─ powerbi/
│  └─ README.md  (add your .pbix here)
├─ .gitignore
└─ README.md
```

---

## ▶️ How to Reproduce

1. **SQL Analysis**
   - Load `Coffee Shop Sales.xlsx` into **MySQL** as `coffee_shop_sales`.
   - Run the scripts from `sql/queries.sql` to clean data and compute KPIs/trends.

2. **Power BI Dashboard**
   - Import the cleaned dataset (`Excel` or `MySQL connection`).
   - Recreate visuals as shown in `images/`.
   - Save your report (`.pbix`) into `powerbi/`.

---

## 🧮 Sample SQL Queries

**Total Sales (for May)**  
```sql
SELECT ROUND(SUM(unit_price * transaction_qty)) AS Total_Sales
FROM coffee_shop_sales
WHERE MONTH(transaction_date) = 5;
```

**Weekday vs Weekend Sales**  
```sql
SELECT 
  CASE WHEN DAYOFWEEK(transaction_date) IN (1,7) THEN 'Weekend' ELSE 'Weekday' END AS DayType,
  ROUND(SUM(unit_price * transaction_qty), 2) AS Total_Sales
FROM coffee_shop_sales
WHERE MONTH(transaction_date) = 5
GROUP BY DayType;
```

**Sales by Store Location**  
```sql
SELECT store_location, SUM(unit_price * transaction_qty) AS Total_Sales
FROM coffee_shop_sales
WHERE MONTH(transaction_date) = 5
GROUP BY store_location
ORDER BY Total_Sales DESC;
```

---

## 🛠 Tools & Tech
- **SQL (MySQL)** → Data cleaning & KPI queries  
- **Excel** → Raw dataset  
- **Power BI Desktop** → Dashboard & visualization  
