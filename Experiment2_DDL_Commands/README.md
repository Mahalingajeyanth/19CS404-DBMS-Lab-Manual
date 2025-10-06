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

**Question 1**
--
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
For example:

Test	Result
INSERT INTO ProjectAssignments (AssignmentID, EmployeeID, ProjectID, AssignmentDate) VALUES (2, 99, 1, '2024-01-03');
Error: FOREIGN KEY constraint failed


```sql
create table ProjectAssignments(
AssignmentID integer primary key,
EmployeeID integer,
ProjectID integer,
AssignmentDate date not null,
foreign key (EmployeeID) references Employees(EmployeeID)
foreign key (ProjectID) references projects(ProjectID)
);
```

**Output:**
<img width="1463" height="718" alt="Screenshot 2025-10-06 133706" src="https://github.com/user-attachments/assets/d512d809-49fa-4ffd-b284-db5dfdc8cbe2" />



**Question 2**
---
Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER
For example:

Test	Result
pragma table_info('Products');
cid   name        type        notnull     dflt_value  pk
----  ----------  ----------  ----------  ----------  ----------
0     ProductID   INTEGER     0                       0
1     ProductNam  TEXT        0                       0
2     Price       REAL        0                       0
3     Stock       INTEGER     0                       0


```sql
CREATE TABLE Products(
ProductID INTEGER,
ProductName TEXT,
Price REAL,
Stock INTEGER
);
```

**Output:**

<img width="1468" height="800" alt="Screenshot 2025-10-06 133723" src="https://github.com/user-attachments/assets/1facdeea-d9db-45d3-ac6e-a6b6e85207ce" />


**Question 3**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

For example:

Test	Result
select * from Customers;
CustomerID  Name             Address         Email
----------  ---------------  --------------  ---------------------
301         Michael Johnson  123 Elm Street  michael.j@example.com
302         Sarah Lee        456 Oak Avenue  sarah.lee@example.com
303         David Wilson     789 Pine Road   david.w@example.com


```sql
insert into customers(CustomerID, Name, Address, Email)
select CustomerID, Name, Address, Email
from Old_customers
```

**Output:**

<img width="1451" height="736" alt="Screenshot 2025-10-06 133741" src="https://github.com/user-attachments/assets/9ea496c8-0294-47d7-b7cd-a01b8ca98dde" />


**Question 4**
---
Write an SQL query to add a new column email of type TEXT to the Student_details table, and ensure that this column cannot contain NULL values and make default value as 'Invalid'

 

 

For example:

Test	Result
INSERT INTO Student_details (RollNo, Name, Gender, Subject, email) 
VALUES (1, 'John Doe', 'M', 'Math', 'john@example.com');
select * from Student_details;
RollN  Name   Gen  Subject     email
-----  -----  ---  ----------  ----------------
1      John   M    Math        john@example.com


```sql
alter table Student_details add column email TEXT not null default 'Invalid';
```

**Output:**

<img width="1156" height="693" alt="Screenshot 2025-10-06 133825" src="https://github.com/user-attachments/assets/7bca06fd-51a6-47c1-a6d2-a068164e3804" />


**Question 5**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.
For example:

Test	Result
INSERT INTO Bonuses (BonusID, EmployeeID, BonusAmount, BonusDate, Reason) VALUES (1, 6, 1000.0, '2024-08-01', 'Outstanding performance');
SELECT * FROM Bonuses;
BonusID     EmployeeID  BonusAmount  BonusDate   Reason
----------  ----------  -----------  ----------  -----------------------
1           6           1000.0       2024-08-01  Outstanding performance


```sql
create table Bonuses(
BonusID integer primary key,
EmployeeID integer,
BonusAmount real check(BonusAmount>0),
BonusDate date,
Reason text not null,
foreign key (EmployeeId) references Employees(EmployeeId)
);
```

**Output:**

<img width="1460" height="794" alt="Screenshot 2025-10-06 133842" src="https://github.com/user-attachments/assets/b691a064-6649-41f4-9c20-90dc8363f9a8" />


**Question 6**
---
Write a SQL query for adding a new column named "email" with the datatype VARCHAR(100) to the  table "customer" 

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
alter table  customer add column email VARCHAR(100)
```

**Output:**

<img width="1441" height="872" alt="Screenshot 2025-10-06 133901" src="https://github.com/user-attachments/assets/a57f9718-08b1-46c1-b124-723de9552676" />


**Question 7**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700


```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id)
    ON UPDATE SET NULL
    ON DELETE SET NULL
);
```

**Output:**
<img width="1369" height="837" alt="Screenshot 2025-10-06 133918" src="https://github.com/user-attachments/assets/dbc1f2a5-d6e2-425d-927d-b6036d662cca" />



**Question 8**
---
Insert a new product with ProductID 101, Name Laptop, Category Electronics, Price 1500, and Stock 50 into the Products table.

For example:

Test	Result
SELECT * FROM Products WHERE ProductID = 101;
ProductID   Name        Category     Price       Stock
----------  ----------  -----------  ----------  ----------
101         Laptop      Electronics  1500        50


```sql
insert into Products (ProductId,Name,Category,Price,Stock)
values(101,"Laptop","Electronics",1500,50);
```

**Output:**

<img width="1263" height="649" alt="Screenshot 2025-10-06 133934" src="https://github.com/user-attachments/assets/1cb5d5f7-63f0-4e7b-952b-6037f4cc06e6" />


**Question 9**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001
For example:

Test	Result
SELECT * FROM Customers;

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001


```sql
insert into Customers(CustomerId,Name,Address,City,Zipcode)
values(302,"Laura Croft","456 Elm St","Seattle",98101),(303,"Bruce Wayne","789 Oak St","Gotham",10001)
```

**Output:**

<img width="1298" height="796" alt="Screenshot 2025-10-06 133951" src="https://github.com/user-attachments/assets/29cf93aa-8b5d-42c4-af10-310614b35b0a" />


**Question 10**
---
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
For example:

Test	Result
INSERT INTO Attendance (AttendanceID, EmployeeID, AttendanceDate, Status) VALUES (1, 1, '2024-08-01', 'Present');
SELECT * FROM Attendance;
AttendanceID  EmployeeID  AttendanceDate  Status
------------  ----------  --------------  ----------
1             1           2024-08-01      Present


```sql
CREATE TABLE Attendance (
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1367" height="752" alt="Screenshot 2025-10-06 134006" src="https://github.com/user-attachments/assets/c8dcd663-c091-4eb7-b4b0-463793955eff" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
