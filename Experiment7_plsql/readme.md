# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

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

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

### Code :

```
DECLARE
    a INTEGER;
    b INTEGER;
BEGIN
    a := 80;
    b := 50;

    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
/
```

**Expected Output:**  
Greater number is: 80 

### OUTPUT 

<img width="951" height="478" alt="image" src="https://github.com/user-attachments/assets/6a288796-3c5f-47a1-816d-40a437ec8853" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

### Code:

```
DECLARE
    n INTEGER;
    i INTEGER;
    sum INTEGER;
BEGIN
    n := 10;
    i := 1;
    sum := 0;

    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
/
```

**Expected Output:**  
Sum of first 10 natural numbers is: 55

### OUTPUT 

<img width="820" height="466" alt="image" src="https://github.com/user-attachments/assets/67ddcee5-1a92-42d6-9fbf-c27a257e04bd" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

### Code 
```
DECLARE
    n INTEGER;
    a INTEGER;
    b INTEGER;
    c INTEGER;
    i INTEGER;
BEGIN
    n := 7;
    a := 0;
    b := 1;

    DBMS_OUTPUT.PUT('Fibonacci sequence: ');

    FOR i IN 1..n LOOP
        DBMS_OUTPUT.PUT(a);

        IF i < n THEN
            DBMS_OUTPUT.PUT(', ');
        END IF;

        c := a + b;
        a := b;
        b := c;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;
/
```

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

### OUTPUT

<img width="810" height="416" alt="image" src="https://github.com/user-attachments/assets/9973de39-205d-4c63-b141-a6d8aa292622" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

### Code 

```
DECLARE
    n INTEGER;
    rev INTEGER;
    digit INTEGER;
BEGIN
    n := 1535;
    rev := 0;

    WHILE n > 0 LOOP
        digit := MOD(n, 10);
        rev := rev * 10 + digit;
        n := TRUNC(n / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;
/
```


**Expected Output:**  
n = 1535  
Reversed number is 5351

### OUTPUT 

<img width="775" height="432" alt="image" src="https://github.com/user-attachments/assets/617f8e87-522e-40a1-8fc3-ec3b3a138fc4" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

### Code 
 ```
DECLARE
    a INTEGER;
    b INTEGER;
    c INTEGER;
    largest INTEGER;
BEGIN
    a := 10;
    b := 9;
    c := 15;

    IF a >= b AND a >= c THEN
        largest := a;
    ELSIF b >= a AND b >= c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || largest);
END;
/
```

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

### OUTPUT 

<img width="801" height="425" alt="image" src="https://github.com/user-attachments/assets/51efcafe-7473-4372-9392-14e69e23dafc" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
