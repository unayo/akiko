---
title: PostgreSQL 基礎教學 | 建立表單、新增資料、刪除資料、查詢資料
description: PostgreSQL 是一種功能強大的資料庫管理系統。本篇文章將帶你快速學會如何建立資料表、新增資料、查詢資料與刪除資料，入門資料庫操作。
categories:
- [PostgreSQL, 資料庫教學]
- [SQL 指令, 基礎教學]
tags:
- [PostgreSQL]
- [SQL 教學, 資料庫操作, 建立表單]

date: 2024-11-20
---

PostgreSQL 是一款功能強大的開源關聯式資料庫管理系統，非常適合用於中大型專案中。這篇教學將帶你快速學會如何進行以下操作：

1. 建立資料表
2. 新增資料
3. 查詢資料
4. 更新資料
5. 刪除資料

---

## 1. 建立資料表 (Create Table)

在資料庫中建立一個名為 `products` 的資料表，用來儲存產品相關資訊。

```sql
CREATE TABLE products (
    product_id SERIAL PRIMARY KEY,   -- 自動增長的產品 ID
    name VARCHAR(100) NOT NULL,      -- 產品名稱，最多100個字符
    category VARCHAR(50),            -- 產品類別
    price NUMERIC(10, 2),            -- 價格，小數點後保留2位
    in_stock BOOLEAN DEFAULT TRUE    -- 是否有庫存，預設為有
);
```

#### 欄位說明：
- product_id：自動增長的主鍵，PostgreSQL 會為每筆資料自動分配唯一的 ID。
- name：產品名稱，不允許為空值。
- category：產品分類。
- price：產品價格，支援小數格式。
- in_stock：庫存狀態，布林值，預設為 TRUE。

## 2. 新增資料 (Insert Data)
將資料插入 products 資料表，以下是範例資料：
```sql
INSERT INTO products (name, category, price, in_stock)
VALUES
    ('手機', '3C', 999.99, TRUE),
    ('耳機', '配件', 49.99, TRUE),
    ('洗衣機', '家電', 4999.99, FALSE);
```

## 3. 查詢資料 (Select Data)
查詢所有資料
想要查詢表中的所有產品，可以使用以下指令：

```sql
SELECT * FROM products;
```

### 篩選特定條件的資料
查詢 `category` 為「3C」的產品：
```sql
SELECT * FROM products WHERE category = '3C';
```
查詢價格大於 100 的產品：
```sql
SELECT * FROM products WHERE price > 100;
```

### 使用進階篩選條件
查詢 `category` 為「3C」或「配件」的產品：
```sql
SELECT * FROM products WHERE category IN ('3C', '配件');
```
範圍查詢（價格介於 50 到 1000）：
```sql
SELECT * FROM products WHERE price BETWEEN 50 AND 1000;
```

## 4. 更新資料 (Update Data)
將「手機」的價格更新為 899.99：
```sql
UPDATE products
SET price = 899.99
WHERE name = '手機';
```
注意：
WHERE 條件是必需的，否則會更新整個表內的所有資料！

## 5. 刪除資料 (Delete Data)
刪除 category 為「家電」的所有產品：
```sql
DELETE FROM products WHERE category = '家電';
```
## 6. 刪除資料表 (Drop Table)
若不再需要這個資料表，可以直接刪除：
```sql
DROP TABLE products;
```


