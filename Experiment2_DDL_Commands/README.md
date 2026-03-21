# Experiment 2: DDL Commands
```
Developed by;
Name : JAI HARISH R
Reg No : 212224040124
```
## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
```
Write an SQL query to add two new columns, first_name and last_name, to the table employee. Both columns should have a data type of varchar(50).

For example:

Test	Result
pragma table_info('employee');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           salary      number      0                       0
2           first_name  varchar(50  0                       0
3           last_name   varchar(50  0                       0

```
***CODE :***
```sql
ALTER TABLE employee ADD first_name varchar(50) ; 
ALTER TABLE employee ADD last_name varchar(50) ; 
```

**Output:**
<img width="1131" height="184" alt="image" src="https://github.com/user-attachments/assets/581d3c1e-d963-4263-aa01-5b14d1d8a14a" />




**Question 2**
```
Insert a student with RollNo 201, Name David Lee, Gender M, Subject Physics, and MARKS 92 into the Student_details table.

For example:

Test	Result
SELECT * FROM Student_details WHERE RollNo = 201;
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
201         David Lee   M           Physics     92

```
***CODE :***
```sql
INSERT INTO Student_details VALUES (201,'David Lee','M','Physics',92);
```

**Output:**
<img width="1166" height="138" alt="image" src="https://github.com/user-attachments/assets/be37b5fd-9cd3-4b07-8068-8da8ca9a9dee" />


**Question 3**
```
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.
For example:

Test	Result
INSERT INTO Products
VALUES (1, NULL,0,5);
Error: NOT NULL constraint failed: Products.ProductName

```
***CODE :***
```sql
CREATE TABLE Products(
ProductID INTEGER PRIMARY KEY ,
ProductName TEXT NOT NULL ,
Price REAL,
Stock INTEGER,
CHECK (Price>0),
CHECK (Stock >=0));
```

**Output:**
<img width="1007" height="165" alt="image" src="https://github.com/user-attachments/assets/37a9f554-6079-43df-ab55-b72794152be0" />


**Question 4**

```
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

For example:

Test	Result
select * from Books;
ISBN            Title           Author              Publisher      YearPublished
--------------  --------------  ------------------  -------------  -------------
978-1234567890  The Lost World  Arthur Conan Doyle  Vintage Books  1912
978-0987654321  Gone with the   Margaret Mitchell   Macmillan      1936
978-1122334455  Moby Dick       Herman Melville     Harper & Brot  1851
```
***CODE :***
```sql
INSERT INTO Books (ISBN,Title,Author,Publisher,YearPublished)
SELECT * FROM  Out_of_print_books;
```

**Output:**
<img width="1209" height="166" alt="image" src="https://github.com/user-attachments/assets/86807bef-e671-42c2-9d91-af1ecdff25da" />


**Question 5**
```
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
For example:

Test	Result
INSERT INTO Department (DepartmentID, DepartmentName, Location) VALUES (1, 'Human Resources', 'New York');
select * from Department;
DepartmentID  DepartmentName   Location
------------  ---------------  ----------
1             Human Resources  New York
```
***CODE :***
```sql
CREATE TABLE  Department(
DepartmentID INTEGER ,
DepartmentName TEXT NOT NULL UNIQUE ,
Location TEXT ,
PRIMARY KEY (DepartmentID)
);
```

**Output:**
<img width="1212" height="128" alt="image" src="https://github.com/user-attachments/assets/eb2b3009-8e7f-40b7-bebf-f9abb1fbf2a0" />


**Question 6**
```
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.

 

 

For example:

Test	Result
pragma table_info('employees');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           name        TEXT        1                       0
2           salary      INTEGER     0                       0
```
***CODE :***
```sql
ALTER TABLE employees ADD salary INTEGER CHECK (salary>0);
```

**Output:**
<img width="1136" height="160" alt="image" src="https://github.com/user-attachments/assets/73edbd7c-53d5-42e7-b062-fcfb04f373fb" />


**Question 7**
```
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
For example:

Test	Result
-- Attempt to insert a record with NULL FirstName
INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, Salary, DepartmentID)
VALUES (1, NULL, 'Doe', 'john.doe@example.com', 50000, 1);
Error: NOT NULL constraint failed: Employees.FirstName

```
***CODE :***
```sql
create TABLE Employees(
EmployeeID NUMBER PRIMARY KEY,
FirstName TEXT NOT NULL,
LastName TEXT NOT NULL,
Email TEXT UNIQUE,
Salary INTEGER ,
DepartmentID INTEGER ,
FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID),
CHECK (Salary>0));
```

**Output:**
<img width="1275" height="257" alt="image" src="https://github.com/user-attachments/assets/d1dff717-e625-4be8-b563-6858941dee5f" />


**Question 8**
```
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700         COM5

```
***CODE :***
```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT not null ,
rate INTEGER not null,
icom_id VARCHAR(4),
FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE );
```

**Output:**
<img width="1089" height="217" alt="image" src="https://github.com/user-attachments/assets/a65feb77-a105-4c1e-9e9a-1097c4289ea9" />


**Question 9**
```
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
For example:

Test	Result
SELECT Name, Category, Price, Stock FROM Products;

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
```
***CODE :***

```sql
INSERT INTO Products (Name,Category,Price,Stock) VALUES
('Smartphone','Electronics',800,150),('Headphones','Accessories',200,300); 
```

**Output:**
<img width="1011" height="199" alt="image" src="https://github.com/user-attachments/assets/2d729ace-54f5-413e-bcca-f9a19752c37d" />


**Question 10**
```
Create a table named Members with the following columns:

MemberID as INTEGER
MemberName as TEXT
JoinDate as DATE
For example:

Test	Result
pragma table_info('Members');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           MemberID    INTEGER     0                       0
1           MemberName  TEXT        0                       0
2           JoinDate    DATE        0                       0

```
***CODE :***
```sql
CREATE TABLE Members(
MemberID INTEGER ,
MemberName TEXT,
JoinDate DATE );
```

**Output:**
<img width="1274" height="226" alt="image" src="https://github.com/user-attachments/assets/4b670dc1-7270-49e9-ae70-512ef5cb7600" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
