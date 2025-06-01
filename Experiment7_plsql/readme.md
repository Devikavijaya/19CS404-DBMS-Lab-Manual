# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

## Program
```
DECLARE
   num1 NUMBER := 80;
   num2 NUMBER := 45;
BEGIN
   IF num1 > num2 THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
   ELSIF num2 > num1 THEN
      DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
   ELSE
      DBMS_OUTPUT.PUT_LINE('Both numbers are equal: ' || num1);
   END IF;
END;
/
``` 
**Expected Output:**  

![image](https://github.com/user-attachments/assets/f044f569-3cc7-422a-85dc-b8e07c253136)

Greater number is: 80

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

## Program:
```
DECLARE
 n NUMBER := 10;
 i NUMBER := 1;
 sum NUMBER := 0;
BEGIN
 WHILE i <= n LOOP
    sum := sum + i;
    i := i + 1;
 END LOOP;
 
 DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```
**Expected Output:**

![image](https://github.com/user-attachments/assets/9a267f4e-b807-4361-ab49-38f546abeb7d)

Sum of first 10 natural numbers is: 55

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.
  
## Program
```
DECLARE
   n NUMBER := 10;
   i NUMBER := 1;
   sum NUMBER := 0;
BEGIN
   WHILE i <= n LOOP
      sum := sum + i;
      i := i + 1;
   END LOOP;
   
   
   DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```
**Expected Output:**
![image](https://github.com/user-attachments/assets/1112beda-d270-472c-9fb4-5f442489e683)

n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

## Program
```
DECLARE
   n NUMBER := 1535;         
   original NUMBER := n;     
   reversed NUMBER := 0;    
   digit NUMBER;             
BEGIN
   WHILE n > 0 LOOP
      digit := MOD(n, 10);                
      reversed := (reversed * 10) + digit; 
      n := TRUNC(n / 10);                 
   END LOOP;

   DBMS_OUTPUT.PUT_LINE('n = ' || original);
   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
/
```
**Expected Output:**  

![image](https://github.com/user-attachments/assets/399d3949-390a-4440-a0e4-b0668c90ce5d)
n = 1535  
Reversed number is 5351

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.
  
## Program
```
DECLARE
   a NUMBER := 10;
   b NUMBER := 9;
   c NUMBER := 15;
   largest NUMBER;
BEGIN
   IF a >= b AND a >= c THEN
      largest := a;
   ELSIF b >= a AND b >= c THEN
      largest := b;
   ELSE
      largest := c;
   END IF;

   DBMS_OUTPUT.PUT_LINE('a = ' || a || ', b = ' || b || ', c = ' || c);
   DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
/
```
**Expected Output:**  

![image](https://github.com/user-attachments/assets/8f07e5c6-3fa5-4bfe-8151-b48929986c07)

a = 10, b = 9, c = 15  
Largest of three number is 15

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
