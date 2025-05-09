# Experiment 2: DDL Commands

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
## PROGRAMS :
**Question 1**
--
Create a table named Events with the following columns:

- EventID as INTEGER
- EventName as TEXT
- EventDate as DATE
### Code:
```sql
create table Events
(EventID INTEGER,
EventName TEXT,
EventDate DATE);
```

**Output:**

![image](https://github.com/user-attachments/assets/efd719e3-ec81-4b6e-b3d5-7747219fbfc4)


**Question 2**
---
- Insert all customers from Old_customers into Customers

- Table attributes are CustomerID, Name, Address, Email
### Code:
```sql
insert into Customers (CustomerID , Name,Address,Email)
select CustomerID,Name ,Address , Email from Old_customers;
```

**Output:**

![image](https://github.com/user-attachments/assets/c25f78f4-b6c3-47a7-832b-c51ccb7d361e)

**Question 3**
---
- Create a table named Locations with the following columns:

- LocationID as INTEGER
- LocationName as TEXT
- Address as TEXT
### Code:
```sql
create table Locations
(LocationID INTEGER,
LocationName TEXT,
Address TEXT);
```

**Output:**

![image](https://github.com/user-attachments/assets/4fe5e477-db2f-4a54-b61d-f5b84c00c9c3)


**Question 4**
---
- Create a table named Invoices with the following constraints:
- InvoiceID as INTEGER should be the primary key.
- InvoiceDate as DATE.
- Amount as REAL should be greater than 0.
- DueDate as DATE should be greater than the InvoiceDate.
- OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
### Code:
```sql
create table Invoices
(InvoiceID INTEGER primary key,
InvoiceDate DATE,
Amount REAL check(Amount>0),
DueDate DATE check(DueDate>InvoiceDate),
OrderID INTEGER,
foreign key(OrderID) references Orders(OrderID));
```

**Output:**

![image](https://github.com/user-attachments/assets/a05fed85-bff0-4886-9aca-4e4ae7104b29)


**Question 5**
---
- Create a table named Products with the following columns:

- ProductID as INTEGER
- ProductName as TEXT
- Price as REAL
- Stock as INTEGER
### Code:
```sql
create table Products
(ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER);
```

**Output:**

![image](https://github.com/user-attachments/assets/b3f61aba-b15b-46f3-9f94-37d17a88ba3e)



**Question 6**
---
- Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
### Code:
```sql
create table Attendance
(AttendanceID INTEGER primary key,
EmployeeID INTEGER,
AttendanceDate DATE,
Status TEXT check(status in ('Present' , 'Absent' ,  'Leave')),
foreign key(EmployeeID) references Employees(EmployeeID));
```

**Output:**

![image](https://github.com/user-attachments/assets/882cb770-ef5c-4491-8dad-c9106979ad76)


**Question 7**
---
```
Insert the following students into the Student_details table:
RollNo      Name        Gender      Subject     MARKS
----------  ----------  ----------  ----------  ----------
202            Ella King         F           Chemistry   87
203            James Bond   M          Literature    78
```
### Code:
```sql
insert into Student_details (RollNo,Name,Gender,Subject,MARKS) values
(202,'Ella King','F','Chemistry',87),
(203,'James Bond','M','Literature',78);
```

**Output:**

![image](https://github.com/user-attachments/assets/f40090a0-04a9-48af-a8e2-40a8132165dd)


**Question 8**
---
- Write an SQL query to add two new columns, designation and net_salary, to the table Companies. The designation column should have a data type of varchar(50), and the net_salary column should have a data type of number.
### Code:
```sql
alter table Companies
add column designation varchar(50);
alter table Companies
add column net_salary number;

```

**Output:**

![image](https://github.com/user-attachments/assets/e5369b52-585f-4c89-bc61-6613b09c15be)


**Question 9**
---
```
 Insert the following products into the Products table:

 Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
```
### Code:
```sql
insert into Products
(Name,Category,Price,Stock) values
('Smartphone','Electronics',800,150),
('Headphones','Accessories',200,300);
```

**Output:**

![image](https://github.com/user-attachments/assets/b25bfcd5-2cb9-4150-82ce-768605f82cc3)


**Question 10**
---
```
Write a SQL query to Add a new column Mobilenumber as number in the Student_details table.

 Sample table: Student_details

 cid              name             type             notnu  dflt_value  pk
 ---------------  ---------------  ---------------  -----  ----------  ----------
 0                RollNo           int              0                  1
 1                Name             VARCHAR(100)     1                  0
 2                Gender           TEXT             1                  0
 3                Subject          VARCHAR(30)      0                  0
 4                MARKS            INT (3)          0                  0

```
### Code:
```sql
alter table Student_details
add column  Mobilenumber number; 
```

**Output:**

![image](https://github.com/user-attachments/assets/ab702d54-ed70-40da-988f-e0cf946ed1ae)


**GRADE:**
![image](https://github.com/user-attachments/assets/7d67df86-0413-4171-8c2a-fc1b27adf36b)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
