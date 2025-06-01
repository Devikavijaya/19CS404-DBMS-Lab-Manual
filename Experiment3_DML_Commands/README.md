# Experiment 3: DML Commands

## Aim
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
```
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'. sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)
```
 SQL code1
```
UPDATE sales 
SET sell_price = sell_price * 1.05
WHERE product_id = 15 
AND sale_date = '2023-01-31';
```
**Output:**

![image](https://github.com/user-attachments/assets/9b5c9d25-d041-47a3-8120-0d19215f8bd1)

**Question 2**
```
Write a SQL statement to double the availability of the product with product_id 1.
products table

---------------
product_id
product_name
category_id
availability
```
SQL Code:
```
UPDATE products
SET availability = 2 * availability 
WHERE product_id = 1;
```
**Output:**

![image](https://github.com/user-attachments/assets/84b1c373-42df-4792-aa07-19ccfd561aba)

**Question 3**
```
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.
Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```
SQL code
```
UPDATE Products
SET reorder_lvl = 20
WHERE quantity < 10
AND category = 'Snacks';
```
**Output:**

![image](https://github.com/user-attachments/assets/8a96bd93-3c3d-406e-bf20-d43e3cfb57c7)

**Question 4**
```
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.
products table

---------------
product_id
product_name
category_id
availability

```
SQL code 
```
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

![image](https://github.com/user-attachments/assets/b831a03e-68a0-4093-a8b3-cf31c9896080)

**Question 5**
```
Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules. Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```
SQL code 
```
UPDATE Employees
SET salary =
CASE 
WHEN department_id = 40 THEN ROUND(salary * 1.25 ,2)
WHEN department_id = 90 THEN ROUND(salary * 1.15 ,2)
WHEN department_id = 110 THEN ROUND(salary * 1.10 ,2)
ELSE salary
END;
```
**Output:**

![image](https://github.com/user-attachments/assets/e9965bce-5a7e-4585-835a-45b23180922f)

**Question 6**
```
Write a SQL query to Delete customers from 'customer' table where 'WORKING_AREA' is 'New York'. Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA 
```
SQL code 
```
DELETE FROM Customer
WHERE WORKING_AREA = 'New York';
```
**Output:**

![image](https://github.com/user-attachments/assets/10b4c0ed-ba58-401b-a44d-4094f405e37a)

**Question 7**
```
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'. Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003  |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |

```
SQL Code
```
DELETE FROM Customer
WHERE CUST_NAME LIKE '%Holmes%';
```
**Output:**

![image](https://github.com/user-attachments/assets/a8cf9da4-f656-4c1e-a40a-d238851d3f2e)

**Question 8**
 ```
Write a SQL query to Delete All Doctors with a NULL Last Name.

Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization.
```
SQL code
```
DELETE FROM Doctors
WHERE last_name IS NULL;
```
**Output:**

![image](https://github.com/user-attachments/assets/60473733-044b-40f9-8738-54fb19f234ff)

**Question 9**
```
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization

```
SQL code
```
DELETE FROM Doctors
WHERE specialization IN ('Pediatrics','Cardiology')
AND last_name = 'Brown';
```
**Output:**

```
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization

```
SQL code
```
DELETE FROM Doctors
WHERE specialization IN ('Pediatrics','Cardiology')
AND last_name = 'Brown';
```
**Question 10**
```
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000 Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          
```
SQL Code:

```
DELETE FROM Customer
WHERE CUST_NAME LIKE 'M%'
AND PAYMENT_AMT < 3000;
```
**Output:**

![image](https://github.com/user-attachments/assets/a4778cdf-eed0-4cfb-a601-0fec937ae6ed)

## RESULT

<img width="388" alt="image" src="https://github.com/user-attachments/assets/2b757797-9119-4563-b0cb-b21b7df3ec59" />

Thus, the SQL queries to implement DML commands have been executed successfully.
