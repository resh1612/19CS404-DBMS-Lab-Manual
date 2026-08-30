# Experiment 8: PL/SQL Cursor Programs

## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: When no rows are fetched.
2. **OTHERS**: Any other unexpected errors during execution.

**Steps:**

- Create an `employees` table with fields `emp_id`, `emp_name`, and `designation`.
- Insert some sample data into the table.
- Use a simple cursor to fetch and display employee names and designations.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Code:**
```
SET SERVEROUTPUT ON;

CREATE TABLE employees (
    emp_id NUMBER,
    emp_name VARCHAR2(50),
    designation VARCHAR2(50)
);

INSERT INTO employees VALUES (1, 'Rahul', 'Manager');
INSERT INTO employees VALUES (2, 'Priya', 'Developer');
INSERT INTO employees VALUES (3, 'Arun', 'Tester');

COMMIT;

DECLARE
    CURSOR emp_cursor IS
        SELECT emp_name, designation
        FROM employees;

    v_emp_name employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_emp_name, v_designation;
        EXIT WHEN emp_cursor%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE(
            'Name: ' || v_emp_name ||
            ', Designation: ' || v_designation
        );
    END LOOP;

    IF emp_cursor%ROWCOUNT = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

    CLOSE emp_cursor;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/
```

**Output:**  

<img width="736" height="417" alt="image" src="https://github.com/user-attachments/assets/f932a00d-bb17-4ad0-aac3-ba1111f21ae7" />

---

### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees meet the salary criteria.
2. **OTHERS**: For any unexpected errors during the execution.

**Steps:**

- Modify the `employees` table by adding a `salary` column.
- Insert sample salary values for the employees.
- Use a parameterized cursor to accept a salary range as input and fetch employees within that range.
- Implement exception handling to catch and display relevant error messages.

**Code:** 
```
SET SERVEROUTPUT ON;

ALTER TABLE employees ADD salary NUMBER;

UPDATE employees SET salary = 50000 WHERE emp_id = 1;
UPDATE employees SET salary = 40000 WHERE emp_id = 2;
UPDATE employees SET salary = 30000 WHERE emp_id = 3;

COMMIT;

DECLARE
    CURSOR emp_cursor(p_min_salary NUMBER, p_max_salary NUMBER) IS
        SELECT emp_name, designation, salary
        FROM employees
        WHERE salary BETWEEN p_min_salary AND p_max_salary;

    v_emp_name employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
    v_salary employees.salary%TYPE;
BEGIN
    OPEN emp_cursor(30000, 45000);

    LOOP
        FETCH emp_cursor INTO v_emp_name, v_designation, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE(
            'Name: ' || v_emp_name ||
            ', Designation: ' || v_designation ||
            ', Salary: ' || v_salary
        );
    END LOOP;

    IF emp_cursor%ROWCOUNT = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

    CLOSE emp_cursor;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the given salary range.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/
```
**Output:**  

<img width="885" height="424" alt="image" src="https://github.com/user-attachments/assets/e060fb84-8b27-41a3-b396-aa66698cd95a" />

---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no employees are found in the database.
2. **OTHERS**: For any other unexpected errors.

**Steps:**

- Modify the `employees` table by adding a `dept_no` column.
- Insert sample department numbers for employees.
- Use a cursor FOR loop to fetch and display employee names along with their department numbers.
- Implement exception handling to catch the relevant exceptions.

**Code:**

```
SET SERVEROUTPUT ON;

ALTER TABLE employees ADD dept_no NUMBER;

UPDATE employees SET dept_no = 10 WHERE emp_id = 1;
UPDATE employees SET dept_no = 20 WHERE emp_id = 2;
UPDATE employees SET dept_no = 10 WHERE emp_id = 3;

COMMIT;

DECLARE
    CURSOR emp_cursor IS
        SELECT emp_name, dept_no
        FROM employees;

    v_count NUMBER := 0;
BEGIN
    FOR emp IN emp_cursor LOOP
        DBMS_OUTPUT.PUT_LINE(
            'Name: ' || emp.emp_name ||
            ', Department: ' || emp.dept_no
        );

        v_count := v_count + 1;
    END LOOP;

    IF v_count = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/
```
**Output:**  

<img width="818" height="431" alt="image" src="https://github.com/user-attachments/assets/36ee9210-bfc6-4630-ae66-99dfd61e9b9f" />

---

### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees are found in the database.
2. **OTHERS**: For any other errors that occur.

**Steps:**

- Modify the `employees` table by adding `emp_id`, `emp_name`, `designation`, and `salary` fields.
- Insert sample data into the `employees` table.
- Declare a cursor using `%ROWTYPE` to fetch complete rows from the `employees` table.
- Implement exception handling to catch the relevant exceptions and display appropriate messages.

**Code:** 

```
SET SERVEROUTPUT ON;

DECLARE
    CURSOR emp_cursor IS
        SELECT emp_id, emp_name, designation, salary
        FROM employees;

    v_emp emp_cursor%ROWTYPE;
BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_emp;
        EXIT WHEN emp_cursor%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE(
            'ID: ' || v_emp.emp_id ||
            ', Name: ' || v_emp.emp_name ||
            ', Designation: ' || v_emp.designation ||
            ', Salary: ' || v_emp.salary
        );
    END LOOP;

    IF emp_cursor%ROWCOUNT = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

    CLOSE emp_cursor;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/
```

**Output:**  

<img width="781" height="430" alt="image" src="https://github.com/user-attachments/assets/1768c567-469a-4af7-bb4b-bccdd6dd3f2f" />

---

### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no rows are affected by the update.
2. **OTHERS**: For any unexpected errors during execution.

**Steps:**

- Modify the `employees` table to include a `dept_no` and `salary` field.
- Insert sample data into the `employees` table with different department numbers.
- Use a cursor with the `FOR UPDATE` clause to lock the rows of employees in a specific department and update their salary.
- Implement exception handling to handle `NO_DATA_FOUND` or other errors that may occur.

**Code:** 

```
SET SERVEROUTPUT ON;

DECLARE
    CURSOR emp_cursor IS
        SELECT emp_id, salary
        FROM employees
        WHERE dept_no = 10
        FOR UPDATE;

    v_emp_id employees.emp_id%TYPE;
    v_salary employees.salary%TYPE;
    v_count NUMBER := 0;
BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_emp_id, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;

        UPDATE employees
        SET salary = salary + 5000
        WHERE CURRENT OF emp_cursor;

        v_count := v_count + 1;

        DBMS_OUTPUT.PUT_LINE(
            'Employee ID: ' || v_emp_id ||
            ', Old Salary: ' || v_salary ||
            ', New Salary: ' || (v_salary + 5000)
        );
    END LOOP;

    CLOSE emp_cursor;

    IF v_count = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

    COMMIT;

    DBMS_OUTPUT.PUT_LINE('Salary updated successfully.');

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the specified department.');
    WHEN OTHERS THEN
        ROLLBACK;
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
/
```
**Output:**  

<img width="1000" height="436" alt="image" src="https://github.com/user-attachments/assets/1e0ff210-db0c-45c1-95ea-65685db5fdde" />

---

## RESULT
Thus, the program successfully executed and displayed employee details using a cursor. 

