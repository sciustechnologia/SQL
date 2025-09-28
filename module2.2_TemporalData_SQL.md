## 2.2 Temporal Data in SQL

### The Calendar

* The calendar year has more than 365 days, 365.2522 to be exact. 
* Over time, the calendar did not align anymore with the seasons and the farmers were using the starts to accurately predict the seasons, the flooding of the river Nile for example. Therefore, the **Julian calendar** added the additional **leap day every four years to account for the fraction**. 

However, the 0.0022 fraction still adds up over time, and in 1582 had gotten 10 days out of sync with the seasons. Finally, scientist had convinced Pope Gregory to drop almost two weeks in October of the year of 1582. That was a big deal, even at that time! Some countries did not follow right away, they adopted the change in calendar later on.

The abbreviations A.D. (Anno Domino, latin for “in the year of Our Lord”) and B.C (before Christ) have been replaced by `C.E. (common era)` and `B.C.E. (before common era)` in the ISO standard to avoid religious references.

The year also **varied from country to country**. Great Britain preferred to begin the year on March 25, while other countries began at Easter, December 25, or March 1, and of course January 1.
Until fairly recently, no one agreed on the proper display format for dates. For example, 12/16/95 in Boston is 16/12/95 in London, and 16.12.95 in Berlin and 95-12-16 in Stockholm.

Faced with all the various possibilities, software vendors came up with various general ways of formatting dates for display. The usual ones are some mixtures of two or four-digit year, a three letter or two-digit month and a two digit day within the month.Slashes, dashes or spaces can separate the three parts of a date.

Today’s standard format is the “yyyy-mm-dd” format that is part of the SQL standard.
The timestamp format can be either `local time` or `UTC/GMT time`.
Furthermore, daylight savings time makes matters more complicated, and up to today there is no general agreement how to handle this in the SQL standard. A date without a time zone is ambiguous in an international system, for example.

***

### SQL **Temporal Data Types**: Date, Time. Timestamp

* All SQL databases have a **date data type**, and then most have a separate time and **timestamp data type**. 
* SQL standard also has the **Interval data type**, that is, Day, Hour, Minute and Seconds. 
* Both of these data types are temporal data types, but 
  * `date/time` represents a point in time, whereas 
  * the `Interval` are durations of time.

* **Standard SQL** has a full set of operators for all these data types, the full syntax and functionality have not yet been implemented in any SQL product, particularly since many **database vendors came up with their own extension long before there was a standard**.

The following table lists the most important `date/time` functions. Again, many of these functions are vendor specific, however, similar functions exist in the other database products.

|  Function  | Description  |
|-------|-----|
| Current_Date, Sysdate  | Returns the current date and time. Current_Date works in conjunction with a time zone, whereas sysdate will always return the server date and time value.  | 
|  To_Date(char, format)  |  Takes a character data type and converts it back into a date/time data type using the specified format.  | 
 |  Greatest(date1, date2, ..)  |  Returns the latest date (works across multiple columns) | 
|  Least(date1,date2,…)  |  Returns the earliest date (also across multiple columns)  | 
 |  Max(date)  |  Returns the latest date (in one column only) | 
 | Min(date)   |  Returns the earliest date (in one column only)  | 
 |  Round(date, format)  |  Returns a date rounded to the unit specified by the format. If you omit the format, the date is rounded to the nearest day. | 
 |  Trunc(date)  |  Returns a date at midnight (effectively removing the time component)  | 
 |  Trunc(date, format) |  Allows to selectively remove part of a date  | 




### To_Char(date/time,format)

| Day  | Month | Year   | Hour   | Minute   | Seconds |
|-------|-----|----------|----------|----------|----------|
| D | MM  | YY  | HH | MI   | SS  |
|  DD  | MON  | YYYY  | HH12 |    |  SSSS |
| DDD |   |  RR |  |    | SSSSSS  |
|  DAY  |   | RRRR  |  |    |   |
| DY |   | YEAR  | A.M. or P.M. |    |   |

AM or PM

* Allows to format a date/time value in various ways
* The RR or RRRR format mask is for Y2K compatibility. 
* If a year is given in a two-digit format and if the year is **between 50 and 99**, the year is prepended with 19, otherwise it is prepended with 20.


### TO_CHAR: SUFFIXES and Prefix

* Suffixes for Number Display

|  Suffix  | Description  |
|-------|-----|
|  TH | Ordinal number (DDTH for 4th)   | 
|  SP  |  Spelled out numbers (DDSP for FOUR)  |
|  SPTH or THSP
  |  Spelled-out ordinal numbers (DDTHSP for FOURTH)  |

|  Prefix  | Description  |
|-------|-----|
| FM  |  Returns a value with no leading or trailing blanks.  | 

***

* **Oracle** stores date and time (datetime) data in its own internal format, in `7-byte` fields that correspond to century, year, month, day, hour, minute, and second. 
* The date/time default format is `dd-Mon-YY` or `dd-Mon-YYYY`. 
* Note that there is `no time component`. Therefore, when you do not specify a format, the default format is used.

### TO_CHAR, TO_DATE

* use the **TO_CHAR** function to `format date/time values stored in the database for viewing` (to the date base)
 and 
* the **TO_DATE**  function `to store a string and a corresponding format back into the database as a date/time data type` (to the client).

Image here

### Example 2.2.1: using the TO_CHAR function to format date values:

```SQL
SELECT sysdate FROM dual;

SELECT TO_CHAR(sysdate, 'mm/dd/yyy hh24:mi:ss' Formatted_Date 
FROM dual;

SELECT TO_CHAR(sysdate, 'FmMonth DDTHSP, YYYY' )
FROM dual;
```

* `sysdate` is the time on the databe server, which might be in a different time zone. 
* `CURRENT_DATE` works with time-zone and is the date/time on the client computer. 
* `SYSDATE` is always the database server date/time. Change 4 time zones  west of GMT (east coast)

### Example 2.2.2:  using the Current_Date and Sysdate functions:

```SQL
SELECT TO_CHAR(CURRENT_DATE, 'mm-dd-yyy hh12:Mi:ss' CURRENT_DATE 
FROM dual;

SELECT TO_CHAR(SYSDATE, 'mm-dd-yyy hh12:Mi:ss' CURRENT_DATE 
FROM dual;

ALTER SESSION SET TIME_ZONE = 'America/New York';

SELECT TO_CHAR(CURRENT_DATE, 'mm-dd-yyy hh12:Mi:ss' CURRENT_DATE 
FROM dual;

SELECT TO_CHAR(SYSDATE, 'mm-dd-yyy hh12:Mi:ss' CURRENT_DATE 
FROM dual;
```

***

## GREATEST, LEAST, MIN, MAX

### Example 2.2.3: using the GREATEST and LEAST functions: 

```SQL
SELECT start_date, end_date, GREATEST(start_date. end_date) Greattest, LEAST(start_date. end_date) 
FROM job_history;
```


### Example 2.2.4: using the MIN and MAX aggregate functions:

```SQL
SELECT MIN(hire_date)  First_Hire, MAX(hire_date) Last_hire
FROM employees;
```

## ROUND, TRUNC

### Example 2.2.5: using the ROUND function: 

```SQL
SELECT TO_CHAR(ROUND(TO_DATE('4-jun-06'), 'Year'),'Month-dd/yyy') Last_New_Year
FROM dual;  

SELECT TO_CHAR(ROUND(TO_DATE('4-jul-06'), 'Year'),'Month-dd/yyy') Last_New_Year
FROM dual;  

SELECT TO_CHAR(ROUND(TO_DATE('4-jun-06'), 'Month'),'Month-dd/yyy') FIRST_of_thisMonth
FROM dual;  
```

* rounds the entire year back to -01/2006

### Example 2.2.6: using the TRUNC function: 

```SQL
SELECT TO_CHAR(TRUNC(SYSDATE), 'dd-mm-yyyy hh:mi:ss pm') AS Trund_date FFROM dual;
```

* The `TRUNC` function used on date/time values removes the time portion of a date/time value (if no number of decimal parameter is specified). 
* A date value without a time component is set to midnight.
 
> Note: 
* In the above example, pm was used in the format as an am/pm indicator. However, am was displayed as this is the current part of the day since we are displaying a midnight time.

1. What does the default Date/Time format look like in Oracle?
2. What is the diffeence between Current_date and Sysdate functions?
3. Besides date/tome value, what else do you need to properly display or store the date/time value in the database?


