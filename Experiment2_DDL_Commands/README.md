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

-- <img width="790" height="320" alt="image" src="https://github.com/user-attachments/assets/3b1f0aed-09c0-4e04-acd7-023c40588c5e" />


```sql
CREATE TABLE Events (EventID INTEGER , EventName TEXT , EventDate DATE);
```

**Output:**

<img width="850" height="361" alt="image" src="https://github.com/user-attachments/assets/c127d794-059d-40f4-b700-c27bea2a54e2" />

**Question 2**
---
<img width="854" height="289" alt="image" src="https://github.com/user-attachments/assets/42f2bb45-7d84-47e4-b050-aa6fc2337bba" />


```sql
CREATE TABLE ProjectAssignments (AssignmentID INTEGER PRIMARY KEY , EmployeeID INTEGER , ProjectID INTEGER , AssignmentDate DATE NOT NULL , FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID), FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID));
```

**Output:**

<img width="856" height="302" alt="image" src="https://github.com/user-attachments/assets/2b864919-23f6-4622-a8cd-4457116b75ba" />

**Question 3**
---
<img width="843" height="319" alt="image" src="https://github.com/user-attachments/assets/f4358094-a873-41ca-a49d-174e22874baa" />


```sql
ALTER TABLE Employees ADD COLUMN Date_of_joining Date ;
ALTER TABLE Employees RENAME COLUMN job_title TO Designation;
```

**Output:**

<img width="849" height="320" alt="image" src="https://github.com/user-attachments/assets/c9992f3e-2e42-4a23-832e-5a1a6e5ee1c9" />

**Question 4**
---
<img width="823" height="318" alt="image" src="https://github.com/user-attachments/assets/d9e422a3-d433-4c86-9074-106bf3b68d4f" />

```sql
CREATE TABLE Locations (LocationID INTEGER, LocationName TEXT , Address TEXT);
```

**Output:**

<img width="851" height="351" alt="image" src="https://github.com/user-attachments/assets/71964825-1456-4e2e-9517-c15347b53bbb" />

**Question 5**
---
<img width="828" height="366" alt="image" src="https://github.com/user-attachments/assets/8d757db6-deee-49ea-89a5-f7f192ba9a16" />

```sql
CREATE TABLE item( item_id TEXT PRIMARY KEY, item_desc TEXT NOT NULL , rate INTEGER NOT NULL, icom_id TEXT(4) , FOREIGN KEY (icom_id) REFERENCES company(com_id) ON UPDATE CASCADE ON DELETE CASCADE);
```

**Output:**

<img width="838" height="336" alt="image" src="https://github.com/user-attachments/assets/551582bf-58ff-4cec-8a00-c11364842b85" />

**Question 6**
---
<img width="844" height="336" alt="image" src="https://github.com/user-attachments/assets/52206b0e-b9f3-4e87-992a-ad1347089663" />

```sql
CREATE TABLE Invoices(InvoiceID INTEGER PRIMARY KEY,InvoiceDate DATE,Amount REAL CHECK (Amount > 0),DueDate DATE CHECK (DueDate >InvoiceDate), OrderID INTEGER , FOREIGN KEY (OrderID) REFERENCES Orders(OrderID) );
```

**Output:**

<img width="849" height="280" alt="image" src="https://github.com/user-attachments/assets/1fbb4fd7-8358-4345-bb81-d0cdff2cebbb" />



**Question 7**
---
<img width="837" height="209" alt="image" src="https://github.com/user-attachments/assets/b4ff144b-da14-459a-a55d-823e1b75ca99" />

```sql
INSERT INTO Student_details (RollNo, Name , Gender , Subject , MARKS ) VALUES (201 , 'David Lee','M','Physics', 92);
```

**Output:**

<img width="839" height="251" alt="image" src="https://github.com/user-attachments/assets/87405613-fe7e-4a57-a916-6d93438674c7" />

**Question 8**
---
<img width="602" height="275" alt="image" src="https://github.com/user-attachments/assets/300fb986-c659-4147-8f82-9a91ce651dda" />

```sql
INSERT INTO Products (ProductID, ProductName, Price, Stock)
SELECT ProductID, ProductName, Price, Stock
FROM Discontinued_products;
```

**Output:**

<img width="844" height="286" alt="image" src="https://github.com/user-attachments/assets/dde649f4-a82f-4b3e-9efb-d1ba20b0c24b" />

**Question 9**
---
<img width="842" height="341" alt="image" src="https://github.com/user-attachments/assets/f7a29931-7d57-4a34-a7bb-92d22f3d6ab6" />

```sql
ALTER TABLE Student_details ADD MobileNumber NUMBER ;
ALTER TABLE Student_details ADD Address VARCHAR(100);
```

**Output:**

<img width="841" height="359" alt="image" src="https://github.com/user-attachments/assets/9757f4d6-be23-4f22-bb42-df82ce37aa00" />

**Question 10**
---
<img width="562" height="268" alt="image" src="https://github.com/user-attachments/assets/bfe0fb92-2dd9-4b36-be48-f6d39b2888c3" />

```sql
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
Select EmployeeID, Name, Department, Salary from Former_employees;
```

**Output:**

<img width="836" height="283" alt="image" src="https://github.com/user-attachments/assets/4d0aad8c-1fb9-48ed-a68f-62a7631eb242" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

## GRADES 

<img width="1354" height="598" alt="image" src="https://github.com/user-attachments/assets/7673bf31-65d0-4689-ab90-cbb5a6bee8df" />

