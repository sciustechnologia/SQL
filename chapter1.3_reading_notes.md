## 1.3 ORDER BY Clause

The next clause in the `SELECT` statement is the Order By clause >> allows the user to perform very specific sorting.

One of the core principles of relational databases is that `a relation is unordered`. That means data in a table is not sorted in any way, such as chronological order, primary key order, or unique index order. In fact, when you issue a SQL SELECT statement to retrieve data, the order of data is absolutely random. 
The `SELECT statement allows you to retrieve the data in a specific order`. You can sort by more than one column, and whether you want to sort a specific column ascending or descending. The official SQL standard requires that all sorted columns must be included in the SELECT clause of the SELECT statement. Here we see the first deviations in database vendor products, some database products allow you to sort on columns that are not part of the SELECT clause.

Example 1.3.1:
Issue the following SELECT statement using an ORDER BY clause: 

```sql
SELECt * (column name) FROM table name
	ORDER BY column name
			ASC
			DESC
```

When we talk about sorting data, we have to introduce the `collating sequence of database software`. The collating sequence determines the `order of precedence for every character listed in the current language character set specified by the operating system`. For example, it prescribes whether lower case letters will be sorted before uppercase letters and so on. Also think about the special characters in other languages, such as French, German, and of course Spanish.

We will cover the collating sequence in more detail when we discuss the WHERE clause later in this chapter.

To order data using multiple columns, separate each column by a comma. Specify for each column whether `ascending (ASC)` or `descending (DESC)` is requested. The order of the columns listed in the ORDER BY clause is important as SQL processes sort order `from left to right`.

Example 1.3.2:
Issue the following SQL statement using multiple columns in the ORDER BY clause: 
```sql
SELECt first_name, last_name,, phone_number, manager_id
FROM employees
ORDER BY manager_id DESC, last_name ASC;

# expected result: 107 rows selected.
```


When using the `ORDER BY` clause, you also have to think about null values. 
* How do null values fit into the sort order? 
* Do they come before or after non-null values? 
There is no answer available, so the SQL standard incorporated a special sub clause in the ORDER BY clause to indicate whether Nulls should come first or last (in relation to non-null values). 

* By default, `nulls are ordered after non-null values when the order is ascending and before when the sort order is descending`. 
* Use the `NULLS FIRST`/`NULLS LAST` clause for each column in the Order By clause to explicitly indicate how nulls should be sorted.

Example 1.3.3:
Issue the following SQL statements, one without specifying NULLS first and one with: 

```sql
SELECt * country_id, country_name, region_id
FROM countries
ORDER BY region_id;

# expected result: 25 rows selected.
```

