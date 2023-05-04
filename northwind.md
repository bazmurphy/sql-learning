# Setup

In the terminal:

create a database called northwind:

`createdb northwind`

populate the database using the provided sql file:

`psql -d northwind -f northwind.sql`

login and use the database:

`psql -d northwind`

test it populated correctly:

`SELECT * FROM Customers;`
