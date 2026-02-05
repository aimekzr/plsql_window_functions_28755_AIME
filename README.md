# Information About Me 🪄:
My name is Kwizera Aime<br>
Stusent ID: 28755 <br>
This is my Database with pl/sql Assignment 1<br>Welcome everybody to collaborate!🕸️

## 🌐 Socials:
[![Discord](https://img.shields.io/badge/Discord-%237289DA.svg?logo=discord&logoColor=white)](https://discord.gg/https://discord.gg/yRSgqtf2) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/aime41_) 

# 💻 Tech Stack:
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
---
[![](https://visitcount.itsvg.in/api?id=aimekzr&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
# plsql_window_functions_28755_AIME
New Database with PL/SQL Projects

## Step 1: Problem Definition

### Business Context
My business context is an online retail store company. The analysis focuses on the sales department of E-commerce industry.

### Data Challenge
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
 1. Part A. SQL JOINs Implementation<br>
**INNER JOIN inner_join.png** <br>  *Shows only matching rows from both tables.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/aee051da-7550-481a-8b73-38d56f738a47" /><br>
**LEFT JOIN left_join.png** <br> *Shows all rows from the left table and matching rows from the right.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/a3b07cac-e8ad-4cd9-be97-7f48f0646377" /><br>
**RIGHT JOIN right_join.png**<br>  *Shows all rows from the right table and matching rows from the left.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/32a4a4e5-e904-4ca3-a237-ffaa4e7a3977" /><br>
**FULL OUTER JOIN full_join.png**<br>  *Shows all rows from both tables, matching where possible.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/f3bba839-9a72-44d0-afcf-7a0c5ccb8b3a" /><br>
**SELF JOIN self_join.png**<br>  *Shows a table joining with itself.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/382fd78f-57c2-4482-9d26-2f7fa660d058" /><br>
 2. Part B. Window Functions Implementation<br>
**Ranking Functions rank.png**<br>  *Shows ranking of rows in a table.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/ed242827-ae69-4661-8d12-8ea52007ef15" /><br>
**Aggregate Window Functions running_total.png**<br>  *Shows cumulative total of values.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/16f3b2f6-ccc6-4afa-a3ef-70e797099f14" /><br>
**Navigation Functions lag.png**<br> *Shows previous row value for comparison.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/81e0576e-8003-4174-b94c-fe52efcf309c" /><br>
**Distribution Functions ntile.png**<br> *Divides rows into equal groups and numbers them.* <br>
<img width="500" height="200" alt="Image" src="https://github.com/user-attachments/assets/354b7511-72ba-4127-b1a9-a939a574a0b6" /><br>
##  Key Insights

 - A few products bring most of the sales revenue.<br>
 - High-value customers spend much more than other customers.<br>
 - Some products have no sales and may need promotion or replacement.<br>
 - Monthly sales go up and down, showing times when marketing should be improved.<br>
 - Running totals and averages help show the overall sales trend.<br>

## References 🤖
Class Materials<br>
- DBMS notes by Temitope for join commands. <br>
- Lecture notes <br>

Online Sources <br>
 - Window functions (https://www.postgresql.org/docs/current/functions-window.html) <br>
  
Video tutorials <br>
 - Youtube tutorials (https://www.youtube.com/shorts/d87syC9_3Rk?feature=share) for github repository editing & look professional <br>
 - Youtube tutorials <https://youtu.be/UfecjNcR4rQ> for Create database and tables using postgresql <br>
  
IDEA <br>
 - Business Idea is mine. <br>
# Integrity <br>
" All sources were properly cited. Implementations and analysis represent original work. No AI-
generated content was copied without attribution or adaptation."

