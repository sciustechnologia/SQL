## 1.2 basic Select Statement

The SELECT statement forms the fundamental building block of the SQL language, better yet, of the DQL part of SQL. 
It allows the user to retrieve data from the database in a variety of ways. 
Furthermore, it also enables the user to analyze the data in a very sophisticated way by using `Group summaries` and `Aggregate functions`.

The required clauses of the SELECT statement are the SELECT and the FROM clause. 
* The `SELECT` clause specifies `which columns and/or expressions (calculations of column values) appear and in which order (from left to right)`. 
* The `FROM` clause tells the SELECT statement `where the data can be found (in tables and/or views)`. 

The syntax of the SELECT statement is shown below:
`SELECT` column name `FROM` table name

Figure 1: Basic `SELECT` statement

* If more than one column is selected, the column names are separated by commas. 
* If the data is coming from more than one table and/or view, the table names are comma separated as shown above.

Example 1.2.1:
* Display the last and first name of employees along with their salary and their hire date:

```sql
SELECT last_name, first_name, salary, hire_date
FROM employees;
```

The SELECT clause can also contain static values or expressions (will be covered later in this course). A `static value` is a fixed value that can be used along with other columns in the SELECT clause

Example 1.2.2:
* Query the Jobs table and show the Job Title along with the Minimum Salary. 
* Use a static string ‘Minimum Salary’ before the Minimum Salary column.

```sql
SELECT job_title, 'Minimum Salary=', min_salary
FROM jobs;
```

> Note: 
 The Set Page[s] option has been set to 50 in order not to repeat the column headers for 50 rows. This number includes the column header and the underline characters (-------), these are two rows.

You can alias column names (as well as table names), that is, use a different name than the actual column name: 
* add after the column expression a column alias or 
* use the AS keyword to explicitly indicate a column alias. The AS keyword is optional, so you can use it or simply leave it out.

Example 1.2.3:
Modify the previous example as follows: 

```sql
SELECT job_title, 'Minimum Salary=' AS StaticString, Min_Salary AS MinSalary
FROM jobs;

# 19 rows expected
```

As you can see from the example above, the column alias is expressed all in upper case. If you want to preserve the case or even include blank spaces in your column alias, then you must include the column alias in double quotation marks as shown in the next example.

Example 1.2.4:
Display the job_title, and a static string together with the min_salary column using column aliases using the optional keyword AS:

```sql
SELECT job_title, 'Minimum Salary=' AS "Static String", Min_Salary AS "Min Salary"
FROM jobs;
```


There is no limit to the number of columns you can specify in the SELECT clause. As a matter of fact, you can easily request all columns from the underlying table without having to type all column names in the SELECT clause. Simply use the `*` (asterisk) command in the SELECT statement to retrieve all columns for a given table.

> SELECT * (column name) FROM table name

* This shortcut can come in handy sometimes, but is also poses a certain risk. 
* The asterisk will always retrieve all columns of the current datasource. 
* If you expect a certain number of columns or a certain column name, than this particular use of the SELECT statement may not be the right choice.

The rule of thumb is to use the asterisk only as a quick and dirty way to see all columns. But do not use it in SQL programming unless when explicitly recommended.

> Note: 
You cannot mix the asterisk character with any other columns or expressions listed in the SELECT clause, this will result in an error message.

Example 1.2.5:
Issue the following SELECT statement using the asterisk:

```sql
SELECT *
FROM countries;

# expected result; 25 rows selected.
```



