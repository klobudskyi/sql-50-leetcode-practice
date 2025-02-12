# sql-50-leetcode-practice
## SELECT:
### 1757. Recyclable and Low Fat Products
```sql
SELECT
    product_id
FROM Products
WHERE
    low_fats = 'Y'
    AND recyclable = 'Y';
```
### 584. Find Customer Referee
```sql
SELECT name
FROM Customer
WHERE
    referee_id != 2
    OR referee_id IS NULL;
```
### 595. Big Countries
```sql
SELECT
    name,
    population,
    area
FROM World
WHERE
    area >= 3000000
    OR population >= 25000000;
```
### 1148. Article Views I
```sql
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY 1 ASC;
```
### 1683. Invalid Tweets
```sql
SELECT
    tweet_id
FROM Tweets
WHERE LENGTH(content) > 15;
```
## Basic JOINs:
### 1378. Replace Employee ID With The Unique Identifier
```sql
SELECT
    u.unique_id
    , e.name
FROM Employees e
LEFT JOIN EmployeeUNI u ON e.id = u.id;
```
### 1068. Product Sales Analysis I
```sql
SELECT
    p.product_name
    , s.year
    , s.price
FROM Sales s
LEFT JOIN Product p ON s.product_id = p.product_id;
```
### 1581. Customer Who Visited but Did Not Make Any Transactions
```sql
SELECT
    v.customer_id
    , COUNT (*) AS count_no_trans
FROM Visits v
LEFT JOIN Transactions t ON v.visit_id = t.visit_id
WHERE 
    t.transaction_id IS NULL
    AND t.visit_id IS NULL
GROUP BY 1;
```
### 197. Rising Temperature
```sql

```
### 570. Managers with at Least 5 Direct Reports
```sql
WITH status_manager AS (

    SELECT
        managerId
        , CASE
                WHEN COUNT(*) >= 5 THEN 'busy_manager'
                ELSE 'free_manager'
          END AS managerStatus
    FROM Employee
    WHERE managerId IS NOT NULL
    GROUP BY 1

)

SELECT name
FROM Employee e
JOIN status_manager s ON s.managerId = e.id
WHERE managerStatus = 'busy_manager';
```
