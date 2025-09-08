## 1.1 Overview of SQL

### SQL (=Structured Query Language) 
* has become a norm as a data retrieval and manipulation language. This chapter presents the `history of SQL` as well as a basic overview.
* is a software tool for `organizing, managing, protecting, and retrieving data stored in a database system`.
* has found wide acceptance among many Database Management Systems (DBMS) due to the fact of its early development and standardization that make up today’s SQL language. 
*  is highly portable across the different database platforms.
* is also a `non-procedural language`, also called `declarative language`. You specify only the “What” (`what do you want to retrieve`, for example) and not the “How”.  The SQL database engine will take care of the “How” (how to get the data in the most efficient and fasted way) internally, this process is hidden from the user and does not concern the user at all.
In contrast, a procedural language, also called imperative language, is a language where the programmer specifies an explicit sequence of steps to follow to produce a result.

> Note: 
* A database management system (DBMS) also contains a procedural environment to supplement the non-procedural SQL language. The most common object in this environment is the Stored Procedure. This course covers only the non-procedural SQL language.

* is a command-based language, and SQL statements are comprised of many different clauses. Every SQL statement begins with a verb, such as SELECT. The clauses are made up of keywords and parameters, they also begin with a keyword such WHERE, FROM, INTO, etc. A clause may specify the data to be acted on by the statement or provide more detail about what the statement is supposed to do. Some clauses are required, whereas others are optional.
A SQL statement can span multiple lines, in fact it does not matter how many lines it contains or how the statement is broken down as long as it ends with a semicolon. The semicolon tells SQL where the statement ends, it is not line-based like some other programming languages (that means one line is one executable statement).
The order of the different clauses or parts of a SQL statement is prescribed and important, besides that SQL does not mind spaces, line breaks, or indentation. It is a freeform language.

The SQL language can be structured in the following way:
* Data Query Language(DQL)
* Data Manipulation Language (DML)
* Data Definition Language (DDL)
* Data Control Language (DCL)

Data Query Language (DQL)
This is the most commonly used part of the SQL language and the most developed one. DQL statements retrieve data from the database in many different ways, they can also analyze data (count, summarize, find minimum and maximum values). Using this part of the SQL language is fairly harmless, as it does not alter any database objects or its data.

Data Manipulation Language (DML)
Using this part of SQL is definitely riskier, as DML statements alter data in the database. When mistakes are made, the changes can affect an entire table or only part of the data in a table. Fortunately, every fully-relational compliant database has some tools to either recover the original data or safeguards that require specific commands to commit the changes (that means asking the user do you really want to perform this transaction?)

Data Definition Language (DDL)
This part of SQL is not so “famous” as it really does not deal with data at all. It creates the data containers, or the structures that hold the data. Without it, no database would even exist. The DDL language allows to Create, Drop, and Alter database objects.

Data Control Language (DCL)
This part of SQL manages access to the database objects as well as the data themselves. This is a very important part of every database to secure its structures and data from unauthorized access. Data access can be achieved by granting access to an entire table, or only access to certain columns (for example no access to the Salary column), or only access to certain rows in the table.


### SQL Developments
The relational database model was introduced in `1970 by Dr. E.F. Codd` (also called the God of databases). Shortly after this great moment (now we know) research laboratories and universities began to develop a common language to interact with this new kind of database model. Many different initial efforts lead to a variety of various languages. So how did the SQL language evolve?

It really started out here in `Silicon Valley, at the IBM research center in Almaden`. A major project was underway named `System/R`.  This project was to prove the viability of the relational database model. This project culminated in one of the first relational database prototype systems in the middle of the 1970’s.  Along with this prototype a new language was developed as well, the so-called `Structured English Query Language (SEQUEL)`.

The initial feedback was so overwhelmingly positive that the IBM team furthered their research into this new language. The next version came out in 1976 named SEQUEL/2.  For legal reason the name was changed to SQL (apparently the acronym SEQUEL was already taken). Although many people still pronounce it as “SEQUEL”, the official pronunciation is “S-Q-L”. In 1979 IBM closed this project and proved its viability with commercial potential.

It became clear to many other vendors that IBM was right on target to roll out a commercial relational database system. It was just a matter of time. A few other vendors started now work on their own to develop database software. One of them was Relational Software Inc., founded in 1977 in Menlo Park by a group of engineers. They actually shipped their first version of a database product in 1979, beating IBM by two years. Their product was called Oracle.

UC Berkeley was also researching a new database product at that time. Like IBM, they also created first a prototype and christened their product INGRES.  The language that came with this product was called Query Language (QUEL).  But over time, INGRES converted to SQL as it became clear that SQL was an evolving standard.

IBM finally brought their product to market in 1981 and called it SQL/Data system (SQL/DS). The second version of this product was called DB2, which is still around today.
Sybase was yet another database vendor that developed quite successfully a solid database system called Sybase running under the UNIX operating system. Sybase entered into an agreement with Microsoft to develop the next version of Sybase (to be called System 10) with a version for Windows. That relationship went down the drain over the years. Microsoft finished the Windows version and called the product SQL Server. Sybase called its product Sybase System 10.

Both products were so similar that instructors for Microsoft used the Sybase manuals for teaching purposes as they were much better than the Microsoft manuals.

Current mainstream database systems include:
    • Microsoft SQL Server, Microsoft Visual FoxPro, Microsoft Access
    • Sybase
    • MySQL (Oracle)
    • Oracle
    • IBM DB/2
    • Postgre SQL
    • Informix (IBM)
    • Terradata
    • SQLLite (part of C Library)

> Note:  
Recently new types of databases evolved such as NoSQL. A NoSQL database provides a mechanism for storage and retrieval of data that uses looser consistency models than traditional relational databases. Motivations for this approach include simplicity of design, horizontal scaling and finer control over availability. NoSQL databases are often highly optimized key–value stores intended for simple retrieval and appending operations, with the goal being significant performance benefits in terms of latency and throughput. NoSQL databases are finding significant and growing industry use in big data and real-time web applications. NoSQL systems are also referred to as "Not only SQL" to emphasize that they do in fact allow SQL-like query languages to be used.

### SQL Standards
In 1982, the American National Standards Institute (ANSI) created a technical database committee named X3H2. This committee was comprised of database industry experts and from representatives from every major SQL-based database vendor. 

The committee first proposed standard was primarily based on IBM’s DB2 SQL dialect. In 1986, the first official SQL standard was ratified by ANSI named ANSI X3.135-1986. At this point, this standard represented the least common denominator of the many requirements that most database vendors could conform.

This standard was adopted in 1987 by the International Organization of Standardization (ISO) and was published as ISO 9075-1987. Both of these standards are referred to as simply SQL/86. Finally, all database vendors had a common foundation to work from and to expand the SQL language from here on. The SQL/86 was quickly criticized for various problems such as lack of support for certain relational operators, lack of referential integrity, and redundancy with the SQL syntax. 

In 1989, a new version of the standard was published that addressed some of the problems of the old standard.  This standard was officially named ISO 9075:1989 and X3.135-1989. Again, these standards were referred to as `SQL 89`.

These two standards were far from complete, but they formed an important foundation for the SQL language. For example, these standards still lack many DDL statements to create/modify or maintain database objects such as tables, index, and views.

By the time SQL/89 standard was adopted, both standard organizations were already working on the next version of SQL. Therefore, it did not surprise anybody that a new version of the SQL standard was adopted in 1992 by both organizations. They were named X3.135-1992 and ISO/IEC 9075:1992. This standard was the first fairly complete standard and was much broader in scope than the previous standards. It marked a major milestone in the developing of a comprehensive SQL standard.

Surprisingly, no database vendor currently fully supports and implements this standard. There are some very complex new features contained in SQL/92 that takes time to integrate into the currently already very complex database products. Secondly, the question arises whether it is necessary and economically viable to implement the complete standard. The SQL/92 standard is also referred to as SQL2.

Fortunately, the complex SQL/92 standard has been broken down into three parts, the so-called SQL/92 levels to facilitate implementation of this standard into the database products:

* Entry SQL:
This is the basic level that every major database product now supports. This level is easy to implements and should be followed by every database software.

* Intermediate SQL:
This level encompasses the majority of the features of the SQL/92 standard. Up to today, most major database vendors are still trying to implement and integrate this level into their database products.

* Full SQL
Obviously, this is the complete SQL/92 standard.

Besides the SQL/92 standard, many database vendors implement their own flavor of SQL and add their own extension to SQL to overcome some major shortcomings of SQL. Many database products have their own datatypes besides the six required by the SQL standard. Adding their own extensions to SQL naturally makes the SQL language not portable anymore, one of the main goals of the SQL standard.

The last major revision of SQL is the `SQL 99 standard`, also referred to as `SQL 3`. This revision added regular expression matching, recursive queries, triggers, support for procedural and control-of-flow statements, non-scalar types, and some object oriented features.

Year || Name || Alias || Comments
1986
SQL-86
SQL-87
First formalized by ANSI.
1989
SQL-89
FIPS 127-1
Minor revision, adopted as FIPS 127-1.
1992
 SQL-92
SQL2, 
FIPS 127-2
Major revision (ISO 9075), Entry Level SQL-92 adopted as FIPS 127-2.
1999
SQL1999
SQL3
Added regular expression matching, recursive queries, triggers, support for procedural and control-of-flow statements, non-scalar types, and some object-oriented features.
2003
SQL:2003
SQL 2003
Introduced XML-related features, window functions, standardized sequences, and columns with auto-generated values (including identity-columns).
2006
SQL:2006
SQL 2006
Defines ways of importing and storing XML data in an SQL database, manipulating it within the database and publishing both XML and conventional SQL-data in XML form. In addition, it enables applications to integrate into their SQL code the use of XQuery, the XML Query Language published by the World Wide Web Consortium (W3C), to concurrently access ordinary SQL-data and XML documents
2008
SQL:2008
SQL 2008 
Legalizes ORDER BY outside cursor definitions. Adds INSTEAD OF triggers. Adds the TRUNCATE statement
2011
SQL:2011
SQL 2011
Contains only optional, new features. Language enhancements for temporal support

> His notes are missing something.
* The current SQL standard is `SQL:2023`, officially known as ISO/IEC 9075:2023.

