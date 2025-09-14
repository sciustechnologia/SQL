### Problem 1:
* Display employees (first_name, last_name, salary, manager_id) not having a manager assigned.
* Deliverables: One query

```SQL
SELECT first_name, last_name, salary, manager_id
FROM employees
WHERE manager_id IS NULL;
```

### Xplanation

**not having a manager assigned** means an unknown or missing value - a `NULL` value. 
* We are not looking for zero (0) or an empty string (''), therefore standard comparison operators (`=` or `!=`) don't apply.
* `IS NULL` or `IS NOT NULL` operators
    * `IS NULL` checks if a column's value is missing.
    * `IS NOT NULL` checks if a column's value is present.

* **`WHERE` manager_id IS NULL**
  * filters the employees table to return only the rows where the value in the manager_id column is `NULL`, identifying employees who do not have a manager assigned.

***

### Problem 2:
* Display employees (first_name, last_name, salary, job_id) and order the resulting data set by job_id in ascending order and salary in descending order.
* Deliverables: One query

```SQL
SELECT first_name, last_name, salary, job_id
FROM employees
ORDER BY job_id ASC, salary DESC;
```

### Xplanation

* `ORDER BY` clause sorts the result set of a query. 
  * to sort by more than one column, I list the columns in the order I want the sorting to be applied.

* **ORDER BY job_id ASC**:
  * First sort all rows based on the values in the job_id column in ascending order (A-Z, 0-9) and `ASC` is the default behavior, so you can omit it - including for clarity.

* **salary DESC**:
  * First sort by job_id, then sort any rows that have the same job_id based on the salary column in descending order (secondary sort key).
  * All employees with the same job are grouped together, and within each job group, they are sorted from the highest-paid to the lowest-paid.

***

### Problem 3: ISSUE
* Display employees (last_name, salary, job_id, hire_date) that were hired after December 31, 1999. Order the resulting data set by hire_date in ascending order.
* Deliverables: One query

```SQL
SELECT last_name, salary, job_id, hire_date
FROM employees
WHERE hire_date > '1999-12-31'
ORDER BY hire_date ASC;
```

***

### Problem 4:
* Display employees (last_name, first_name, hire_date, salary) having their salary in the range of 10,000 and 20,000 (border values included). Order the resulting data set by salary descending and last_name ascending.
Deliverables: One query

```SQL
SELECT last_name, first_name, hire_date, salary
FROM employees
WHERE salary BETWEEN 10000 AND 20000
ORDER BY salary DESC, last_name ASC;
```

### Xplanation
* The BETWEEN operator specifies a range of values, including the border values.
* The condition `salary BETWEEN 10000 AND 20000` is equivalent to `salary >= 10000 AND salary <= 20000`. 

The ORDER BY clause sorts the result set in two ways:

* **salary DESC**: 
  * This is the primary sort. The results are first ordered from the highest salary to the lowest.
* **last_name ASC**:
  * This is the secondary sort. For any employees who have the same salary, they will be sorted alphabetically by their last name.

***

### Problem 5:
* Display employees (last_name , first_name, salary) having the lower case letter e in the 3rd position of the last_name and a total length of last_name of 6 characters. 
* Order the resulting dataset by salary in descending order.
* Deliverables: One query

```SQL
SELECT last_name, first_name, salary
FROM employees
WHERE last_name LIKE '__e___'
ORDER BY salary DESC;
```


### Xplanation
* **LIKE**:
  * pattern matching (often used in the WHERE clause to search for a specified pattern in a column).

* **Wildcards**:
  * The LIKE operator uses two special wildcard characters:
    * `_` (Underscore): Matches any single character.
    * `%` (Percent sign): Matches any sequence of zero or more characters.

* **last_name LIKE '__e___'**:
  * The pattern that filters the results.
  * The first `_` matches the first character.
  * The second `_` matches the second character.
  * The `e` matches a literal lowercase 'e' in the third position.
  * The three remaining `_`'s match the fourth, fifth, and sixth characters.

> The last_name has exactly six characters and the third character is an 'e'.

***

### Problem 6:
* Display employees (last_name , first_name, salary, department_id) not working in department 80. Order the resulting dataset by department_id and last_name.
* (Hint: Query the number of employees in department 80, and note that there are a total of 107 employees in the employees table.
  * Your result should be total number minus employees in department 80)
* Deliverables: One query

```SQL
SELECT last_name, first_name, salary, department_id
FROM employees
WHERE department_id <> 80
ORDER BY department_id, last_name;
```

***

### Problem 7:
* Display employee_id, department_id from table job_history and sort it by employee_id, department_id. 
* Then show only the **unique** values of `employee_id` and `department_id` contained in table `job_history` sorted by `employee_id`.
* Deliverables: Two queries

```SQL
SELECT employee_id, department_id
FROM job_history
ORDER BY employee_id, department_id;

SELECT DISTINCT employee_id, department_id
FROM job_history
ORDER BY employee_id;
```
