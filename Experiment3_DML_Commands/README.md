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
<img width="595" height="426" alt="image" src="https://github.com/user-attachments/assets/915639c8-db01-4d66-bb90-e4f593f97b2a" />

```sql
delete from Surgeries where surgery_id = 3 ;
```

**Output:**

<img width="843" height="358" alt="image" src="https://github.com/user-attachments/assets/c7c3d97d-6e32-4548-97ef-13f941a1a9bb" />

**Question 2**
---
<img width="862" height="518" alt="image" src="https://github.com/user-attachments/assets/a7d5e64b-3d47-46a7-98fa-8db78de11e23" />

```sql
delete from Customer where GRADE == 2;
```

**Output:**

<img width="487" height="444" alt="image" src="https://github.com/user-attachments/assets/83e0a640-2ec4-479b-b6af-e2959e8e1b1d" />

**Question 3**
---
<img width="665" height="141" alt="image" src="https://github.com/user-attachments/assets/ac96b316-3215-4509-a8c2-d4653782d9ae" />

```sql
delete from Doctors where doctor_id = 1;
```

**Output:**

<img width="865" height="239" alt="image" src="https://github.com/user-attachments/assets/4c27b1c4-90de-40a4-86a4-3f8e33665ff9" />

**Question 4**
---
<img width="854" height="333" alt="image" src="https://github.com/user-attachments/assets/9e510a3a-08a2-42e1-a39b-ce52350b0160" />

```sql
select customer_id,cust_name,city,grade,salesman_id from customer where city = 'New York' OR grade <= 100 ;
```

**Output:**

<img width="872" height="351" alt="image" src="https://github.com/user-attachments/assets/e231272b-ff41-4fe5-af74-e57ca2510852" />

**Question 5**
---
<img width="828" height="444" alt="image" src="https://github.com/user-attachments/assets/07428286-77cc-4989-b1f7-2fd71466a798" />

```sql
select product_id, original_price, discount_percentage,(original_price * (1 - discount_percentage)) as discounted_price from Products where original_price between 50 and 150; 
```

**Output:**

<img width="858" height="265" alt="image" src="https://github.com/user-attachments/assets/ef204519-f394-445c-ab97-66cb30987201" />

**Question 6**
---
<img width="810" height="223" alt="image" src="https://github.com/user-attachments/assets/cf70d0db-96ee-4e7a-80e7-c52a85e831cf" />

```sql
update Products set sell_price = sell_price * 1.10 where category = 'Bakery';
```

**Output:**

<img width="875" height="431" alt="image" src="https://github.com/user-attachments/assets/23e2987a-d31d-4d0a-a7e9-5fd2f7c1c126" />

**Question 7**
---
<img width="851" height="438" alt="image" src="https://github.com/user-attachments/assets/e2f67942-62b3-446d-bf01-4c1f0ad696d5" />

```sql
update Employees set email = 'not available' , commission_pct = 0.55 where department_id = 110;
```

**Output:**

<img width="865" height="318" alt="image" src="https://github.com/user-attachments/assets/50633aa0-bdb1-44c3-9274-60dcc07b4c97" />

**Question 8**
---
<img width="803" height="385" alt="image" src="https://github.com/user-attachments/assets/8b439fc5-6274-4b6f-93e1-3ee2c77c4ed5" />

```sql
update Products set category = 'Household' where product_name like '%Detergent%' ;
```

**Output:**

<img width="865" height="408" alt="image" src="https://github.com/user-attachments/assets/1b9b49e8-483c-4bbf-92fd-c026d1a4e352" />

**Question 9**
---
<img width="556" height="267" alt="image" src="https://github.com/user-attachments/assets/07d2f51d-efd8-4bd7-aad6-c69e9193b5c2" />

```sql
select name , commission from salesman limit 5;
```

**Output:**

<img width="503" height="381" alt="image" src="https://github.com/user-attachments/assets/3276eb4b-af2a-4a14-ae82-ac7de976744b" />

**Question 10**
---
<img width="877" height="547" alt="image" src="https://github.com/user-attachments/assets/9fe926e0-7195-4e04-9db5-e2d7d972c49c" />


```sql
UPDATE Products
SET sell_price = CAST(cost_price * 1.35 AS INT)
WHERE ((sell_price - cost_price) * 100 / cost_price) < 30;
```

**Output:**

<img width="865" height="447" alt="image" src="https://github.com/user-attachments/assets/edbd6864-83b1-4ef8-8db5-d2e51f918243" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.

## GRADES

<img width="1345" height="600" alt="image" src="https://github.com/user-attachments/assets/a2a73861-9eea-43e5-9dc8-39e13c029e98" />


