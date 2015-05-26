###2014-2015, WDI COURSE ASSIGNMENT
####Learning Database SQL (Structured Query Language)
***

# Apartment lab

- Create a database called apartmentlab

* CREATE DATABASE apartmentlab;

- Using this database, create two tables, one for owners and one for properties
- Keep this relationship in mind when designing your schema:
	+ **One owner can have many properties**

###Tables

- The owners table should consist of:
	+ owner_id (this should be the primary key as well as a unique number that increments automatically)
	+ name
	+ age

```
CREATE TABLE owners (
    owner_id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    age INTEGER
    );
```


- The properties table should consist of:
	+ property_id (this should be the primary key as well as a unique number that increments automatically)
	+ name
	+ number of units
	+ owner_id (this should have the constraint NOT NULL)
		+ There should be also be a foreign key that references the owners table

```
CREATE TABLE properties (
    property_id SERIAL PRIMAY KEY,
    name VARCHAR(50),
    num_units INTEGER,
    owner_Id INTEGER NOT NULL,
    FOREIGN KEY (owner_id) REFERENCES owners(owner_id)
    );
```


###Questions
Write down the following sql statements that are required to solve the following tasks.

```
1. Show all the tables.
* \dt

2. Show all the users.
* \du

3. Show all the data in the owners table.
* SELECT * FROM owners;

4. Show the names of all owners.
* SELECT name from owners;

5. Show the ages of all of the owners in ascending order.
* SELECT * FROM owners ORDER BY ASC;

6. Show the name of an owner whose name is Donald.
* SELECT name FROM owners WHERE name = 'Donald';

7. Show the age of all owners who are older than 30.
* SELECT * FROM owners WHERE age > 30;

8. Show the name of all owners whose name starts with an E.
* SELECT * FROM owners WHERE ame LIKE %E%;

9. Add an owner named John who is 33 years old to the owners table.
* INSERT INTO owners (name, age) VALUES ('John',33);

10. Add an owner named Jane who is 43 years old to the owners table.
* INSERT INTO owners (name, age) VALUES ('Jane',43);

11. Change Jane's age to 30.
* UPDATE owners SET age = '43' WHERE age = '30';

12. Change Jane's name to Janet.
* UPDATE owners SET name = 'Janet' WHERE name = 'JANE';

13. Add a property named Archstone that has 20 units.
* INSERT INTO properties (name, num_units) VALUES ('Archstone', 20);

14. Delete the owner named Jane.
* DELETE name FROM owners WHERE name = 'Jane';

15. Show all of the properties in alphabetical order that are not named Archstone and do not have an id of 3 or 5.
* SELECT * FROM properterws WHERE name <> 'Archstone' AND property_id NOT IN (3,5) ORDER BY ASC;

16. Count the total number of rows in the properties table.
* SELECT count(*) FROM properties;

17. Show the highest age of all owners.
* SELECT MAX(age) FROM owners;

18. Show the names of the first three owners in your owners table.
* SELECT * FROM owners LIMIT 3;


```
Bonus (this might require you to look up documentation online)

```
1. In the properties table change the name of the column "name" to "property_name".
* ALTER TABLE properties RENAME COLUMN name TO property_name;

2. Count the total number of properties where the owner_id is between 1 and 3.
* SELECT COUNT(*) FROM properties WHERE owner_id <=3 and owner_id >=1;
```
