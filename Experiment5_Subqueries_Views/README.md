# Experiment 5: Subqueries and Views
```
Developed by;
Name : JAI HARISH R
Reg No : 212224040124
```
## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $4500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

 
 

For example:

Result
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           Chaitali    25          Mumbai      6500
5           Hardik      27          Bhopal      8500
7           Muffy       24          Indore      10000

```
```sql
select * from CUSTOMERS
where SALARY in (select SALARY from CUSTOMERS where  SALARY>4500);
```

**Output:**

<img width="929" height="312" alt="image" src="https://github.com/user-attachments/assets/1aafa188-645b-4df3-9207-5fb073dca907" />


**Question 2**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is greater than $1500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

 
 

For example:

Result
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Ramesh      32          Ahmedabad   2000
3           Kaushik     23          Kota        2000
4           Chaitali    25          Mumbai      6500
5           Hardik      27          Bhopal      8500
6           Komal       22          Hyderabad   4500
7           Muffy       24          Indore      10000

```

```sql
select * from CUSTOMERS
where SALARY in (select SALARY FROM  CUSTOMERS WHERE SALARY>1500);
```

**Output:**

<img width="941" height="445" alt="image" src="https://github.com/user-attachments/assets/30adfafd-1a95-4f40-9ea1-3a23c4c04f47" />


**Question 3**
```
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

ORDERS TABLE

name            type
----------     ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int

For example:

Result
ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70005       2400.6      2012-07-27  3007         5001
70008       5760.0      2012-09-10  3002         5001
70003       2480.4      2012-10-10  3009         5003
70013       3045.6      2012-04-25  3002         5001

```

```sql
select * from ORDERS
WHERE purch_amt > (select AVG(purch_amt) from ORDERS WHERE ord_date='2012-10-10');
```

**Output:**

<img width="1008" height="313" alt="image" src="https://github.com/user-attachments/assets/b1f7a617-34f1-47ac-9864-27e3fe833db8" />


**Question 4**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

 
 

For example:

Result
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Ramesh      32          Ahmedabad   2000
2           Khilan      25          Delhi       1500
3           Kaushik     23          Kota        2000

```

```sql
select * from CUSTOMERS
where SALARY in (select SALARY from CUSTOMERS where SALARY<2500 );
```

**Output:**

<img width="950" height="340" alt="image" src="https://github.com/user-attachments/assets/acebd396-be18-4c8b-b84b-a5442656a197" />


**Question 5**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

 
 

For example:

Result
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Khilan      25          Delhi       1500

```

```sql
select * from CUSTOMERS 
where Address =(select Address from CUSTOMERS where Address='Delhi');
```

**Output:**

<img width="983" height="246" alt="image" src="https://github.com/user-attachments/assets/1122c4f1-c27e-4815-826f-986746c23b6b" />


**Question 6**
```
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER

For example:

Result
id     name             age              city             income
-----  ---------------  ---------------  ---------------  ----------
101    Peter            32               NewYork          200000
102    Mark             32               California       300000
103    Donald           25               Arizona          1000000
104    Obama            35               Florida          5000000
105    Linklon          32               Georgia          250000
107    Adam             35               California       5000000

```
```sql
select * from Employee
where age < (select AVG(age) from Employee where income >250000);
```

**Output:**

<img width="1107" height="362" alt="image" src="https://github.com/user-attachments/assets/5a17f9b4-c01e-4de3-956e-55caf15af71f" />


**Question 7**
```
Write a SQL query that retrieve all the columns from the table "Grades", where the grade is equal to the maximum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)



For example:

Result
student_id       student_name     subject          grade
---------------  ---------------  ---------------  ---------------
3                Charlie          Math             95
5                Emma             Science          92
7                John             Social           85

```

```sql
select * from GRADES g
where grade in(select MAX(grade) from GRADES where subject=g.subject);
```

**Output:**

<img width="1107" height="311" alt="image" src="https://github.com/user-attachments/assets/8526e6ed-c0b0-418e-93c3-a40dfa2dfd4b" />


**Question 8**
```
Write a SQL query to Retrieve the medications with dosages equal to the lowest dosage

Table Name: Medications (attributes: medication_id, medication_name, dosage)



For example:

Result
medic  medication_name  dosage
-----  ---------------  ---------------
2      Ibuprofen        200mg
```

```sql
select * from Medications
where dosage =(select min(dosage) from Medications);
```

**Output:**

<img width="736" height="280" alt="image" src="https://github.com/user-attachments/assets/689f3a91-c059-4948-a70a-aac3ebb77cc6" />


**Question 9**
```
Write a SQL query to List departments with names longer than the average length

Departments Table (attributes: department_id, department_name)



For example:

Result
depar  department_name
-----  ---------------
5      Anesthesiologis

```

```sql
select department_id,department_name from Departments
where LENGTH(department_name) >(select AVG(LENGTH(department_name)) from Departments );
```

**Output:**

<img width="487" height="298" alt="image" src="https://github.com/user-attachments/assets/f287f6f8-3395-4d89-964f-84b2791d6aad" />


**Question 10**
```
Write a SQL query that retrieves the names of students and their corresponding grades, where the grade is equal to the minimum grade achieved in each subject.

Sample table: GRADES (attributes: student_id, student_name, subject, grade)



For example:

Result
student_name     grade
---------------  ---------------
Bob              85
Frank            85
John             85

```

```sql
select student_name,grade from GRADES g
where grade in (select MIN(grade) from GRADES where subject=g.subject);
```

**Output:**

<img width="608" height="325" alt="image" src="https://github.com/user-attachments/assets/3e7872be-b304-4c21-88f9-8c1b2423372a" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
