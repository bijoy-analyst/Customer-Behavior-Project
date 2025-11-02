
# 🛍️ Customer Behavior Analysis

## 📊 Project Overview
This project explores **customer purchasing behavior** using **SQL, Power BI, and Python**.  
The goal is to analyze customer demographics, spending patterns, discounts, and loyalty trends to uncover actionable insights that can help improve marketing, pricing, and customer retention strategies.

---

## 🧩 Tech Stack
- **SQL** → For data querying and cleaning  
- **Power BI** → For interactive dashboards and data visualization  
- **Python (Jupyter Notebook)** → For statistical analysis and data preprocessing  

---

## 📁 Project Files
| File Name | Description |
|------------|-------------|
| `customer_shoping.sql` | SQL queries for analyzing customer data |
| `Customer_behavior_Analysis.ipynb` | Python notebook for data exploration and analysis |
| `customer_behavior.pbix` | Power BI dashboard visualizing key insights |

---

## 🧠 Key SQL Insights

### 1️⃣ Revenue by Gender
```sql
SELECT gender, SUM(purchase_amount) AS revenue
FROM customer
GROUP BY gender;
```

### 2️⃣ Discount Users with Above-Average Spending
```sql
SELECT customer_id, purchase_amount 
FROM customer 
WHERE discount_applied = 'Yes' 
  AND purchase_amount >= (SELECT AVG(purchase_amount) FROM customer);
```

### 3️⃣ Top 5 Products by Average Rating
```sql
SELECT item_purchased, ROUND(AVG(review_rating::numeric),2) AS "Average Product Rating"
FROM customer
GROUP BY item_purchased
ORDER BY AVG(review_rating) DESC
LIMIT 5;
```

### 4️⃣ Purchase Comparison: Standard vs Express Shipping
```sql
SELECT shipping_type, ROUND(AVG(purchase_amount),2)
FROM customer
WHERE shipping_type IN ('Standard','Express')
GROUP BY shipping_type;
```

### 5️⃣ Subscribers vs Non-Subscribers Spending
```sql
SELECT subscription_status,
       COUNT(customer_id) AS total_customers,
       ROUND(AVG(purchase_amount),2) AS avg_spend,
       ROUND(SUM(purchase_amount),2) AS total_revenue
FROM customer
GROUP BY subscription_status
ORDER BY total_revenue, avg_spend DESC;
```

---

## 📈 Power BI Dashboard Highlights
- Gender-wise Revenue Distribution  
- Discount Impact on Spending  
- Subscription vs Non-Subscription Insights  
- Product Ratings & Top Categories  
- Age Group Revenue Contribution  

---

## 🧩 Customer Segmentation Logic
Customers are segmented based on previous purchases:
| Segment | Condition | Meaning |
|----------|------------|----------|
| **New** | 1 Purchase | First-time customer |
| **Returning** | 2–10 Purchases | Repeat buyer |
| **Loyal** | >10 Purchases | Long-term customer |

---

## 📊 Example Visualization Ideas
- Pie chart for **Gender-based Revenue**
- Bar chart for **Top 5 Products by Rating**
- Line chart for **Revenue Trend by Age Group**
- KPI cards for **Total Revenue** and **Average Purchase Amount**

---

## 🚀 How to Use
1. Run the SQL queries from `customer_shoping.sql` on your SQL database.  
2. Open the Power BI file `customer_behavior.pbix` to explore dashboards.  
3. Use `Customer_behavior_Analysis.ipynb` for deeper statistical analysis or model building.

---

## 🏁 Conclusion
This project demonstrates how to integrate **SQL, Power BI, and Python** to analyze and visualize customer behavior effectively.  
It provides insights into how **gender, subscription status, discounts, and loyalty** influence overall sales performance.

---

## 🧑‍💻 Author
**Bijoy Hossen**  
_Data Analyst | SQL | Power BI | Python | Excel_  

🌐 Connect with me on [LinkedIn](https://www.linkedin.com)  

