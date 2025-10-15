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
--
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

For example:

Test	Result
select changes();
changes()
----------
1


```sql
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;
```

**Output:**

<img width="1444" height="779" alt="image" src="https://github.com/user-attachments/assets/0335ec54-2101-4d9e-92ff-88de812e0105" />


**Question 2**
---
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

<img width="1468" height="660" alt="image" src="https://github.com/user-attachments/assets/37136011-dcfe-4e56-83ea-5ef66c9add84" />


**Question 3**
---
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

```sql
UPDATE products
SET quantity = quantity * 1.10;
```

**Output:**
<img width="1407" height="867" alt="image" src="https://github.com/user-attachments/assets/5ea8e71b-1ec6-4309-9ddd-ff8c450b3ab6" />



**Question 4**
---
For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)
For example:

Test	Result
select changes();
changes()
----------
1


```sql
UPDATE sales
SET sell_price = sell_price + 3
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE supplier_id = 4
);
```

**Output:**

<img width="1447" height="915" alt="image" src="https://github.com/user-attachments/assets/9a7aa770-01f5-4314-9d2a-f3742afc3122" />


**Question 5**
---
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


```sql
UPDATE products
SET reorder_lvl = reorder_lvl * 1.30
WHERE category = 'Food'
  AND quantity < (reorder_lvl * 0.5);
```

**Output:**

<img width="1421" height="856" alt="image" src="https://github.com/user-attachments/assets/fad97bf4-5bdd-42cb-bc6c-3a170376afd8" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is not equal to 3.

```sql
DELETE FROM customer
WHERE grade <> 3;
```

**Output:**

<img width="1219" height="960" alt="image" src="https://github.com/user-attachments/assets/9a681ffb-7896-49ed-a312-126505ece76a" />


**Question 7**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',
3.       11000            PPHGRTS     A010

```sql
DELETE FROM customer
WHERE cust_country = 'India'
  AND cust_city <> 'Chennai';
```

**Output:**

<img width="1448" height="968" alt="image" src="https://github.com/user-attachments/assets/5947f91c-7309-4146-8646-c0869b8d3a81" />


**Question 8**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000

```sql
DELETE FROM customer
WHERE opening_amt BETWEEN 4000 AND 6000;
```

**Output:**

<img width="1363" height="449" alt="image" src="https://github.com/user-attachments/assets/be5552ae-1fee-41f7-80b8-42c97840e0bc" />


**Question 9**
---
Write a SQL query to Delete customers with 'GRADE' 2 and 'CUST_NAME' starting with 'M', and whose 'PAYMENT_AMT' is less than 3000

```sql
DELETE FROM customer
WHERE grade = 2
  AND cust_name LIKE 'M%'
  AND payment_amt < 3000;
```

**Output:**

<img width="1387" height="807" alt="image" src="https://github.com/user-attachments/assets/7e305072-4a3f-4e1b-9294-155dae6196e8" />


**Question 10**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

```sql
DELETE FROM doctors
WHERE last_name = 'Brown'
  AND specialization IN ('Pediatrics', 'Cardiology')
```

**Output:**

<img width="1256" height="880" alt="image" src="https://github.com/user-attachments/assets/9493c1f5-f209-4064-8b19-1d0594237890" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
