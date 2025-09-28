## 2.3 Character Data in SQL

### Character data 
* in `SQL version 89` 
  * was represented by a **fixed-length string of characters** (`char(n)` or `character(n)`). 

* `SQL 92` 
  * added the varying character data type, which at that time was already supported by many database vendors. 
  * This was important, particularly at that time, in order to save storage space since a varying character data type will use only as much space as needed up the maximum defined. 
  * For example `varchar(10)` is a **varying character data type** with a **maximum length of 10 printable characters**. 
  * defined the national character data types which are based on the ISO defined Unicode character sets. 
  * allows the database administrator to define **collation sequences**. The collation sequence **defines the order of characters**. There is always a default collating sequence defined for each character set.

In SQL, 
* **character strings** are printable characters enclosed in **single quotation marks**. 
* To use a single quote within a quoted string, you must add two single quotes. 
* **You cannot use double quotes in strings**. 
* **Double quotation** marks are **used for column names** containing spaces or SQL reserved words.
* No two languages agree on how to compare character strings as equal unless they are totally identical. First of all, is an uppercase letter the same as a lower case letter? Some languages even do not have this concept at all. 
* Most programming languages, including SQL, ignore case in the program text but not necessarily in the data. Some database products allow the DBA to set uppercase and lowercase matching as a system parameter. 
* `MS Access` does not differentiate between upper and lower case in data, it is case-insensitive!

**Standard SQL** has two functions to change the case of a string:
* Lower(string expression) and 
* Upper(string expression)

**Equality of strings** of unequal length is processed by first padding the shorter string with blanks on the right side until the strings are of the same length. Then they are matched, position for position, for identical values. If one position fails to match, the equality fails.

In contrast, **XBase language** (such as FoxPro, dBase) truncate the longer string to the length of the shorter string and then match them position for position. Other languages ignore upper and lower case differences.

* **SQL 89** 
  * did not specify a collating sequence at all. Mostly all database products used either `ASCII` or `EBCDIC`, which are both Roman I character sets in ISO terminology. 
  * National language options can be very complicated. For example, the Nordic languages share a common ISO character set, however, they sort the letters in a different way. German is sorted differently in Germany and Austria (ouch!). Standard SQL now allows the DBA to tweak the collating sequence, a very important task in the age of globalization.

* **SQL 92** 
  * defines standard string functions that most database vendors have implemented, either as a SQL function or as a vendor library function. 


| Function  | Description |
|--------------|----------|
| ASCII(char) | Returns the ASCII character code of a character  | 
| Chr(integer)   | Converts a ASCII character code into a character (reverse of ASCII)  | 
| Initcap(char)   | Returns the first character in each word to uppercase and the rest to lowercase.  | 
| Lower(char)   | Returns the entire string in lower case.  |    
| Upper(char)   | Returns the entire string in upper case.  | 

| Function  | Description |
|--------------|----------|  
| Concat(char1, char2)   | Returns a concatenation of char1 and char2. Use double pipe command `||`  | 
| Instr(char_test, char_locate, [start_Pos], [occurrence])   | Returns the position of a string char_locate found in string char_test. You may specify a start position to start searching. You may also specify an occurrence number, for example the 2nd occurrence.   |    
| Length(char)   | Returns the length of a string  | 
| Ltrim(char, [char_trim])
Rtrim(char, [char_trim])
Trim(char,[char_trim])   | Returns a partial string of char starting at position and of length len.  | 
|    |   | 
| Substr(char,pos,[len])   | Removes leading spaces from a string, or a specified string char_trim. Rtrim removes from the right side. Trim removes from both sides.  |

* To add strings together, use the string concatenation operator `||`

### Example 2.3.1: using the ASCII function: 

* The `ASCII` function returns the key code for a given character in the current character set.

```SQL
SELECT ASCII ('A') FROM dual;
```
EXPECTED RESULT
65
A is at position 65 or has an ASCII code of 65.
Z has ASCII code of 90.
From 65 to 90 we find all the upper case letters. 

### Example 2.3.2: using **INITCAP**, **LOWER**, and **UPPER** functions:

```SQL
SELECT INITCAP('this is a test sentence') Init_Cap 
FROM dual;

SELECT LOWER('This is a Test Sentence') Lowert_case 
FROM dual;

SELECT UPPER('This is a Test Sentence') UPPER_case 
FROM dual;
```

### Example 2.3.3: using the CHR function: 

* CHR function is the opposite of the ASCII function. You give the code and it converts it into the corresponding character. 
* '||' combine multipel character to one string


```SQL
SELECT CHR(72) || CHR(101) || CHR(108) || CHR(108) || CHR(111) || 
FROM dual;
```

### ### Example 2.3.4: **INSTR** function. 

* **use case**: 
  * when you have to look for substrings
* returns an integer position at which a substring is found within a string. 

The example shows how to find the position of the first hyphen in a social security number. The additional syntax allows for specifying the starting position from which to start searching and the number of occurrence of the substring found in the string. 
* The parameter 1 after the hyphen signifies to start from the beginning of the string, the second parameter (2) instructs the function to find the second occurrence.

```SQL

```

### Example 2.3.5: using the **LENGTH** function: 

```SQL

```





### Example 2.3.6: using the **TRIM** function: 

```SQL

```

### Example 2.3.7: using the **SUBSTR** function:

```SQL

```

* The substring function extracts a substring from a string or column. 
* The second parameter (3) is the starting position from which to start extracting, the second parameter (2) is the number of characters to extract.





### Example 2.3.8: using the **INSTR** and **SUBSTR** functions: 

```SQL

```