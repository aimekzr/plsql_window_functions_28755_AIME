# Information About Me 🪄
My name is Kwizera Aime<br>
Stusent ID: 28755 <br>
This is my Database with pl/sql Assignment 1<br>

## 🌐 Socials
[![Discord](https://img.shields.io/badge/Discord-%237289DA.svg?logo=discord&logoColor=white)](https://discord.gg/https://discord.gg/yRSgqtf2) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/aime41_) 

# 💻 Tech Stack
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

[![](https://visitcount.itsvg.in/api?id=aimekzr&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
# plsql_window_functions_28755_AIME
Database with PL/SQL Assignment 1

## Step 1: Problem Definition

### Business Context
My business context is an online retail store company. The analysis focuses on the sales department of E-commerce industry.

### Data Challenge !🕸️
The online store keeps data about customers, products, prices, stock, delivery, and transactions. However, the business does not know exactly which products sell the most, which bring more income, or how sales change over time. Because of this, it is hard to manage stock or invertory, plan deliveries, and make good pricing decisions.

### Expected Outcome
The goal is to identify top-performing products, understand customer segments, and records all sales transactions in a database to analyze sales growth to support better business decisions.
 
 ## Step 2: Success Criteria

1. Top 5 products per region or quarter → RANK()**
- A goal to rank products by sales in each region and select the top  five consumed products based on total sales.

2. Running monthly sales totals → SUM() OVER()
- A goal to calculate cumulative sales to see how sales increase over time.

3. Month-over-month growth → LAG() / LEAD()
- A goal to compare sales of one month with the previous or next month to measure growth or decline.

4. Customer quartile segmentation → NTILE(4)
- A goal to divide customers into four (4) equal groups based on their total spending.

5. Three-month moving averages → AVG() OVER()
- A goal to calculate the average sales over the last three months to smooth short-term changes.

## Step 3: Database Schema Design
###  Three (3) related tables with primary and foreign keys.
- CREATE DATABASE onlinedbms;
1. CREATE TABLE customer (
    customerID SERIAL PRIMARY KEY,
    customerName VARCHAR(50) NOT NULL,
    region VARCHAR(50) NOT NULL
);
2. CREATE TABLE products (
    productID SERIAL PRIMARY KEY,
    productName VARCHAR(50) NOT NULL,
    price DECIMAL(10,2) NOT NULL CHECK (price>0)
);
3. CREATE TABLE sales (
    salesID SERIAL PRIMARY KEY,
    customerID INT,
    productID INT,
    salesDate DATE,
    quantity INT,
    totalAmount NUMERIC(10,2) NOT NULL CHECK(totalAmount>0),
    FOREIGN KEY (customerID) REFERENCES customers(customerID),
    FOREIGN KEY (productID) REFERENCES products(productID)
);

### An ER diagram
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/e410b088-b366-44c9-bdf5-267622452891" />

## Step 4 & 5: SQL Screenshots with Explanations
 ### 1. Part A. SQL JOINs Implementation<br> 
#### INNER JOIN SQL Command <br>
  ```sql
SELECT s.salesid, s.salesdate, c.name AS customer_name, p.productname, s.quantity, s.totalamount
FROM sales s
INNER JOIN customer c ON s.customerid = c.customerid
INNER JOIN products p ON s.productid = p.productid;
``` 

 **INNER JOIN Screenshot** <br> *"This INNER JOIN displays all completed sales with same customer & product details. It helps to see which customers bought products & how much money each sale generated."* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/aee051da-7550-481a-8b73-38d56f738a47" /><br>
#### LEFT JOIN SQL Command <br>
```sql
SELECT c.customerid, c.name, c.region
FROM customer c
LEFT JOIN sales s ON c.customerid = s.customerid
WHERE s.salesid IS NULL;
```

**LEFT JOIN Screenshot** <br> *"This LEFT JOIN identifies customers who have never made any purchases. In this dataset, all customers have bought products, so no inactive customers were found."* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/d5a78cd3-3ed5-4231-87af-19d828a25e87" /> <br>
#### RIGHT JOIN SQL Command <br>
```sql
SELECT p.productid, p.productname
FROM sales s
RIGHT JOIN products p ON s.productid = p.productid
WHERE s.salesid IS NULL;
```

**RIGHT JOIN Screenshot**<br>  *"This RIGHT JOIN finds products that have not been sold. In this dataset, every product has sales, showing that all products are active."* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/9b87b4a0-debc-4893-a509-89827f55b8f0" /> <br>
#### FULL JOIN SQL Command <br>
```sql
SELECT c.name, p.productname
FROM customer c
FULL OUTER JOIN products p
ON c.customerid = p.productid;
```

**FULL OUTER JOIN screenshot**<br>  *"This FULL OUTER JOIN compares customers and products, including unmatched records. It helps identify any customers or products without relationships."* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/2ee1276e-7151-49e1-a468-d35b8ce7e801" /><br>
#### SELF JOIN Command <br>
```sql
SELECT c1.name AS customer1, c2.name AS customer2, c1.region
FROM customer c1
JOIN customer c2
ON c1.region = c2.region
AND c1.customerid <> c2.customerid;
```

**SELF JOIN Screenshot**<br>  *"This SELF JOIN compares customers in the same region. It helps the business understand which customers are located in the same areas."* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/c051ac73-bf52-4860-8cea-cc4966fa8ac9" /><br>
### 2. Part B. Window Functions Implementation<br>
#### RANKING FUNCTION Command
```sql
SELECT p.productname, SUM(s.totalamount) AS total_sales,
    ROW_NUMBER() OVER (ORDER BY SUM(s.totalamount) DESC) AS row_num,
    RANK() OVER (ORDER BY SUM(s.totalamount) DESC) AS rank,
    DENSE_RANK() OVER (ORDER BY SUM(s.totalamount) DESC) AS dense_rank,
    PERCENT_RANK() OVER (ORDER BY SUM(s.totalamount)) AS percent_rank
FROM sales s
JOIN products p ON s.productid = p.productid
GROUP BY p.productname;
```

**Ranking Functions Screenshot**<br>  *"This query ranks products based on total revenue. It helps the business identify top-performing products and compare their relative performance"* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/ed242827-ae69-4661-8d12-8ea52007ef15" /><br>
#### AGGREGATE WINDOW FUNCTION Command
```sql

```
**Aggregate Window Functions running_total.png**<br>  .* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/16f3b2f6-ccc6-4afa-a3ef-70e797099f14" /><br>
#### NAVIGATION FUNCTION Command
```sql
SELECT salesdate, totalamount,
    LAG(totalamount) OVER (ORDER BY salesdate) AS previous_sales,
    totalamount - LAG(totalamount) OVER (ORDER BY salesdate) AS sales_change
FROM sales;
```

**Navigation Functions Screenshot**<br> *"This query compares current sales with previous sales. It helps identify increases or decreases in revenue between periods."* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/95887173-cc86-43c5-b70b-4aa69d4a625a" /><br>
**Distribution Functions ntile.png**<br> *Divides rows into equal groups and numbers them.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/354b7511-72ba-4127-b1a9-a939a574a0b6" /><br>
## Step 6: Key Insights

 - A few products bring most of the sales revenue.<br>
 - High-value customers spend much more than other customers.<br>
 - Some products have no sales and may need promotion or replacement.<br>
 - Monthly sales go up and down, showing times when marketing should be improved.<br>
 - Running totals and averages help show the overall sales trend.<br>

## References 🤖
Class Materials<br>
- DBMS notes by Temitope for join commands. <br>
- Lecture notes. <br>

Online Sources <br>
 - How to Creating and highlighting code blocks SQL commands in README.md.
   (https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks)
 - Window functions. (https://www.postgresql.org/docs/current/functions-window.html) <br>
 - Specific syntax and Key symbols Github Docs. <br>(https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax>)
 
Video tutorials <br>
 - Youtube tutorials. (https://www.youtube.com/shorts/d87syC9_3Rk?feature=share) for github repository editing & look professional <br>
 - Youtube tutorials. <https://youtu.be/UfecjNcR4rQ> for Create database and tables using postgresql <br>
  
Business Idea <br>
 - Business Idea is mine. <br>
# Integrity Statement <br>
" All sources were properly cited. Implementations and analysis represent original work. No AI-
generated content was copied without attribution or adaptation."

