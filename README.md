#  About Me 🪄:
My name is Kwizera Aime<br>This is my Database with pl/sql Assignment project<br>Welcome everybody to collaborate!🕸️


## 🌐 Socials:
[![Discord](https://img.shields.io/badge/Discord-%237289DA.svg?logo=discord&logoColor=white)](https://discord.gg/https://discord.gg/yRSgqtf2) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/aime41_) 

# 💻 Tech Stack:
![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=for-the-badge&logo=c%2B%2B&logoColor=white) ![C](https://img.shields.io/badge/c-%2300599C.svg?style=for-the-badge&logo=c&logoColor=white) ![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![Apache](https://img.shields.io/badge/apache-%23D42029.svg?style=for-the-badge&logo=apache&logoColor=white) ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) ![Adobe](https://img.shields.io/badge/adobe-%23FF0000.svg?style=for-the-badge&logo=adobe&logoColor=white) ![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)

---
[![](https://visitcount.itsvg.in/api?id=aimekzr&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->
# plsql_window_functions_28755_AIME
New Database with PL/SQL Projects

## Step 1: Problem Definition

### Business Context
- My business context is an online retail store company. The analysis focuses on the sales department of E-commerce industry.

### Data Challenge
- The online store keeps data about customers, products, prices, stock, delivery, and transactions. However, the business does not know exactly which products sell the most, which bring more income, or how sales change over time. Because of this, it is hard to manage stock or invertory, plan deliveries, and make good pricing decisions.

### Expected Outcome
- The goal is to identify top-performing products, understand customer segments, and records all sales transactions in a database to analyze sales growth to support better business decisions.
 
 ## Step 2: Success Criteria

1. Top 5 products per region or quarter → RANK()
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
## SQL Screenshots with Explanations
 -- inner_join.png
 -- left_join.png
 -- right_join.png
 -- full_join.png
 -- self_join.png
 -- rank.png
 -- running_total.png
 -- lag.png
 -- ntile.png
