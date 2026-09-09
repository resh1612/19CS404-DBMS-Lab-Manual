# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**

<img width="856" height="520" alt="image" src="https://github.com/user-attachments/assets/ab24c991-75d5-4264-9e2e-03fb7d16e4c4" />


```sql
--
SELECT p.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'X-Ray' AND t.result = 'Normal';

```

**Output:**

<img width="843" height="396" alt="image" src="https://github.com/user-attachments/assets/c78a42df-0d8f-4f27-b5cb-ad891b4fd8ff" />


**Question 2**

<img width="829" height="527" alt="image" src="https://github.com/user-attachments/assets/b80af9c8-f3b3-4dae-a293-326e4357cd9f" />


```sql
-- select s.name from Salesman s LEFT JOIN Customer c ON s.salesman_id = c.salesman_id where c.city = 'London';
```

**Output:**

<img width="354" height="430" alt="image" src="https://github.com/user-attachments/assets/7e824953-2e9c-4de5-b13c-7524a49c84ea" />


**Question 3**

<img width="851" height="508" alt="image" src="https://github.com/user-attachments/assets/65c84ef0-5a70-461e-9ff6-1e3569a3ef7b" />


```sql
--
SELECT p.first_name AS patient_name, t.*
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';

```

**Output:**

<img width="830" height="388" alt="image" src="https://github.com/user-attachments/assets/d3a6d01e-9a33-47f3-b6db-32701842a30e" />


**Question 4**

<img width="854" height="559" alt="image" src="https://github.com/user-attachments/assets/71eeb484-0ef4-4fba-bcfa-c17cf616677c" />


```sql
--
SELECT 
    c.cust_name AS "Customer Name", 
    c.city AS "city", 
    s.name AS "Salesman", 
    s.city AS "city", 
    s.commission AS "commission"
FROM customer c
INNER JOIN salesman s ON c.salesman_id = s.salesman_id
WHERE c.city <> s.city 
  AND s.commission > 0.12;

```

**Output:**

<img width="874" height="438" alt="image" src="https://github.com/user-attachments/assets/79b1b8f6-a7ba-4bb0-9a50-9b1626751bc4" />


**Question 5**

<img width="809" height="405" alt="image" src="https://github.com/user-attachments/assets/130f9b68-8c5f-4671-85a0-4305786004b9" />


```sql
--
SELECT c.cust_name
FROM orders o
LEFT JOIN customer c ON o.customer_id = c.customer_id
WHERE o.purch_amt < 100;

```

**Output:**

<img width="355" height="343" alt="image" src="https://github.com/user-attachments/assets/d86b977b-6bfe-4333-916b-5ed8447d583c" />

**Question 6**

<img width="858" height="428" alt="image" src="https://github.com/user-attachments/assets/eef322d0-98c2-4d86-9574-7d159b003e1a" />


```sql
-- select n.*, d.department_name from nurses n inner join departments d on n.department_id = d.department_id;
```

**Output:**

<img width="883" height="407" alt="image" src="https://github.com/user-attachments/assets/b2ca4864-65fe-4b87-9586-bdb64f2e7587" />

**Question 7**

SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
For example:

Result
cust_name        city             ord_no           ord_date         Order Amount  name        commission
---------------  ---------------  ---------------  ---------------  ------------  ----------  ----------
Nick Rimando     Chennai          70002            2012-10-05       65.26         Bob Emily   0.15
Nick Rimando     Chennai          70008            2012-09-10       5760.0        Bob Emily   0.15
Nick Rimando     Chennai          70013            2012-04-25       3045.6        Bob Emily   0.15
Graham Zusi      California       70001            2012-10-05       150.5         Nail Knite  0.13
Graham Zusi      California       70007            2012-09-10       948.5         Nail Knite  0.13
Brad Guzan       London           70009            2012-09-10       270.65        Pit Alex    0.11
Fabian Johns     Paris            70010            2012-10-10       1983.43       Mc Lyon     0.14
Brad Davis       New York         70005            2012-07-27       2400.6        Bob Emily   0.15
Geoff Cameron    Berlin           70003            2012-10-10       2480.4        Lauson Hen  0.12
Geoff Cameron    Berlin           70004            2012-08-17       110.5         Lauson Hen  0.12
Julian Green     London           70012            2012-06-27       250.45        Nail Knite  0.13
Jozy Altidore    Moscow           70011            2012-08-17       75.29         Paul Adam   0.13


```sql
--
SELECT 
    c.cust_name, 
    c.city, 
    o.ord_no, 
    o.ord_date, 
    o.purch_amt AS "Order Amount", 
    s.name, 
    s.commission
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
LEFT JOIN salesman s ON c.salesman_id = s.salesman_id;

```

**Output:**

<img width="879" height="549" alt="image" src="https://github.com/user-attachments/assets/38bcc490-e1a2-43e5-85d4-cecb13c1ae5f" />

**Question 8**

<img width="889" height="360" alt="image" src="https://github.com/user-attachments/assets/afff6564-4491-444c-8773-05c3fdb887f0" />


```sql
--
SELECT p.first_name AS patient_name
FROM patients p
INNER JOIN test_results t ON p.patient_id = t.patient_id
WHERE t.test_name = 'Blood Pressure';


```

**Output:**

<img width="271" height="278" alt="image" src="https://github.com/user-attachments/assets/412638e2-b1f6-4528-8236-7ef915fcb5fd" />


**Question 9**

write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
For example:

Result
Salesman         cust_name        city
---------------  ---------------  ---------------
Bob Emily        Brad Davis       New York
Nail Knite       Fabian Johns     Paris
Pit Alex         Brad Guzan       London
Pit Alex         Julian Green     London
Mc Lyon          Fabian Johns     Paris


```sql
--
SELECT 
    s.name AS "Salesman", 
    c.cust_name, 
    c.city
FROM salesman s
INNER JOIN customer c ON s.city = c.city;


```

**Output:**

<img width="680" height="417" alt="image" src="https://github.com/user-attachments/assets/1630ec18-16c3-46cd-8be2-90bdfa77d506" />

**Question 10**

<img width="842" height="496" alt="image" src="https://github.com/user-attachments/assets/fc72988d-f998-404c-8f83-26abd91fefdf" />


```sql
--
SELECT p.*, d.specialization AS doctor_specialization
FROM patients p
INNER JOIN doctors d ON p.doctor_id = d.doctor_id;

```

**Output:**

<img width="891" height="396" alt="image" src="https://github.com/user-attachments/assets/c0bb45e4-e4c8-42ef-bff0-bc327ebd4de4" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.

## GRADES

<img width="1345" height="439" alt="image" src="https://github.com/user-attachments/assets/2d5fcff5-e37e-4288-bf2e-57e4f7959211" />

