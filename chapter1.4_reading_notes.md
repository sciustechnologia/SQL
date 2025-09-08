## 1.4 `WHERE` Clause `filtering data`. 

* `Selecting data` basically means you are limiting the data horizontally (the `number of columns`). 
* `Filtering data` means you are limiting the data vertically, that is the `number of rows`.

To `limit the number of rows` based on some kind of search condition may include:
* View sales in a particular region
* Looking for customer names that start with a particular string combination* List employees who left the company within the last year

### Example 1.4.1:
Issue the following SQL statement using a WHERE clause: 

Note the usage of the single quotes in the above example in the WHERE clause. You use single quotes as delimiters for enclosing string data, and double quotes as delimiters for database object names (identifiers). In most cases, you do not have to use double quotes for identifiers, try to avoid them for simplicity reasons.
 WARNING: When using blank spaces or special characters other than alphanumeric and the underscore character, double quotes are required for delimiting the object name, such as a table or column name for example. Avoid this at all cost!

 Note: A good way to remember the difference between single and double quotes is the following: [S]ingle quotes are for [s]tring data. [D]ouble quotes are for [d]atabase object names.



The SQL standard defines the following five basic predicates in a WHERE clause:
Predicate
Description

Comparison:
Use one of the six comparison operators to compare one value expression (column) against another value expression. The six comparison operators are:
    • =	equals
    • <>, !=	not equal
    • <	less than
    • >	greater than
    • <=	less than or equal to
    • >= 	greater than or equal to
Range:
The Between predicate tests whether the value of a given value expression falls within a specified range of values. Specify the Between keyword followed by the beginning value of the range, then the And keyword followed by the ending value of the range.
    • BETWEEN beginning_value AND ending_value
Membership:
Use the IN predicate to test a value expression against a list of values. List the values in the IN predicate separated by commas and enclose the entire list in parentheses.
    • IN(comma-separated list of values)
Pattern Match:
The LIKE predicate allows you to test whether a character string value expression matches a specified character string pattern.
    • %	Zero, one or many arbitrary characters
    • _	One and only one arbitrary character
Null:
Use the IS NULL predicate to determine whether a value expression evaluates to Null. Use NOT IS NULL to exclude nulls.
    • IS NULL
    • IS NOT NULL




### Example 1.4.2:
Issue the following SQL statement using a WHERE and an ORDER BY clause. 

Note that in the previous example the comparison value was not enclosed in any delimiter. The following rules regarding delimiters in WHERE clauses apply:
    • Comparison values used against character data type column must be enclosed in single quotes.
    • Comparison values used against a number data type column does not need a delimiter.
    • Comparison values used against a date/time data type column must be enclosed in single quotes.
The date/time field is unfortunately handled differently by the various database vendors, a main reason is how the date/time data is stored in the database. In Oracle, the default date format is:
‘d-Mon-yy’ or ‘d-Mon-yyyy’. 
 WARNING: To avoid any further Y2K issues, I recommend using always the 4-digit format notation.


Example 1.4.3:
Issue the following SQL statement using a WHERE clause having a Date data type: 

As you can see, it does not matter whether the two or four digit year is used. Also lower or uppercase spelling of the month has the same effect. Lastly, you may use one or two digit format for days less than 10.
 Note: You may have noticed that Oracle displays a feedback statement after a SELECT statement, such as 25 rows selected. In the above example, it did not show this statement. When more than 5 rows are selected, Oracle issue the feedback statement, otherwise it leaves it out. Also, if no rows are returned as a result of a SQL statement, Oracle issues ‘no rows selected’ feedback statement.
Comparing value expressions:
It is easily understood when you compare numeric or even date/time values, but you must pay close attention when you compare character strings.  For example, are ‘Michael’ and ‘MICHAEL’ equal or are they different? And which one is smaller than the other? This really depends on the collating sequence of the database product, that is, how individual characters are sorted within a character set.
Example 1.4.4:
Issue the following SQL statements comparing characters: 


To figure out the collating sequence of the Oracle product, compare individual characters in the WHERE clause. If the condition in the WHERE clause is true then all rows are returned, if it is false, no rows are returned. This is a simple test as shown in the next example.








Example 1.4.4 (continued):
Issue the following SQL statements to determine collating sequence of characters: 


The above example shows that the first WHERE clause results in a Boolean True, otherwise we would not have received any rows back from the database. That, in turn, means that the character 1 comes before the uppercase character A in the character set. When you reverse the relational operator, then no rows are returned. In this case, the condition in the WHERE clause yields a Boolean false.
In the next examples we will use the inequality operator.








	

Example 1.4.5:
Issue the following SQL statement using the inequality operator in the WHERE clause:
 

 Note: Instead of the operator <> you could also use the other inequality operator != in the above example.


Example 1.4.6:
Issue the following SQL statement using a Date column and the inequality operator: 
 

Example 1.4.7:
Issue the following SQL statement using the greater than operator: 


Example 1.4.8:
Issue the following SQL statement using a Date criteria and the greater than operator: 



 WARNING: In the above example, the date literal is used without a time component, that means January 1, 2000 midnight(00:00:00). If the hire_date column contains date and time values, then a date/time value of January 1, 2000 8:53:23AM in the hire_date column would result in a true condition and therefore the row would be retrieved. The date/time data type will be covered in the next chapter.





Range Value Comparison
Example 1.4.9:
Issue the following SQL statement using the Between And operator: 

When searching for ranges of data, it is always better to use the Between predicate, the statement is shorter and it involves less processing time. The start and end values are inclusive.
 WARNING: You must use the lower value of the range as the first parameter in the Between And operator, otherwise the condition evaluates to a Boolean False and no rows are returned.

Example 1.4.10:
Issue the following SQL statement where the higher value is used first: 

Example 1.4.11:
Issue the following SQL statement using dates in BETWEEN operator: 

Membership Value Comparison
Use the IN predicate to compare a column value against a list of distinct values.
Example 1.4.12:
Issue the following SQL statement using the IN predicate: 


Example 1.4.13:
Issue the following SQL statement using the IN predicate with number values:

Pattern Match Value Comparison
The pattern match comparison is useful when you need to find values that are similar to a given pattern string or when you have only a partial piece of information. Use the LIKE relational operator in pattern match comparison.
The following two wildcard characters are defined in the SQL standard:
%	Represents zero, one or more arbitrary characters
_	Represents exactly one arbitrary character
Example 1.4.15:
Issue the following SQL statement using the LIKE predicate:


Example 1.4.16:
Issue the following SQL statement using the LIKE predicate and the single character wildcard: 

Escaping Special Characters
Sometimes, you have to write SQL statements and query for data that contains SQL specific characters, meaning these characters have special meaning in SQL. These characters are the single quote (‘), the percent sign (%) and the underscore (_).
To express an apostrophe within a string, escape the apostrophe with another apostrophe or single quote as shown below:
Example 1.4.16:
Issue the following SQL statement using an apostrophe within a string: 

Another common scenario is searching for data that contains wildcard characters. For example, to perform a wildcard search that also contains the percent sign (%) and to query for such characters, you need to escape those characters in your expression using another special character. To escape means that SQL should treat this character as data and not as a wildcard operator.
In the next example, find all employees whose job_id contains 7 characters after the underscore character. First we need to start with the percent sign (%, zero, one or more characters), then with an underscore as data (so we need to escape it), and then seven wildcard character underscores. 

To escape a character, you can pretty much choose any character you want. You must define the escape character in the SQL statement at the end using the ESCAPE keyword.
Example 1.4.17:
Issue the following SQL statement using escape character in wildcard expression: 

Null (Value) Comparison
Up to now we have searched for exact values or for pattern of characters. Now we are looking for unknown values. The Null (value) represent an unknown value meaning there will be a value in the future, but it is currently unknown. It is not zero, because zero is a definite value and means empty. A null means that there will be a value unequal to zero later, once it is known.
I use parentheses around the value word because Null is really not a value, it is a concept. It stands for anything possible but a zero value (in a numeric context). Therefore, Null = Null is False, and any expression compared to Null will yield false, for example hire_date = Null. 
To test for Null values, we must use the Is Null predicate in order for SQL to look for unknown values.

Example 1.4.18:
Issue the following SQL statement using the IS NULL predicate: 

To find rows of data where an attribute is not null, type Is Not Null. 
Example 1.4.19:
Issue the following SQL statement using the IS NOT NULL predicate: 

