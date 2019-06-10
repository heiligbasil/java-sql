# java-sql

A student that completes this project shows that they can:
* Query data from a single table
* Query data from multiple tables
* Create a new datadaase using PostgreSQL

# Introduction

Working with SQL

# Instructions

Surf to [SQL Try Editor at W3Schools.com](https://www.w3schools.com/Sql/tryit.asp?filename=trysql_select_top)  
Answer the following data queries. Keep track of the SQL you write by pasting it into this document under its appropriate header below. You will be submitting that through the regular fork, change, pull process.

### **Clicking the `Restore Database` button in the page will repopulate the database with the original data and discard all changes you have made**.

### find all customers that live in London. Returns 6 records.
> _SELECT * FROM Customers WHERE city = 'London'_  
CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country  
4	Around the Horn	Thomas Hardy	120 Hanover Sq.	London	WA1 1DP	UK  
11	B's Beverages	Victoria Ashworth	Fauntleroy Circus	London	EC2 5NT	UK  
16	Consolidated Holdings	Elizabeth Brown	Berkeley Gardens 12 Brewery	London	WX1 6LT	UK  
19	Eastern Connection	Ann Devon	35 King George	London	WX3 6FW	UK  
53	North/South	Simon Crowther	South House 300 Queensbridge	London	SW7 1RZ	UK  
72	Seven Seas Imports	Hari Kumar	90 Wadhurst Rd.	London	OX15 4NB	UK  

### find all customers with postal code 1010. Returns 3 customers.
> _SELECT * FROM Customers WHERE PostalCode = '1010'_  
CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country  
12	Cactus Comidas para llevar	Patricio Simpson	Cerrito 333	Buenos Aires	1010	Argentina  
54	Océano Atlántico Ltda.	Yvonne Moncada	Ing. Gustavo Moncada 8585 Piso 20-A	Buenos Aires	1010	Argentina  
64	Rancho grande	Sergio Gutiérrez	Av. del Libertador 900	Buenos Aires	1010	Argentina  

### find the phone number for the supplier with the id 11. Should be (010) 9984510.
> _SELECT Phone FROM [Suppliers] WHERE SupplierID = '11'_  
Phone  
(010) 9984510  

### list orders descending by the order date. The order with date 1997-02-12 should be at the top.
> _SELECT * FROM Orders ORDER BY OrderDate DESC_  
OrderID	CustomerID	EmployeeID	OrderDate	ShipperID  
10443	66	8	1997-02-12	1  
10442	20	3	1997-02-11	2  
10440	71	4	1997-02-10	2  
10441	55	3	1997-02-10	2  
10439	51	6	1997-02-07	3  
10438	79	3	1997-02-06	2  
10436	7	3	1997-02-05	2  
...  
10254	14	5	1996-07-11	2  
10253	34	3	1996-07-10	2  
10252	76	4	1996-07-09	2  
10250	34	4	1996-07-08	2  
10251	84	3	1996-07-08	1  
10249	81	6	1996-07-05	1  
10248	90	5	1996-07-04	3  

### find all suppliers who have names longer than 20 characters. You can use `length(SupplierName)` to get the length of the name. Returns 11 records.
> _SELECT * FROM Suppliers WHERE length(SupplierName) > 20_  
SupplierID	SupplierName	ContactName	Address	City	PostalCode	Country	Phone  
2	New Orleans Cajun Delights	Shelley Burke	P.O. Box 78934	New Orleans	70117	USA	(100) 555-4822  
3	Grandma Kelly's Homestead	Regina Murphy	707 Oxford Rd.	Ann Arbor	48104	USA	(313) 555-5735  
5	Cooperativa de Quesos 'Las Cabras'	Antonio del Valle Saavedra	Calle del Rosal 4	Oviedo	33007	Spain	(98) 598 76 54  
8	Specialty Biscuits, Ltd.	Peter Wilson	29 King's Way	Manchester	M14 GSD	UK	(161) 555-4448  
10	Refrescos Americanas LTDA	Carlos Diaz	Av. das Americanas 12.890	São Paulo	5442	Brazil	(11) 555 4640  
11	Heli Süßwaren GmbH & Co. KG	Petra Winkler	Tiergartenstraße 5	Berlin	10785	Germany	(010) 9984510  
12	Plutzer Lebensmittelgroßmärkte AG	Martin Bein	Bogenallee 51	Frankfurt	60439	Germany	(069) 992755  
13	Nord-Ost-Fisch Handelsgesellschaft mbH	Sven Petersen	Frahmredder 112a	Cuxhaven	27478	Germany	(04721) 8713  
14	Formaggi Fortini s.r.l.	Elio Rossi	Viale Dante, 75	Ravenna	48100	Italy	(0544) 60323  
18	Aux joyeux ecclésiastiques	Guylène Nodier	203, Rue des Francs-Bourgeois	Paris	75004	France	(1) 03.83.00.68  
19	New England Seafood Cannery	Robb Merchant	Order Processing Dept. 2100 Paul Revere Blvd.	Boston	02134	USA	(617) 555-3267  

### find all customers that include the word "market" in the name. Should return 4 records.
> _SELECT * FROM Customers WHERE CustomerName LIKE '%market%'_  
CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country  
10	Bottom-Dollar Marketse	Elizabeth Lincoln	23 Tsawassen Blvd.	Tsawassen	T2F 8M4	Canada  
32	Great Lakes Food Market	Howard Snyder	2732 Baker Blvd.	Eugene	97403	USA  
71	Save-a-lot Markets	Jose Pavarotti	187 Suffolk Ln.	Boise	83720	USA  
89	White Clover Markets	Karl Jablonski	305 - 14th Ave. S. Suite 3B	Seattle	98128	USA  

### add a customer record for _"The Shire"_, the contact name is _"Bilbo Baggins"_ the address is _"1 Hobbit-Hole"_ in _"Bag End"_, postal code _"111"_ and the country is _"Middle Earth"_.
> _INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country) VALUES ('The Shire', 'Bilbo Baggins', '1 Hobbit-Hole', 'Bag End', '111', 'Middle Earth')_  
CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country  
92	The Shire	Bilbo Baggins	1 Hobbit-Hole	Bag End	111	Middle Earth  

### update _Bilbo Baggins_ record so that the postal code changes to _"11122"_.
> _UPDATE Customers SET PostalCode = '11122' WHERE CustomerName = 'The Shire'_  
CustomerID	CustomerName	ContactName	Address	City	PostalCode	Country  
92	The Shire	Bilbo Baggins	1 Hobbit-Hole	Bag End	11122	Middle Earth  

### list orders grouped by customer showing the number of orders per customer. _Rattlesnake Canyon Grocery_ should have 7 orders.
> This can be done with SELECT, COUNT, JOIN and GROUP BY clauses. Your count should focus on a field in the Orders table, not the Customer table

> There is more information about the COUNT clause on [W3 Schools](https://www.w3schools.com/sql/sql_count_avg_sum.asp)

### list customers names and the number of orders per customer. Sort the list by number of orders in descending order. _Ernst Handel_ should be at the top with 10 orders followed by _QUICK-Stop_, _Rattlesnake Canyon Grocery_ and _Wartian Herkku_ with 7 orders each.
> This can be done by adding an ORDER BY clause to the previous answer

### list orders grouped by customer's city showing number of orders per city. Returns 58 Records with _Aachen_ showing 2 orders and _Albuquerque_ showing 7 orders.
> This is very similar to the previous two queries, however, it focuses on the City rather than the CustomerName

## Stretch Goals

### delete all customers that have no orders. Should delete 17 (or 18 if you haven't deleted the record added) records.
> This is done with a DELETE query

> In the WHERE clause, you can provide another list with an IN keyword this list can be the result of another SELECT query. Write a query to return a list of CustomerIDs that meet the criteria above. Pass that to the IN keyword of the WHERE clause as the list of IDs to be deleted
 
> Use a LEFT JOIN to join the Orders table onto the Customers table and check for a NULL value in the OrderID column

## Create Database and Table

### Keep track of the code you write and paste at the end of this document

- use pgAdmin to create a database, naming it `budget`.
- add an `accounts` table with the following _schema_:

  - `id`, numeric value with no decimal places that should autoincrement.
  - `name`, string, add whatever is necessary to make searching by name faster.
  - `budget` numeric value.

- constraints
  - the `id` should be the primary key for the table.
  - account `name` should be unique.
  - account `budget` is required.
