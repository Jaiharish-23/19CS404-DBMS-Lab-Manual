# Experiment 3: DML Commands

## AIM
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
Write a SQL statement to Increase the salary by 500 and email as 'updated' for employees with job ID 'SA_REP' and commission percentage greater than 0.15

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
For example:

Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, EMAIL, SALARY, JOB_ID FROM EMPLOYEES 
WHERE job_id = 'SA_REP' AND EMAIL='updated' LIMIT 5;
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
150          Peter       updated     10500       SA_REP
151          David       updated     10000       SA_REP
152          Peter       updated     9500        SA_REP
153          Christophe  updated     8500        SA_REP
154          Nanette     updated     8000        SA_REP

```
***Code***
```sql
UPDATE Employees 
SET salary =salary +500,
email ='updated'
WHERE job_id ='SA_REP' AND  commission_pct >0.15;
```

**Output:**
<img width="1237" height="298" alt="image" src="https://github.com/user-attachments/assets/7779076c-77dd-4c23-86ec-21083c28b8c8" />


**Question 2**
```
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

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
***Code***
```sql
UPDATE Products
SET quantity=quantity *1.10;
```

**Output:**
<img width="1156" height="302" alt="image" src="https://github.com/user-attachments/assets/5599760b-f9e4-4159-ba5f-d0d065698ed6" />


**Question 3**
```
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
For example:

Test	Result
select changes();
changes()
----------
4

```
***Code***
```sql
UPDATE products 
SET reorder_lvl =reorder_lvl *1.30
WHERE category ='Food' AND  reorder_lvl<50;
```

**Output:**
<img width="1225" height="180" alt="image" src="https://github.com/user-attachments/assets/27526cc7-a998-4f65-a48f-34f374fd56b5" />


**Question 4**
```
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

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
***Code***
```sql
UPDATE Products
SET sell_price =sell_price *1.10
WHERE category = 'Bakery';
```

**Output:**

<img width="1235" height="248" alt="image" src="https://github.com/user-attachments/assets/0a29ced5-0f58-41a0-bd46-b3e0bf923a94" />


**Question 5**
```
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

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
***Code***
```sql
UPDATE  products
SET  product_name= 'Premium Bread' 
WHERE product_id =5;
```

**Output:**
<img width="1232" height="181" alt="image" src="https://github.com/user-attachments/assets/3ae850f3-f8be-4f6a-a720-6a6554318aa5" />


**Question 6**
```
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
1

```
***Code***
```sql
DELETE FROM Customer 
WHERE  GRADE=2 AND CUST_NAME LIKE 'M%' AND  PAYMENT_AMT<3000;
```

**Output:**
<img width="1337" height="159" alt="image" src="https://github.com/user-attachments/assets/604d13e6-7026-4dea-aabb-3d1499966974" />


**Question 7**
```
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
2
```
***Code***
```sql
DELETE FROM  Customer
WHERE CUST_COUNTRY NOT IN ('UK', 'USA', 'Canada') AND  GRADE>=3;
```

**Output:**
<img width="1344" height="169" alt="image" src="https://github.com/user-attachments/assets/2b31bef9-9aad-4e19-bab9-1d859cc36853" />


**Question 8**
```
Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select changes();
changes()
----------
11

```
***Code***
```sql
DELETE FROM Customer 
WHERE CUST_COUNTRY NOT IN ('India','USA');
```

**Output:**
<img width="1335" height="241" alt="image" src="https://github.com/user-attachments/assets/cc0c4f74-01ca-4d2f-a3f7-80fe1b39b08d" />


**Question 9**
```
Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.

 
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:

Test	Result
select distinct(agent_code)from customer;
AGENT_CODE
----------
A003
A008
A011
A006
A005
A010
A002
A004
A009
A007
A012
A001
AGENT_CODE
----------
A011
A006
A005
A010
A002
A004
A009
A007
A012
A001

```
***Code***
```sql
DELETE FROM  Customer
WHERE AGENT_CODE IN ('A003','A008');
```

**Output:**
<img width="383" height="551" alt="image" src="https://github.com/user-attachments/assets/4bb69b0b-dc7d-405e-b369-bf28d60f0310" />


**Question 10**
```
Write a query to fetch details of employees with the address as “DELHI(DEL)” from EmployeeInfo table.
 
EmpID

EmpFname

EmpLname

Department

Project

Address

DOB

Gender

1

Sanjay

Mehra

HR

P1

Hyderabad(HYD)

01/12/1976

M

2

Ananya

Mishra

Admin

P2

Delhi(DEL)

02/05/1968

F



For example:

Result
EmpID       EmpFname    EmpLname    Department  Project     Address     DOB         Gender
----------  ----------  ----------  ----------  ----------  ----------  ----------  ----------
2           Ananya      Mishra      Admin       P2          Delhi(DEL)  1968-05-02  F
5           Ankit       Kapoor      Admin       P2          Delhi(DEL)  1994-07-03  M

```
***Code***
```sql
SELECT * FROM  EmployeeInfo
WHERE Address ='Delhi(DEL)';
```

**Output:**
<img width="1019" height="121" alt="image" src="https://github.com/user-attachments/assets/7eadeb47-6333-49aa-9a6a-0f9985f3ed64" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
