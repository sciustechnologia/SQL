module2.1_Numeric data in sql.md

## 2.1 Numeric data in sql

SQL is 
* **not** a computational or a procedural language, 
* the `arithmetic capability is weaker` than in many other programming languages. 
* Many specific functions relating to arithmetic are defined differently across the database products.  Therefore it is important to study each implementation of the arithmetic functions of your database product.

The **SQL standard** possesses a wide range of numeric types. 
Furthermore, some database vendors add their own numeric extensions, such as the type Currency in MS Access or Money in SQL Server.

### Data Types

### Exact and Approximate Numeric Data Types
* Numbers are either classified as `exact` or `approximate`. 

* **exact number** has a `precision `(p) and a `scale` (s) (OR `accuracy`). 
  * The **precision p** is a positive integer that represents the `number of significant digits in a particular radix`.
  * The **scales** is a nonnegative integer that indicates `how many decimal places the number has`.
### exact numeric types
> The data types `Numeric`, `Decimal`, `Integer`, `BigInt` and `SmallInt` are exact numeric types.
**Decimal (p,s)**
* use decimal precision for rounding, based on the total number of digits defined by the scale value. The length is equal to the defined presion p plus 1 (for the decimal point) if scale is greater then . The decimal portion is exactly the size denined but the scale.
Numeric (p,s)
Integer (p)
* whole numbers only, scale of zero. Minimum and Maximum precision based on manufacturer.
BigIntWhole numbers 
* whole only, scale of zero. Minimum precision greater than integer (for 64-bit systems)
SmallInt 
* whole numbers only, scale of zero. Minimum and Maximum precision based on manufacturer.

* **approximate** numeric value consists of a `mantissa` and an `exponent`. 
* **exponent** is a signed integer specifying the `magnate of the mantissa`. 
* An approximate numeric value has a precision. 
* The precision is a positive integer specifying the number of significant digits in the mantissa. 
* The value of an approximate numeric value is the mantissa multiplied by 10 to the exponent. 
* `Float (p)`, `Real`, and `Double Precision` are the **approximate numeric types**. 




There is a difference between Float (p) and the Real type. 
* The **Float (p)** type has a `precision equal to or greater than the value p`, whereas 
* **Real** has a `database vendor specific precision`.

List of all the numeric types and their definitions:

### Exact numeric types:

Decimal (p,s)
Uses decimal precision for rounding, based on the total number of digits defined by the scale (s) value. The length is equal to the defined precision p plus 1 (for the decimal point) if scale is greater than 0. The decimal portion is exactly the size defined by the scale (s).
Numeric(p,s)
Very similar to decimal. The only difference is that the decimal portion is at least the size of the scale (s) indicated, but expandable up to a limit set by the database vendor.
Integer(p)
Whole numbers only, scale (s) of zero. Minimum and maximum precision based on manufacturer
BigInt
Whole numbers only, scale (s) of zero. Minimum precision greater than Integer (for 64-bit systems)
SmallInt
Whole numbers only, scale (s) of zero. Minimum and maximum precision based on manufacturer


### Approximate numeric types:
Float (p)
Precision value represents minimum size used, up to the manufacturer’s maximum. Value may be represented in an exponential format, for example 10.5 E-13. Rounding and truncating is defined by the manufacturer.
Real
Has a default precision that must be less than that set for Double Precision.
Double Precision
Has a default precision that must be greater than that set for Real.

### Numeric Type Conversion

Rounding is a process that is almost always necessary. It either happens automatically when different numeric data types are assigned to each other or when a numeric value is stored into a column of a table. The following functions are Oracle functions and not part of the Standard SQL.

**Round function**: `round(n,d)`
The round function rounds a number n to the specified decimal d. The decimal d can be positive, negative or zero. If the decimal is positive, then the number is rounded to that many decimal points. The number five rounds up. If d is zero, then the number is rounded to no decimal points. If d is negative, then the number will have no decimal points and it will be rounded to the d digits to the left of the decimal point.
Example 2.1.1:
Issue the following SQL statement using the ROUND function: 

**Truncation function** `trunc(n,d)`
The trunc  or truncate function simply drops the digits without rounding. The decimal d can again be positive, negative or zero. If the number truncated is five or higher, it is still dropped without rounding the next digit up.

Example 2.1.2:
Issue the following SQL statement using the TRUNC function: 

### Vendor-Specific Numeric Functions
Below a list of selected numeric functions in Oracle:
Function Description
AVG(column_name)
Returns the average of a column of numbers
Count(column_name)
Returns the number of rows returned by a query
GREATEST(value1, value2, …)
Returns the largest of multiple values
LEAST(value1, value2, …)
Returns the smallest of multiple values
MAX(column_name)
Returns the maximum value of a column of numbers
MEDIAN(column_name)
Returns the median (middle value) of a column of numbers


Function
Description
MIN(column_name)
Returns the minimum value of a column of numbers
NVL(value_eval, value_returned)
Returns a value if the value_eval is null
ROUND(value, integer)
Returns a value rounded to number of integer of places
STDDEV(column_name)
Returns the standard deviation of numbers in a column
SUM(column_name)
Returns the sum of numbers in a column
TRUNC(value, decimal_places)
Returns a number truncated to the specified number of decimal places
VARIANCE(column_name)
Returns the variance of numbers in a column


Many of these functions are vendor functions, that is, not part of the standard SQL functions. 
However, many database vendors use the same or similar functions. 
But always check the documentation for the database product to inform yourself about the usage of a particular function.

### Example 2.1.3 `AVG` function: 

The above example calculates the average of the `min_salary` column in the `jobs` table.

> WARNING: 
* The **aggregate functions** – `COUNT`, `SUM`, `AVG`, `MAX`, and `MIN` – do not handle `NULL` in the same way as ordinary functions and operators. 
* Instead of returning `NULL` as soon as a `NULL operand` is encountered, they only take non-NULL fields into consideration while computing the outcome.


### Example 2.1.4:
Issue the following SQL statement using the COUNT function: 

`Count(*)` counts all records of the table listed in the `FROM` clause in the `SELECT` statement. The count function only counts non-null fields when used on a column, even when a record exists. Hence, **if you use a column to count on, and some records contain nulls in this column, the record is not counted**. See the next two examples.

### Example 2.1.5:
Issue the following SQL statement using the COUNT function: 

* The first example shows that there 106 employees (out of a total of 107) that have a manager. 
* The second example shows that there are 35 employees that earn a commission on top of their regular salary.

### Example 2.1.6:
Issue the following SQL statement using the **GREATEST** function: 

As you can see, the `GREATEST` function selects the highest value per row based on the columns provided as parameters for this function.

### Example 2.1.7:
Issue the following SQL statement using the **LEAST** function: 


### Example 2.1.8:
Issue the following SQL statement using the MAX, MEDIAN, and MIN aggregate functions: 

* Looking at the min_salary column values in ascending order on the right side is probably helpful in understanding these aggregate functions. 
* The **median** is the number “in the middle”, where `50% of the data is less than the medium and the other 50% is greater than the median`.

> Note: 
The functions `Greatest` and `Least` work **horizontally across multiple columns (on a per row basis) whereas 
* `Min and Max` can only be applied **against one column, but for many rows**.

Having all these functions at your disposal allows you to construct complex business logic in a SELECT statement, rather than having to write procedural code in a function or stored procedure. 

You can nest functions, that is, call a function from within a function as its argument. In the next example, we will demonstrate exactly that.

 > WARNING: 
 * The Greatest/Least functions will return NULL if one of the values provided is NULL. The Min/Max functions do not consider NULL values.
 
* The **sales_by_quarter** table lists sales by quarter (horizontally) and by year (vertically) in form of a matrix. 
* This particular table has only two rows, imagine you have hundreds or even thousands of rows. Now you want to know the highest sales ever.

### Example 2.1.9:
Issue the following SQL statement using GREATEST nested inside a MAX function: 

* The **Greatest** function is nested inside the **Max** function. 
* The Greatest function takes all quarter columns as an argument and determines the best sales in a quarter per year. 
* Then the Max function takes the highest value in that one column for all years.

### Example 2.1.10:
Issue the following SQL statement using the NVL function: 


 WARNING: 
 * The **to_char** function is necessary here to **convert the manager_id column into a character column** since the substitute for a null value is ‘No Manager’ which is a character data type. The function NVL provides two values for one column, and it must be of the same data type. 

### Example 2.1.11:
Without the to_char function the following error would be generated:



Using the **NVL2** function you cannot not only replace the null value, but also the non-null value with a different value.

### Example 2.1.12:
Issue the following SQL statement using the NVL2 function:


### Example 2.1.13:
Issue the following SQL statement using the STDEV and the VARIANCE function: 


