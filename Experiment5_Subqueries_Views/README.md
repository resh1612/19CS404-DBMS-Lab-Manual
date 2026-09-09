# Experiment 5: Subqueries and Views

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

<img width="846" height="521" alt="image" src="https://github.com/user-attachments/assets/6f9acc19-95c9-467b-87d6-16bec3f34c6f" />


```sql
-- select * from GRADES g where grade = ( select min(grade) from GRADES where subject = g.subject);
```

**Output:**

<img width="848" height="426" alt="image" src="https://github.com/user-attachments/assets/c7c22413-0a92-4c10-b9f8-814f99cea156" />




**Question 2**
---

<img width="824" height="436" alt="image" src="https://github.com/user-attachments/assets/c06d6a63-403d-4f75-bdc4-aebc39ad1916" />


```sql
-- select * from customer where city != ( select city from customer where id = (select max(id) from customer));
```

**Output:**

<img width="840" height="461" alt="image" src="https://github.com/user-attachments/assets/4245ab7b-4aa4-4a8c-ae4a-95890301d809" />


**Question 3**
---
<img width="793" height="488" alt="image" src="https://github.com/user-attachments/assets/1c37fd52-e09b-48d1-b83f-c9ffb87ec08a" />


```sql
-- SELECT commission 
FROM salesman 
WHERE salesman_id IN (
    SELECT salesman_id 
    FROM customer 
    WHERE city = 'Paris'
);

```

**Output:**

<img width="301" height="290" alt="image" src="https://github.com/user-attachments/assets/cec22df3-76a1-47b7-a0c6-6c2778deb856" />


**Question 4**
---
-- <img width="718" height="526" alt="image" src="https://github.com/user-attachments/assets/37662707-9d07-4b53-8afc-cde246954783" />


```sql
-- select * from CUSTOMERS where salary > 1500;
```

**Output:**

<img width="871" height="450" alt="image" src="https://github.com/user-attachments/assets/2e8aa75f-c804-457e-9d54-999c3d7bdb88" />


**Question 5**
---
<img width="706" height="481" alt="image" src="https://github.com/user-attachments/assets/d5267aae-8f81-4a6b-81e4-83a06d89a733" />


```sql
-- select * from CUSTOMERS where SALARY > 4500;
```

**Output:**

<img width="863" height="389" alt="image" src="https://github.com/user-attachments/assets/9d67bbcf-a9ef-40c4-89f4-922ed6412477" />


**Question 6**
---
<img width="822" height="326" alt="image" src="https://github.com/user-attachments/assets/f2ad19c4-bfa6-47bd-b885-b23993e396db" />


```sql
-- select department_id,department_name from Departments where length(department_name) > ( select avg(length(department_name)) from Departments);
```

**Output:**

<img width="419" height="336" alt="image" src="https://github.com/user-attachments/assets/d69dea36-2b60-4420-9c63-2233084d7c54" />


**Question 7**
---
<img width="682" height="454" alt="image" src="https://github.com/user-attachments/assets/84701f14-c367-4330-b0bc-fae24c395119" />


```sql
-- select * from CUSTOMERS where ADDRESS = 'Delhi';
```

**Output:**

<img width="855" height="275" alt="image" src="https://github.com/user-attachments/assets/fd103ac9-8d8d-4585-ab93-f22ff90c2f44" />


**Question 8**
---
<img width="800" height="509" alt="image" src="https://github.com/user-attachments/assets/09d7da6a-7060-4706-84df-e3c7df5abf78" />


```sql
-- select * from customer where customer_id = ( select salesman_id from salesman where name = 'Mc Lyon') - 2001;
```

**Output:**

<img width="877" height="290" alt="image" src="https://github.com/user-attachments/assets/f5693f27-10e9-4725-bd9c-60a9863ea17e" />


**Question 9**
---
<img width="864" height="472" alt="image" src="https://github.com/user-attachments/assets/33167f2c-d689-46c2-8495-bb78f3ffbaa8" />


```sql
-- SELECT ord_no, purch_amt, ord_date, customer_id, salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM salesman
    WHERE name = 'Paul Adam'
);
```

**Output:**

<img width="852" height="332" alt="image" src="https://github.com/user-attachments/assets/dab0c11f-4b5e-4eb8-a8ae-e8cb8ea7d106" />


**Question 10**
---
<img width="859" height="469" alt="image" src="https://github.com/user-attachments/assets/0b9da7fa-0ad1-40a6-8f81-171ee2892c47" />


```sql
-- select student_name , grade  from GRADES g where grade = (select max(grade) from GRADES where subject = g.subject);
```

**Output:**

<img width="573" height="357" alt="image" src="https://github.com/user-attachments/assets/d890e010-32b9-436e-8024-63fe67a1a70c" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.

## GRADES

<img width="1343" height="409" alt="image" src="https://github.com/user-attachments/assets/15692adf-838d-4836-b108-79f9b60323c1" />

