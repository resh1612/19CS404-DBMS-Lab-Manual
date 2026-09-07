# Experiment 4: Aggregate Functions, Group By and Having Clause

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
--
-- Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

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


```sql
-- select max(age) - min(age) as age_difference from employee;
```

**Output:**

<img width="377" height="310" alt="image" src="https://github.com/user-attachments/assets/959765c1-0137-47f2-9348-35eeac6bcbb3" />

**Question 2**
---
-- Write a SQL query to find the youngest employee in the company?

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
Employee_Name  Age
-------------  ----------
Peter          32


```sql
-- select name as Employee_Name,age as Age from employee order by age ASC limit 1 ;
```

**Output:**

<img width="520" height="297" alt="image" src="https://github.com/user-attachments/assets/8ca27d50-0214-45c2-b9c0-4ac82b989c0c" />

**Question 3**
---
-- Write a SQL query to determine the number of customers who received at least one grade for their activity.

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

```sql
-- select count(*) as COUNT from customer where grade is not null;
```

**Output:**

<img width="335" height="302" alt="image" src="https://github.com/user-attachments/assets/84116db5-166f-46a3-8ee6-a33716888821" />

**Question 4**
---
-- <img width="812" height="430" alt="image" src="https://github.com/user-attachments/assets/0ffec6f6-1fc9-4120-be30-8bfe026f4e71" />


```sql
-- select DoctorID,count(*) as TotalAppointments from Appointments group by DoctorID;
```

**Output:**

<img width="585" height="505" alt="image" src="https://github.com/user-attachments/assets/c59459ba-fba8-4cb7-a774-68b14e035e31" />

**Question 5**
---
-- How many patients have insurance coverage valid in each year?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT
For example:

Result
ValidityYear  TotalPatients
------------  -------------
2024          3
2025          1
2027          4
2031          2

```sql
-- select strftime('%Y', ValidityPeriod) as ValidityYear , count(PatientID) as TotalPatients from Insurance group by strftime('%Y',ValidityPeriod);
```

**Output:**

<img width="523" height="303" alt="image" src="https://github.com/user-attachments/assets/c56c2639-d19a-4513-8bd9-1435e67575cb" />

**Question 6**
---
-- <img width="794" height="441" alt="image" src="https://github.com/user-attachments/assets/ffb5d878-bcd5-4a85-af84-24b8efc5fbab" />


```sql
-- select Frequency,count(*) as TotalPrescriptions from Prescriptions group by Frequency;
```

**Output:**

<img width="674" height="478" alt="image" src="https://github.com/user-attachments/assets/0a068781-cd46-4319-89cc-0b1e3b7bd858" />


**Question 7**
---
-- <img width="820" height="415" alt="image" src="https://github.com/user-attachments/assets/3aa8ba14-7706-4520-a70c-5053f1a79eed" />


```sql
-- select address,SUM(salary) from customer1 group by address having SUM(salary) > 2000;
```

**Output:**

<img width="521" height="391" alt="image" src="https://github.com/user-attachments/assets/83839a3d-f74d-41f8-a5a3-95d8c5c25281" />

**Question 8**
---
-- <img width="808" height="368" alt="image" src="https://github.com/user-attachments/assets/25af172f-f675-4391-8258-09a92e9733a1" />


```sql
-- SELECT category_id,AVG(Price) FROM products GROUP BY category_id HAVING AVG(Price) BETWEEN 10 AND 15;
```

**Output:**

<img width="553" height="313" alt="image" src="https://github.com/user-attachments/assets/8047bd06-1bb0-47c5-89f5-b38ca5bc9e38" />


**Question 9**
---
-- <img width="815" height="379" alt="image" src="https://github.com/user-attachments/assets/66540959-391a-4e3d-b449-75d02671ad67" />


```sql
-- SELECT category_id,
       MIN(Price) AS Price
FROM products
GROUP BY category_id
HAVING MIN(Price) < 10;
```

**Output:**

<img width="521" height="356" alt="image" src="https://github.com/user-attachments/assets/387a666c-8ceb-41f0-92f4-ca62ffd6815f" />


**Question 10**
---
-- <img width="821" height="369" alt="image" src="https://github.com/user-attachments/assets/3625e9cc-3873-4145-a3e9-4c9a46529ed3" />


```sql
-- SELECT jdate,
       AVG(workhour)
FROM employee1
GROUP BY jdate
HAVING AVG(workhour) < 10;
```

**Output:**

<img width="573" height="317" alt="image" src="https://github.com/user-attachments/assets/b70ba40a-15cf-4815-9f1c-a3fcbed89d38" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
