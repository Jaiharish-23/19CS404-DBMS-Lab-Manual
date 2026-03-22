# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

**Expected Output:**  
Square of 6 is 36

```sql
CREATE OR REPLACE PROCEDURE find_square(p_number IN NUMBER) IS
    v_square NUMBER;
BEGIN
    v_square := p_number * p_number;
    DBMS_OUTPUT.PUT_LINE('Square of ' || p_number || ' is ' || v_square);
END;
/
SET SERVEROUTPUT ON;

BEGIN
    find_square(6);
END;
/
```
<img width="586" height="144" alt="image" src="https://github.com/user-attachments/assets/6bb1e1e0-894c-4381-b59e-cc916415e573" />


---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

**Expected Output:**  
Factorial of 5 is 120
```sql
SET SERVEROUTPUT ON;


CREATE OR REPLACE FUNCTION get_factorial(p_number IN NUMBER)
RETURN NUMBER
IS
   v_result NUMBER := 1;
BEGIN
   IF p_number < 0 THEN
      RETURN NULL;  
   END IF;

   FOR i IN 1..p_number LOOP
      v_result := v_result * i;
   END LOOP;

   RETURN v_result;
END;
/

DECLARE
   v_input NUMBER := 5;
   v_output NUMBER;
BEGIN
   v_output := get_factorial(v_input);
   DBMS_OUTPUT.PUT_LINE('Factorial of ' || v_input || ' is ' || v_output);
END;
/
```

<img width="561" height="149" alt="image" src="https://github.com/user-attachments/assets/11a4f752-afec-4d7d-9845-be4e9a5e3927" />


---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even

```sql
SET SERVEROUTPUT ON;


CREATE OR REPLACE PROCEDURE check_even_odd(p_number IN NUMBER) IS
BEGIN
  
   IF MOD(p_number, 2) = 0 THEN
      DBMS_OUTPUT.PUT_LINE(p_number || ' is Even');
   ELSE
      DBMS_OUTPUT.PUT_LINE(p_number || ' is Odd');
   END IF;
END;
/

BEGIN
   check_even_odd(12);  
END;
/
```

<img width="517" height="147" alt="image" src="https://github.com/user-attachments/assets/8a519f86-3c00-414d-bd66-a0a298a8d50a" />


---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Expected Output:**  
Reversed number of 1234 is 4321

```sql
CREATE OR REPLACE FUNCTION reverse_number(p_number IN NUMBER)
RETURN NUMBER IS
    v_number     NUMBER := p_number;
    v_reversed   NUMBER := 0;
    v_digit      NUMBER;
BEGIN
    WHILE v_number > 0 LOOP
        v_digit := MOD(v_number, 10);
        v_reversed := (v_reversed * 10) + v_digit;
        v_number := TRUNC(v_number / 10);
    END LOOP;
    RETURN v_reversed;
END;
/
SET SERVEROUTPUT ON;

DECLARE
    v_input    NUMBER := 1234;
    v_result   NUMBER;
BEGIN
    v_result := reverse_number(v_input);
    DBMS_OUTPUT.PUT_LINE('Reversed number of ' || v_input || ' is ' || v_result);
END;
/
```

<img width="713" height="141" alt="image" src="https://github.com/user-attachments/assets/0d9f9da1-bcd6-4e87-8588-f0f488d29d78" />


---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

```sql
CREATE OR REPLACE PROCEDURE print_table(p_number IN NUMBER) IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || p_number || ':');
    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(p_number || ' x ' || i || ' = ' || (p_number * i));
    END LOOP;
END;
/
SET SERVEROUTPUT ON;

BEGIN
    print_table(5);
END;
/
```

<img width="726" height="329" alt="image" src="https://github.com/user-attachments/assets/eda1a0c5-2195-423e-a364-5d3dcd407469" />


## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
