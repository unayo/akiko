---
title: Tables 資料表管理教學 | 創建、修改與刪除資料表的全方位指南
description: 本文詳細介紹如何有效管理資料表 (Tables)，包括創建、修改結構、新增與刪除資料，幫助您掌握資料庫的基礎操作。
categories:
- [資料庫管理, Tables]
- [SQL 教學]
tags:
- [資料表, SQL 指令, 資料庫操作]
date: 2024-11-24
---

資料表 (Tables) 是關聯式資料庫的核心，所有數據都儲存在這些表格中。本教學將幫助您掌握資料表的基礎管理操作，包括 **主鍵 (Primary Key)**、**外來鍵 (Foreign Key)** 的設置，以及如何使用 **INNER JOIN** 連接多張資料表進行查詢。

---

## 🏆 主鍵（Primary Key）

主鍵是一個欄位或一組欄位，用來唯一識別資料表中的每一筆資料。主鍵的好處包括：
- 確保資料表中每筆資料的唯一性。
- 加速查詢操作。
- 確保資料的完整性。

以下範例展示如何設置主鍵：

```sql
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY, -- 自動增長的主鍵
    name VARCHAR(50),              -- 學生名稱
    age INT                        -- 學生年齡
);
```

## 🤝 外來鍵（Foreign Key）
外來鍵用來連結兩張表格，確保資料表之間的資料完整性。例如，將學生與課程建立關聯：

資料表範例
1. `courses`：存放課程資訊。
2. `enrollments`：紀錄學生與課程的對應關係。
```sql
CREATE TABLE courses (
    course_id SERIAL PRIMARY KEY,  -- 課程 ID
    course_name VARCHAR(50)        -- 課程名稱
);

CREATE TABLE enrollments (
    enrollment_id SERIAL PRIMARY KEY, -- 註冊 ID
    student_id INT REFERENCES students(student_id), -- 關聯學生
    course_id INT REFERENCES courses(course_id)     -- 關聯課程
);
```
說明：
- `enrollments.student_id` 參考了 `students.student_id`。
- `enrollments.course_id` 參考了 `courses.course_id`。
- 當新增或更新資料時，資料庫會自動檢查關聯的資料是否存在。

## 🔄 INNER JOIN 查詢
INNER JOIN 用於合併多張表格，僅返回「在所有相關表中同時存在的資料」。

查詢範例
我們希望查詢學生的姓名和他們選修的課程名稱。
```sql
SELECT 
    students.name AS student_name, 
    courses.course_name AS enrolled_course
FROM 
    enrollments
INNER JOIN students 
    ON enrollments.student_id = students.student_id
INNER JOIN courses 
    ON enrollments.course_id = courses.course_id;
```
#### 執行結果（範例輸出）
| student_name  | enrolled_course |
| ----- | -------- |
| John Doe | Mathematics |
| Jane Smith | Physics |
#### 查詢解釋
1. 起點：enrollments 表
此表包含學生與課程的對應關係，是查詢的起始點。

2. 連接學生資訊：INNER JOIN students
將 students.student_id 與 enrollments.student_id 配對，獲取學生姓名。

3. 連接課程資訊：INNER JOIN courses
將 courses.course_id 與 enrollments.course_id 配對，獲取課程名稱。

4. 結果：返回學生姓名和課程名稱
最終輸出學生的姓名與選修的課程。

## 🌟 重點提示
1. 使用主鍵與外來鍵確保資料完整性
主鍵保證資料唯一性，外來鍵確保表與表之間的正確關聯。

2. INNER JOIN 只返回匹配的資料
如果某筆資料在任意一張表中不存在，則不會包含在結果中。

3. 進一步學習
可以探索其他 JOIN 類型，例如 LEFT JOIN 或 FULL OUTER JOIN，了解更複雜的資料查詢方式。


## 結語
本篇文章介紹了資料表管理的基礎內容，包括主鍵、外來鍵的設置及使用 INNER JOIN 進行資料表連接的查詢。透過這些操作，您可以更有效率地管理資料表並實現跨表查詢。

如果您有興趣學習更進階的 SQL 操作，例如索引管理或資料庫優化，請持續關注我們的更多教學文章！


