1.5 The Concept of Null
The concept of nulls has been discussed as long as SQL is around. It is a controversial issue, however, we must use a concept in the real world to account for missing values.
So what exactly is a null. A null stands for a currently unknown value. When a column value is null, we know that there must be value at some point in the future, but currently we do not know the value. Maybe we have an estimate or an approximation of the value, but that is not good enough for the database. Some applications used the concepts of a dummy value to indicate that the real value will follow later. 
Dr. E.F. Codd proposed to use the Null for two situations: A currently unknown value and a not applicable value. He used the famous example of the eye color of a person wearing sun glasses and the eye color of an automobile.
The SQL standard really supports only the currently unknown value. For a not applicable value something should be entered into this field to indicate that rather than using Null.
Here is my famous coffee example: When I buy a coffee, it usually contains a fixed amount of liquid, or at least let us assume that, say 50 ml. I love coffee, and once I receive the cup of coffee, I take right away a sip to taste the coffee. So how much is in the cup now? I know there is more than 0 and less than 50 ml, but I just cannot tell exactly how much. This is considered a null.
A null cannot be compared to another null, this is where you get a three-valued logic instead of a two-valued one. Let us take a look at the next example to demonstrate this:
Example 1.5.1:
Issue the following SQL statement:

Example 1.5.2:
Issue the following SQL statement to find all employees not having manager_id of 123: 
 

By adding the row count of those queries (8 and 98 = 106) we should have the total count of all records in the employees table. Wrong!! Because if the manager_id column contains a null value, we miss this row. Manager_ID != 123 does not work if the manager_ID is null, the comparison yields false and therefore the row is not retrived. We have to specifically ask for null values.

Example 1.5.3:
Issue the following SQL statement to find the employee record having no manager assigned: 

Therefore, to find all records that are unequal to manager_id 123, use the following Where clause:
WHERE manager_id != 123 OR manager_id IS NULL
 

DISTINCT Predicate
In many cases you want to find out how many different values are used in an attribute of a specific table.  For example, the job history table contains a department_id attribute. You want to know how many unique different department_id values are currently stored in this table.
First let us see how many records we have in the job history table:
Example 1.5.4:
Issue the following SQL statement to query the job history table: 

As you can see from the data output, there are duplicates in terms of department_id values. Now let us find out in how many different departments exist in this table. You would use the DISTINCT predicate in the SELECT clause to find only unique values.
Example 1.5.4 (continued):
Issue the following SQL statement to find all unique departments in table job_history:

Note that the distinct keyword applies to all columns/expressions in the SELECT statement.
Example 1.5.5:
Issue the following SQL statement using the DISTINCT predicate having multiple columns: 


The job_history table contains 10 records, in the previous example we retrieved only 9 rows using the DISTINCT predicate on the columns job_id and department_id. That means that the combination of those two columns contain one duplicate record. Take a look at the example on the previous page where we queried the job_history table, you notice that there are two records with a job_id of ST_CLERK and department_id 50.

Another possible issue is sorting on columns that are not part of the SELECT clause when the DISTINCT clause is used. You cannot sort on a column not part of the SELECT statement when the DISTINCT keyword is used. This is due to the fact that the output is reduced by suppressing duplicates of the distinct columns. But other columns may not have duplicate values, therefore you cannot sort on other columns than those specified in the SELECT statement.
Example 1.5.6:
Issue the following SQL statement demonstrating disallowed sort order on columns not part of the SELECT clause: 



 WARNING: According to the SQL Standard, the ORDER BY clause should only include columns that are listed in the SELECT clause. Oracle, however, in general does allow to sort on columns that are not explicitly listed in the SELECT clause.
