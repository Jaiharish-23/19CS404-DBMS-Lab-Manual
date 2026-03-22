# Experiment 4: Aggregate Functions, Group By and Having Clause

```
Developed by;
Name : JAI HARISH R
Reg No : 212224040124
```

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
How many medical records does each doctor have?

Sample table:MedicalRecords Table
```

<img width="755" height="124" alt="image" src="https://github.com/user-attachments/assets/fe6b2a7a-907e-4dc6-9b48-4af1b5a65e4d" />


```
For example:

Result
DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3

```

```sql
select  DoctorID ,COUNT(RecordID) AS TotalRecords FROM  MedicalRecords
GROUP BY DoctorID 
ORDER BY DoctorID ;

```

**Output:**

<img width="537" height="458" alt="image" src="https://github.com/user-attachments/assets/c9d104b9-8840-47e1-9a09-8195f0f1a9ca" />


**Question 2**
```
What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table
```

<img width="713" height="98" alt="image" src="https://github.com/user-attachments/assets/58ba34eb-15e5-4982-aeae-4ff05f51ed9b" />

```
For example:

Result
PatientID   TotalMedications
----------  ----------------
1           1
2           1
3           1
4           1
5           1
6           1
7           1
8           1
9           1
10          1
```


```sql
select  PatientID ,COUNT(*) AS  TotalMedications FROM Prescriptions
GROUP BY  PatientID 
ORDER BY PatientID ;
```

**Output:**

<img width="568" height="545" alt="image" src="https://github.com/user-attachments/assets/63b64734-e082-411c-a79e-fe46e670a1f6" />


**Question 3**
```
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
age_difference
--------------
13

```

```sql
SELECT MAX(age)-MIN(age) AS age_difference FROM  employee;
```

**Output:**

<img width="508" height="224" alt="image" src="https://github.com/user-attachments/assets/ef256246-5bfd-451c-b683-10ddd8f079a7" />


**Question 4**
```
Write a SQL query to count the number of customers. Return number of customers.

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

```sql
SELECT COUNT(*) AS COUNT FROM customer ;
```

**Output:**

<img width="486" height="229" alt="image" src="https://github.com/user-attachments/assets/5b024d98-32d2-4b05-a25d-2fd347265480" />


**Question 5**
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

```sql
SELECT COUNT(*) AS COUNT FROM  customer
WHERE grade>0;
```

**Output:**

<img width="672" height="231" alt="image" src="https://github.com/user-attachments/assets/7fa2c651-5ddd-40f9-9d12-3ead2a79b603" />



**Question 6**
```
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.

Sample table: employee

id

name

age

address

salary

1

Paul

32

California

20000

4

Mark

25

Richtown

65000

5

David

27

Texas

85000

 

For example:

Result
COUNT
----------
4

```

```sql
SELECT COUNT(DISTINCT age) AS COUNT FROM  employee ;
```

**Output:**

<img width="513" height="223" alt="image" src="https://github.com/user-attachments/assets/349eede2-7f49-4fed-9261-5236e7499ee4" />


**Question 7**
```
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

Sample table: customer1
```
<img width="588" height="101" alt="image" src="https://github.com/user-attachments/assets/ba47de76-1465-44c8-9a32-d57ab19931ba" />

```
For example:

Result
address     AVG(salary)
----------  -----------
Ahmedabad   2000.0
Bhopal      8500.0
Delhi       1500.0
Hyderabad   4500.0
Indore      10000.0
Kota        2000.0
Mumbai      6500.0

```

```sql
SELECT  address , AVG(salary) FROM customer1
GROUP BY address 
HAVING AVG(salary)<15000
ORDER BY address ;
```

**Output:**

<img width="582" height="446" alt="image" src="https://github.com/user-attachments/assets/48fc190b-6183-4279-b144-c2fa750fbc10" />


**Question 8**
```
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

Sample table: customer1
```
<img width="593" height="109" alt="image" src="https://github.com/user-attachments/assets/8ae3bc82-4b5a-473c-8d56-879cddaf01c5" />


```
For example:

Result
address     AVG(salary)
----------  -----------
Bhopal      8500.0
Indore      10000.0
Mumbai      6500.0

```

```sql
SELECT address , AVG(salary) FROM  customer1
GROUP BY  address
HAVING  AVG(salary) >5000
ORDER BY  address ;
```

**Output:**

<img width="589" height="312" alt="image" src="https://github.com/user-attachments/assets/c9d3ad38-1d4d-4610-9152-7f078806d61c" />


**Question 9**
```
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.

Sample table: products
```
<img width="596" height="130" alt="image" src="https://github.com/user-attachments/assets/97a848ba-7f5f-484f-971d-2298020253ba" />

```
For example:

Result
category_id  product_name  Price
-----------  ------------  ----------
1            Orange        15.5
2            Monitor       25

```

```sql
SELECT category_id,product_name, price as  Price from products
GROUP BY category_id 
HAVING MAX(Price)>15
ORDER BY category_id  ;
```

**Output:**

<img width="731" height="282" alt="image" src="https://github.com/user-attachments/assets/d4100413-cc93-41fb-9aa9-9d9fe4dd1a82" />


**Question 10**
```
How many male and female doctors are there in each medical specialty?

Sample table:Doctors Table
```
<img width="732" height="113" alt="image" src="https://github.com/user-attachments/assets/897bef41-2faf-4dfa-a68c-60636f82d443" />

```
For example:

Result
Specialty          Gender    TotalDoctors
-----------------  --------  --------------
Cardiology         Male      1
Dermatology        Male      1
Gastroenterology   Female    4
Gastroenterology   Male      1
Pediatrics         Female    1
Pediatrics         Male      2

```

```sql
select  Specialty      ,    Gender , count(*)  TotalDoctors from Doctors
group by Specialty,Gender ; 
```

**Output:**

<img width="772" height="471" alt="image" src="https://github.com/user-attachments/assets/af6d9d1f-17cc-4132-adf5-e80195cbb770" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
