lessenLearned.md

### INNER JOIN

* returns only rows with a match in both tables. 

```syntax
SELECT column_name(s)
FROM table1, primary, child, Foreign Key
INNER JOIN table2, parent, Primary key
ON table1.column_name = table2.column_name;
```

* retrieve specific order and customer information by combining data from two separate tables.

```sql
        SELECT 
        	Orders.OrderID, 
 	Customers.CustomerName, 
 	Orders.OrderDate
-- to appear in the result set (projection clause)
        FROM 
	Orders
-- the primary table, child, Foreign Key
        INNER JOIN 
	Customers 
-- parent table, Primary key
        ON 
	Orders.CustomerID=Customers.CustomerID; 
	child.CustomerID=parent.CustomerID
-- join condition: dictates how the rows from the two tables are matched and combined.
-- column (CustomerID) is the key that links the two tables together.
```

### Primary Table, Parent, and Primary Keys

| Term | Role in the Query |  Role in Database Design | Key Relationship |
|---|---|---|---|
| Primary Table | The table listed immediately after the FROM clause (FROM Orders). | Often considered the ""child"" or ""many"" side of a relationship (e.g., many orders belong to one customer). | Contains the Foreign Key (FK). |
| Parent Table | The table you JOIN to (INNER JOIN Customers). | The definitive source for the related data, considered the ""parent"" or ""one"" side of a relationship. | Contains the Primary Key (PK). |

### JOIN Three Tables
```sql
SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
FROM ((Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID); 
```

what I understand is

1. SELECT gives me what appears in the result set

2. FROM the child (Orders)

3. first JOIN: parent (Customers) has the condition to compare CustomerID from Orders with CustomersID from Customers table
  * Result: A temporary, combined table containing all columns from Orders and Customers where the CustomerID matches.

4. Second JOIN: parent Shippers has the condition to JOIN/compare ShipperID from Orders table with the ShipperID from Shippers table. 
* Result:



