# 1. Introduction to SQL

`SQL` **is a standard language for accessing and manipulating databases**.

What is SQL?

- `SQL stands for Structured Query Language`
- `SQL lets you access and manipulate databases`
- SQL became a standard of the American National Standards Institute (ANSI) in 1986, and of the International Organization for Standardization (ISO) in 1987

What can SQL do?

- SQL can execute queries against a database
- SQL can retrieve data from a database
- SQL can insert records in a database
- SQL can update records in a database
- SQL can delete records from a database
- SQL can create new databases
- SQL can create new tables in a database
- SQL can create stored procedures in a database
- SQL can create views in a database
- SQL can set permissions on tables, procedures, and views

`SQL` is a `Standard` - BUT although SQL is an ANSI/ISO standard, there are different versions of the SQL language.

However, to be compliant with the ANSI standard, they all support at least the major commands (such as `SELECT`, `UPDATE`, `DELETE`, `INSERT`, `WHERE`) in a similar manner.

`RDBMS` is a `Relational Database Management System`.

The data in a `RDBMS` is stored in database objects called `TABLES`.

A `TABLE` is a collection of related data entries and it consists of columns and rows.

Every `TABLE` is broken up into smaller entities called `FIELDS`.

A `FIELD` is a `COLUMN` in a `TABLE` that is designed to maintain specific information about every `RECORD` in the table.

A `RECORD`, also called a `ROW`, is each individual `ENTRY` that exists in a table.

A `RECORD` is a horizontal `ENTITY` in a `TABLE`.

A `COLUMN` is a vertical `ENTITY` in a `TABLE` that contains all information associated with a specific `FIELD` in a `TABLE`.

# 2. SQL Syntax

A database most often contains one or more `TABLES`.
Each `TABLE` is identified by a name (e.g. "Customers" or "Orders").
`TABLES` contain `RECORDS` (`ROWS`) with data.

The table above contains five `RECORDS` (one for each customer) and seven `COLUMNS` (CustomerID, CustomerName, ContactName, Address, City, PostalCode, and Country).

SQL Statements

Most of the actions you need to perform on a database are done with SQL STATEMENTS.

The following SQL STATEMENT selects all the records in the "Customers" table:

```sql
SELECT * FROM Customers;
```

Keep in Mind That...

- SQL keywords are NOT case sensitive: `select` is the same as `SELECT`
- We will write all SQL keywords in upper-case.

Semicolon after SQL Statements?

Some database systems require a semicolon at the end of each SQL statement.

- Semicolon is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server.
- We will use semicolon at the end of each SQL statement.

Some of The Most Important SQL Commands

- `SELECT` - extracts data from a database
- `UPDATE` - updates data in a database
- `DELETE` - deletes data from a database
- `INSERT INTO` - inserts new data into a database
- `CREATE DATABASE` - creates a new database
- `ALTER DATABASE` - modifies a database
- `CREATE TABLE` - creates a new table
- `ALTER TABLE` - modifies a table
- `DROP TABLE` - deletes a table
- `CREATE INDEX` - creates an index (search key)
- `DROP INDEX` - deletes an index

# 3. SQL `SELECT` Statement

The `SELECT` statement is used to select data from a database.

The data returned is stored in a result table, called the result-set.

## `SELECT` Syntax

```sql
SELECT column1, column2, ...
FROM table_name;
```

Here, column1, column2, ... are the field names of the table you want to select data from. If you want to select all the fields available in the table, use the following syntax:

```sql
SELECT * FROM table_name;
```

## `SELECT` Column Example

The following SQL statement **selects the "CustomerName" and "City" columns from the "Customers" table**:

```sql
SELECT CustomerName, City FROM Customers;
```

## `SELECT *` Example

The following SQL statement **selects all the columns from the "Customers" table**:

```sql
SELECT * FROM Customers;
```

# 4. SQL `SELECT DISTINCT` Statement

The `SELECT DISTINCT` **statement is used to return only distinct (different) values.**

Inside a table, a column often contains many duplicate values; and **sometimes you only want to list the different (distinct) values**.

## `SELECT DISTINCT` Syntax

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

## `SELECT` Example Without `DISTINCT`

The following SQL statement **selects all (including the duplicates) values from the "Country" column in the "Customers" table**:

```sql
SELECT Country FROM Customers;
```

## `SELECT DISTINCT` Examples

The following SQL statement **selects only the DISTINCT values from the "Country" column in the "Customers" table**:

Example

```sql
SELECT DISTINCT Country FROM Customers;
```

The following SQL statement **lists the number of different (distinct) customer countries**:

```sql
SELECT COUNT(DISTINCT Country) FROM Customers;
```

# 5. SQL `WHERE` Clause

The `WHERE` clause is used to filter records.

It is used to extract only those records that fulfill a specified condition.

## `WHERE` Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

Note: The `WHERE` clause is not only used in `SELECT` statements, it is also used in `UPDATE`, `DELETE`, etc.!

## `WHERE` Clause Example

The following SQL statement selects all the customers from the country "Mexico", in the "Customers" table:

```sql
SELECT * FROM Customers
WHERE Country='Mexico';
```

## Text Fields vs. Numeric Fields

**SQL requires single quotes around text values** (most database systems will also allow double quotes).

However,** numeric fields should not be enclosed in quotes**:

```sql
SELECT * FROM Customers
WHERE CustomerID=1;
```

## **Operators** in The `WHERE` Clause

The following operators can be used in the `WHERE` clause:

`=` **Equal**

`>` **Greater than**

`<` **Less than**

`>=` **Greater than or equal**

`<=` **Less than or equal**

`<>` **Not equal. In some versions of SQL this operator may be written as** `!=`

`BETWEEN` **Between a certain range**

`LIKE` **Search for a pattern**

`IN` **To specify multiple possible values for a column**

# 5. SQL `AND`, `OR` and `NOT` Operators

The `WHERE` clause can be combined with `AND`, `OR`, and `NOT` operators.

The `AND` and `OR` operators are **used to filter records based on more than one condition**.

- **The `AND` operator displays a record if all the conditions separated by `AND` are `TRUE`**.
- **The `OR` operator displays a record if any of the conditions separated by `OR` is `TRUE`**.
- **The `NOT` operator displays a record if the condition(s) is NOT TRUE.**

## `AND` Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

## `OR` Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

## `NOT` Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

## `AND` Example

The following SQL statement selects all fields from "Customers" where country is "Germany" AND city is "Berlin":

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';
```

## `OR` Example

The following SQL statement **selects all fields from "Customers" where city is "Berlin" `OR` "München"**:

```sql
SELECT * FROM Customers
WHERE City='Berlin' OR City='München';
```

The following SQL statement **selects all fields from "Customers" where country is "Germany" `OR` "Spain"**:

```sql
SELECT * FROM Customers
WHERE Country='Germany' OR Country='Spain';
NOT Example
```

The following SQL statement **selects all fields from "Customers" where country is `NOT` "Germany"**:

```sql
SELECT * FROM Customers
WHERE NOT Country='Germany';
```

## Combining `AND`, `OR` and `NOT`

You can also combine the `AND`, `OR` and `NOT` operators.

The following SQL statement **selects all fields from "Customers" where country is "Germany" `AND` city must be "Berlin" `OR` "München" (use parenthesis to form complex expressions)**:

```sql
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```

The following SQL statement **selects all fields from "Customers" where country is `NOT` "Germany" and `NOT` "USA"**:

```sql
SELECT * FROM Customers
WHERE NOT Country='Germany' AND NOT Country='USA';
```

# 5. SQL `ORDER BY` Keyword

**The `ORDER BY` keyword is used to sort the result-set in ascending or descending order.**

- **The `ORDER BY` keyword sorts the records in ascending order by default.**
- **To sort the records in descending order, use the `DESC` keyword.**

## `ORDER BY` Syntax

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

## `ORDER BY` Example

The following SQL statement **selects all customers from the "Customers" table, sorted by the "Country" column**:

```sql
SELECT * FROM Customers
ORDER BY Country;
```

## `ORDER BY` DESC Example

The following SQL statement **selects all customers from the "Customers" table, sorted DESCENDING by the "Country" column**:

```sql
SELECT * FROM Customers
ORDER BY Country DESC;
```

## `ORDER BY` Several Columns Example

The following SQL statement **selects all customers from the "Customers" table, sorted by the "Country" and the "CustomerName" column**. `This means that it orders by Country, but if some rows have the same Country, it orders them by CustomerName`:

```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```

## `ORDER BY` Several Columns Example 2

The following SQL statement **selects all customers from the "Customers" table, sorted ascending by the "Country" and descending by the "CustomerName" column**:

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```
