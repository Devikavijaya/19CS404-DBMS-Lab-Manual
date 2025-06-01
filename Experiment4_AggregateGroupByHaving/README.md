# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**

```
What is the average duration of insurance coverage for patients covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
StartDate          DATE
EndDate            DATE
For example:
Result
InsuranceCompany  AvgCoverageDurationDays
----------------  -----------------------
ABC Insurance     7.0
DEF Insurance     3.0
JKL Insurance     3.0
STU Insurance     3.0
VWX Insurance     3.0
XYZ Insurance     3.0
YZA Insurance     3.0
```
SQL code 
```
SELECT InsuranceCompany,AVG((EndDate - StartDate)) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany;
```
**Output:**

<img width="392" alt="image" src="https://github.com/user-attachments/assets/3c678e88-dac1-4537-9a33-6df3986bd13d" />

**Question 2**

![image](https://github.com/user-attachments/assets/01e4dc7c-9439-4404-8e5a-a360b907a25d)


SQL code 
```
SELECT strftime('%Y',ValidityPeriod) AS "ValidityYear",COUNT(PatientID) AS "TotalPatients"
FROM Insurance
GROUP BY ValidityPeriod;
```

**Output:**

![image](https://github.com/user-attachments/assets/fccf3624-75a5-40a1-83e6-731bba8316e8)

**Question 3**
```
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_name_length
---------------
10.0


```
SQL code 
```
SELECT AVG(LENGTH(name)) AS avg_name_length
FROM customer
WHERE city = 'Chennai';
```
**Output:**

<img width="286" alt="image" src="https://github.com/user-attachments/assets/76d7738b-24f4-4da1-9809-fece76082523" />

**Question 4**
```
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_email_length_below_30
-------------------------
14.0
```
SQL code 
```
SELECT AVG(LENGTH(email)) AS avg_email_length_below_30
FROM customer
WHERE city = 'Mumbai';
```
**Output:**

<img width="374" alt="image" src="https://github.com/user-attachments/assets/ab0d788c-1474-490a-9564-ee7242f59eef" />

**Question 5**
![image](https://github.com/user-attachments/assets/eaee3f19-9d5a-43b6-8451-db0c6de8c2d9)

SQL code 
```
SELECT jdate,MIN(workhour) AS "MIN(workhour)"
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10;
```
**Output:**

![image](https://github.com/user-attachments/assets/2937d95f-1e2e-4e7e-91b0-de2c541d2cb3)

**Question 6**

![image](https://github.com/user-attachments/assets/41f3ff03-cb78-4df4-a496-b37eecead1c3)


SQL code 
```
SELECT jdate,MIN(workhour) AS "MIN(workhour)"
FROM employee1
GROUP BY jdate
HAVING MIN(workhour) < 10;
SELECT age,MIN(income) AS "MIN(income)"
FROM employee
GROUP BY age
Having MIN(income) < 400000;
```

**Output:**

![image](https://github.com/user-attachments/assets/068e97a8-a041-45cf-9159-0667574b2ada)

**Question 7**
![image](https://github.com/user-attachments/assets/d58a9d0f-75ff-4d23-9a6e-ff9dbbf76897)


SQL code
```
SELECT strftime('%Y',ValidityPeriod) AS "ValidityYear",COUNT(PatientID) AS "TotalPatients"
FROM Insurance
GROUP BY ValidityPeriod;
```

**Output:**

![image](https://github.com/user-attachments/assets/d57e25e9-e3fb-4b45-a26a-29dfb79113b5)

**Question 8**
![image](https://github.com/user-attachments/assets/6757af8e-3b94-4f8d-8732-84ca0340bb1a)

SQL code 
```
SELECT Medication,Avg(Dosage) AS "AvgDosage"
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

![image](https://github.com/user-attachments/assets/58c8c467-6068-4bcc-8eb9-ad68680cd758)

**Question 9**
```
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

For example:

Result
COUNT
----------
8

```
SQL code 
```
SELECT COUNT(cust_name) AS COUNT
FROM customer;
```

**Output:**

<img width="312" alt="image" src="https://github.com/user-attachments/assets/4f17f6de-d652-493f-977b-63a7a7725b09" />

**Question 10**
![image](https://github.com/user-attachments/assets/f552123d-c17f-41d9-b73d-b4d22d7d71b3)


SQL code
```
SELECT PatientID,COUNT(Medication) AS "TotalMedications"
FROM Prescriptions
GROUP BY PatientID;
```
**Output:**

![image](https://github.com/user-attachments/assets/8a5aef2e-3e3c-4fcc-8344-7eae95dbc33c)

## RESULT

![Screenshot 2025-04-30 212935](https://github.com/user-attachments/assets/84122ac5-1b7a-4841-9305-2102fdbeab3d)

Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
