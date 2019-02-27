##SQL

**Sql** is a structured query language used for Storing,Manipulating, and Retrieving data in data base house

**SQL  SELECT**:

SELECT statement is used to select data from database

**Example**:

Lets say we have **Customers Table**

|Customer_id|CustomerName|City|Postalcode|Country|
|----|-----|----|----|----|
|1|Abhishek|Delhi|505213|India|
|2|Rakesh|Noida|505217|India|
|3|Nandan|Ambala|505210|India|
|4|kalyan|New York|003695|United States|

The following SQL statement selects the "CustomerName" and "City" columns from the "Customers" table

SELECT CustomerName, City from Customers

And output of that query would be 

|CustomerName|| City| 
|------|-----|
|Abhishek|Delhi|
|Rakesh|Noida|
|Nandan|Ambala|
|kalyan|New York| 

To select all columns we have to write 
SELECT * FROM Customers 

**SQL WHERE**:

The WHERE clause is used to extract only those records that fulfill a specified condition.

The following SQL statement selects all the customers from the country "United States", in the "Customers" table:

SELECT * FROM Customers

WHERE Country=”United States” 

We get the following Output 

|Cutomer_id|Customername|City|Postalcode|Country|
|----|-----|----|----|----|
|4|kalyan|New York|003695|United States|

 **SQL JOIN**:
 
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.

There are different types of joins 

+ **INNER JOIN**: The INNER JOIN keyword selects records that have matching values in both tables

Lets create **Orders table**

|Order_id|Customer_id|Order_date|Shipper_id|
|---------|-----|-------|-----|
|1003|4|1996-09-18|6|
|2003|3|1996-03-21|3|
|3006|2|1996-08-19|4|

And we have **Customers table**

|Customer_id|Customername|City|Postalcode|Country|
|----|-----|----|----|----|
|1|Abhishek|Delhi|505213|India|
|2|Rakesh|Noida|505217|India|
|3|Nandan|Ambala|505210|India|
|4|kalyan|New York|003695|United States|

The following SQL statement selects all orders with Customer information:  

SELECT Orders.OrderID, Customers.CustomerName
FROM Orders 
INNER JOIN Customers ON 
Orders.CustomerID = Customers.CustomerID;

The output would be 

|Orders_id|CustomerName|
|--------------|---------|
|1003|Kalyan|
|2003|Nandan|
|3006|Rakesh|

+**LEFT JOIN**: The LEFT JOIN keyword returns all records from the left table (table1), and the matched records from the right table (table2). The result is NULL from the right side, if there is no match.

**Example**:

We use Customers and Orders table 

The following SQL statement will select all customers, and any orders they might have

SELECT Customers.CustomerName, Orders.OrderID
FROM Customers 
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID 

We would get the following Output 

|CustomerName|Orders_id|
|----|-----|
|Abhishek|NULL|
|Rakesh| 3006|
|Nandan|2003 |
|kalyan| 1003|

**RIGHT JOIN**: The RIGHT JOIN keyword returns all records from the right table (table2), and the matched records from the left table (table1). The result is NULL from the left side, when there is no match.

Example:

SELECT Customers.CustomerName, Orders.OrderID
FROM Customers 
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID 

 We would get the following Output 
 
|CustomerName|Orders_id|
|----|-----|
|Kalyan||1003|
|Nandan|2006|
|Rakesh|3006|
|NULL|3009|

