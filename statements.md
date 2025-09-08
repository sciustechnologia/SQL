* Every SQL statement begins with a verb.
* Every clause also begins with a keyword, such as `WHERE`, `FROM`, `INTO`, and `HAVING`.
* Each statement requests a specific action from the DBMS, such as creating a new table, retrieving data, or inserting new data into the database.

###  Data Query Language(DQL)

* retrieve data from the database in many different ways, they can also analyze data (count, summarize, find minimum and maximum values). 
* Using this part of the SQL language is fairly harmless, as it does not alter any database objects or its data.

### Data Manipulation (DML)

* alter data in the database. When mistakes are made, the changes can affect an entire table or only part of the data in a table. 
* every fully-relational compliant database has some tools to either recover the original data or safeguards that require specific commands to commit the changes.

| Statement | Description | 
|---|---|
| SELECT | Retrieves data from the database | 
| INSERT | Adds new rows of data to the database | 
| UPDATE | Modifies existing database data | 
| MERGE | Conditionally inserts/updates/deletes new and existing rows | 
| DELETE | Removes rows of data from the database | 

### Data Definition (DDL)

* creates the data containers, or the structures that hold the data. 

| Statement | Description | 
|---|---|
| `CREATE` TABLE | Adds a new table to the database | 
| `DROP` TABLE | Removes a table from the database | 
| `ALTER` TABLE | Changes the structure of an existing table | 
| CREATE VIEW | Adds a new view to the database | 
| DROP VIEW | Removes a view from the database | 
| CREATE INDEX | Builds an index for a column | 
| DROP INDEX | Removes the index for a column | 
| CREATE SCHEMA | Adds a new schema to the database | 
| DROP SCHEMA | Removes a schema from the database | 
| CREATE DOMAIN | Adds a new data value domain | 
| ALTER DOMAIN | Changes a domain definition | 
| DROP DOMAIN | Removes a domain from the database | 

### Data Control Language (DCL) - Access Control 

* manages access to the database objects as well as the data themselves.
* granting access to an entire table, or only access to certain columns, or only access to certain rows in the table.

| Statement | Description | 
|---|---|
| GRANT | Grants user access privileges | 
| REVOKE | Removes user access privileges | 
| CREATE ROLE | Adds a new role to the database | 
| GRANT ROLE | Grants role containing user access privileges | 
| DROP ROLE | Removes a role from the database | 

### Transaction Control

| Statement | Description | 
|---|---|
| COMMIT | Ends the current transaction | 
| ROLLBACK | Aborts the current transaction | 
| SET TRANSACTION | Defines data access characteristics of the current transaction | 
| START TRANSACTION | Explicitly starts a new transaction | 
| SAVEPOINT | Establishes a recovery point for a transaction | 


### Programmatic SQL

| Statement | Description | 
|---|---|
| DECLARE | Defines a cursor for a query | 
| EXPLAIN | Describes the data access plan for a query | 
| OPEN | Opens a cursor to retrieve query results | 
| FETCH | Retrieves a row of query results | 
| CLOSE | Closes a cursor | 
| PREPARE | Prepares a SQL statement for dynamic execution | 
| EXECUTE | Executes a SQL statement dynamically | 
| DESCRIBE | Describes a prepared query | 



