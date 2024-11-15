# Simple Shop Database

This repository contains SQL Server scripts for creating, managing, and querying a **Shop Database**. The project demonstrates essential SQL Server skills, including table creation, relationships, and querying.

---

## 📋 Database Overview

### Tables
1. **Customers**: Contains customer details.
   - Columns: `cutomer_id`, `customer_name`, `email`, `registration_date`.
2. **Products**: Stores product information.
   - Columns: `product_id`, `product_name`, `description` , `price`.
3. **Orders**: Tracks customer orders.
   - Columns: `order_id`, `customer_id`, `order_date` , `order_amount` , `product_id`.

### Relationships
- **Customers ↔ Orders**: One customer can have many orders.
- **Products ↔ Orders**: One product can appear in many orders.

---

## ✨ Features
- **Database Creation**: Using `CREATE DATABASE` and `CREATE TABLE`.
- **Data Management**: Includes scripts for inserting and managing sample data.
- **Joins and Relationships**: Queries demonstrate `INNER JOIN` and `LEFT JOIN`.
- **Aggregations**: Examples using `SUM`, `COUNT`, and `GROUP BY`.
- **Date Functions**: Queries with `GETDATE()` and `DATEADD()` for filtering recent records.

---

## 🛠️ Example Query
Find products with no orders in the last 6 months:
```sql
SELECT
  p.product_id, p.product_name
FROM
  products p
LEFT JOIN
  orders o
ON
  p.product_id = o.product_id
AND
  o.order_date >= DATEADD(MONTH, -6, GETDATE())
WHERE
  o.order_id IS NULL;
