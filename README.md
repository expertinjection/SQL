# SQL Functions Guide

This document provides a comprehensive overview of common SQL functions with explanations, examples, and real-world use cases.

---

## 1. **Aggregate Functions**

### `SUM()`
- **Description**: Returns the total sum of a numeric column.
- **Example**: `SELECT SUM(salary) FROM employees;`
- **Use Case**: Calculating total revenue, expenses, or salaries.

### `AVG()`
- **Description**: Returns the average value of a numeric column.
- **Example**: `SELECT AVG(age) FROM users;`
- **Use Case**: Finding average salary, age, etc.

### `COUNT()`
- **Description**: Counts the number of rows.
- **Example**: `SELECT COUNT(*) FROM orders;`
- **Use Case**: Counting total customers, orders, etc.

### `MAX()` / `MIN()`
- **Description**: Returns the maximum or minimum value in a column.
- **Example**: `SELECT MAX(price), MIN(price) FROM products;`
- **Use Case**: Finding highest/lowest transaction, salary, etc.

---

## 2. **String Functions**

### `CONCAT()`
- **Description**: Combines two or more strings.
- **Example**: `SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;`

### `SUBSTRING()` / `SUBSTR()`
- **Description**: Extracts a part of a string.
- **Example**: `SELECT SUBSTRING(phone_number, 5, 3) FROM employees;`

### `UPPER()` / `LOWER()`
- **Description**: Converts string to upper/lowercase.
- **Example**: `SELECT UPPER(last_name) FROM employees;`

### `LENGTH()` / `LEN()`
- **Description**: Returns length of a string.
- **Example**: `SELECT LENGTH(email) FROM users;`

### `TRIM()` / `LTRIM()` / `RTRIM()`
- **Description**: Removes whitespace.
- **Example**: `SELECT TRIM('   John   ');`

---

## 3. **Date Functions**

### `NOW()` / `CURRENT_DATE` / `CURRENT_TIMESTAMP`
- **Description**: Returns current date/time.
- **Example**: `SELECT NOW();`

### `DATEDIFF()`
- **Description**: Returns difference in days between two dates.
- **Example**: `SELECT DATEDIFF('2025-06-29', '2025-06-01');`

### `DATE_ADD()` / `DATE_SUB()`
- **Description**: Adds or subtracts a date interval.
- **Example**: `SELECT DATE_ADD('2025-06-29', INTERVAL 10 DAY);`

### `EXTRACT()` / `YEAR()` / `MONTH()` / `DAY()`
- **Description**: Extracts part of a date.
- **Example**: `SELECT YEAR(hire_date) FROM employees;`

---

## 4. **Mathematical Functions**

### `ROUND()`
- **Description**: Rounds a number to specified decimals.
- **Example**: `SELECT ROUND(123.4567, 2);`

### `FLOOR()` / `CEIL()`
- **Description**: Rounds down/up.
- **Example**: `SELECT FLOOR(99.99), CEIL(99.01);`

### `ABS()`
- **Description**: Returns absolute value.
- **Example**: `SELECT ABS(-15);`

### `MOD()`
- **Description**: Returns remainder.
- **Example**: `SELECT MOD(10, 3);`

---

## 5. **Conditional Functions**

### `CASE` / `WHEN`
- **Description**: Conditional logic.
- **Example**:
```sql
SELECT employee_id, salary,
  CASE 
    WHEN salary > 10000 THEN 'High'
    WHEN salary BETWEEN 5000 AND 10000 THEN 'Medium'
    ELSE 'Low'
  END AS salary_level
FROM employees;
```

### `COALESCE()`
- **Description**: Returns first non-null value.
- **Example**: `SELECT COALESCE(middle_name, 'N/A') FROM employees;`

### `NULLIF()`
- **Description**: Returns NULL if two values are equal.
- **Example**: `SELECT NULLIF(100, 100);`

---

## 6. **Conversion Functions**

### `CAST()` / `CONVERT()`
- **Description**: Converts data type.
- **Example**: `SELECT CAST(price AS INT) FROM products;`

---

## 7. **Window Functions**

### `ROW_NUMBER()`
- **Description**: Assigns unique row number.
- **Example**:
```sql
SELECT name, salary,
  ROW_NUMBER() OVER (ORDER BY salary DESC) as rank
FROM employees;
```

### `RANK()` / `DENSE_RANK()`
- **Description**: Ranks rows with ties.
- **Example**:
```sql
SELECT name, salary,
  RANK() OVER (ORDER BY salary DESC) as rank
FROM employees;
```

### `LEAD()` / `LAG()`
- **Description**: Access next/previous row.
- **Example**:
```sql
SELECT name, salary,
  LAG(salary) OVER (ORDER BY salary) AS previous_salary
FROM employees;
```

---

## Real-World Use Cases

### 1. **E-commerce Dashboard**
- Aggregate functions to track total sales, average cart value.
- Date functions to filter transactions for current month.
- CASE statements to categorize customers by spend.

### 2. **Employee Management System**
- String functions to format names.
- Date functions to calculate experience.
- Window functions to rank employees by performance.

### 3. **Banking Applications**
- Use `LEAD()`/`LAG()` to analyze transaction patterns.
- `ABS()` to compute net transaction difference.
- `MOD()` to assign routing buckets.

---

End of File.
