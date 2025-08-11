# Northwind Sample – SQL Server Project

This repository contains a *Northwind-style* sample database for Microsoft SQL Server.  
It includes tables for categories, customers, employees, orders, products, shippers, and suppliers, along with sample data to help you test queries and learn SQL.

---

## Requirements
- Microsoft SQL Server (Express or newer)
- SQL Server Management Studio (SSMS) or another SQL client

---

## Installation

1. *Create the database:*
```sql

CREATE DATABASE NorthwindMini;
GO
USE NorthwindMini;
GO


2.	Run the script:

	•	Open northwind_sample.sql in SSMS.
	•	Click Execute.
	•	You should see Query executed successfully.

Schema Overview
customers → orders → order_details
products  → categories
products  → suppliers
orders    → shippers
employees → orders
	•	Primary keys and foreign keys are included for data integrity.
	•	Indexes are added to improve query performance.


Example Queries
Top 5 Customers by Order Count
SELECT c.CustomerName, COUNT(*) AS OrderCount
FROM orders o
JOIN customers c ON c.CustomerID = o.CustomerID
GROUP BY c.CustomerName
ORDER BY OrderCount DESC;


Products by Category
SELECT cat.CategoryName, COUNT(*) AS ProductCount
FROM products p
JOIN categories cat ON cat.CategoryID = p.CategoryID
GROUP BY cat.CategoryName;


Resetting the Database
If you want to reload from scratch:
USE master;
GO
DROP DATABASE IF EXISTS NorthwindMini;
GO
CREATE DATABASE NorthwindMini;
GO
USE NorthwindMini;
GO
-- Run northwind_sample.sql again
