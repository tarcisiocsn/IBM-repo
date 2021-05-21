# SQL Intro - DB 201

## 1.0 What is SQL? (Structured English Query Language)
1. A language used for relational databases
2. Query data 

## 2.0 What is Data?
1. Facts ( words, pics)
2. Pictures
3. One of the most assets of any business
4. Needs to be secure

## 3.0 What is a Database?
1. A repository of data ( a program that stores data)
2. Provides the functionality for adding, modifing and querying that data

### 3.1 Relational Database
1. Data Stored in tabular form (column x row)

## DBMS -> Database management system and RDBMS -> Relational database management system
1. The terms database, database server, database system, data server, and database management systems are often used interchangeably.
2. RDBMS is a set of software tools that controls the data such as access, organization, and storage. And RDBMS serves as the backbone of applications in many industries including banking, transportation, health, and so on.

## 5 Basic Commands in SQL
1. Insert data to populate the table,
2. select data from the table,
3. update data in the table,
4. Delete data from the table.

### Select Statement command
After `creating a table` and `inserting data into`, we want to see the data

``` sql
SELECT * FROM FilmLocations;

SELECT Title, Director, Writer FROM FilmLocations;

SELECT Title, ReleaseYear, Locations FROM Filmlocations WHERE ReleaseYear >= 2001;
```
Others Problems

1. Problem 1

Retrieve the fun facts and filming locations of all films

```sql
SELECT Locations, FunFacts FROM FilmLocation;
```
2. Problem 2

Retrieve the names of all films released in the 20th century and before (release year before 2000 including 2000) that, along filming locations and release years.

```sql
SELECT Title, Locations, ReleaseYear FROM FilmLocations WHERE ReleaseYear <== 2000; 
```
3. Problem 3

Retrieve the names, production company, names, filming locations and release years of the films which are not written by James Cameron.

```sql
SELECT Title, ProductionsCompany, Locations, ReleaseYear FROM FilmLocations WHERE Writer <> "James Cameron"; 
```
[See this link](https://labs.cognitiveclass.ai/tools/datasette/?datasette_path=%2F-%2Fadd-datasets%2F%3Fpath%3D%2Fresources%2Fdatasette%2Fcoursera%2FDB0201EN%2Flab1%2FSanFranciscoFilmLocations.sqlite&md_instructions_url=https%3A%2F%2Fcf-courses-data.s3.us.cloud-object-storage.appdomain.cloud%2FIBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork%2Flabs%2FLabs_Coursera_V5%2Flabs%2FLab%2520-%2520Basics%2520of%2520SQL%2520SELECT%2520Statement%2Finstructional-labs.md&lti=true) about the SELECT statement commmand

 ### COUNT, DISTINCT, LIMIT
 1. Count -> It's a built-in database function that `retrieves` the number of rows that match the query criteria.
 
··· Example 1 -> Get the total number of rows in a given table,
 ``` sql
 select COUNT(*) from tablename
 ```
 > Shift + Option + 9 -> Interpoint 
 
 ··· Example -> Let's say you create a table called MEDALS which has a column called COUNTRY, and you want to retrieve the number of rows where the medal recipient is from Canada.
 ``` sql
 select COUNT(COUNTRY) from MEDALS where COUNTRY = "Canada; 
 
 ```
2. Distinct -> It's used to remove duplicate values from a result set.

 ··· Example -> to retrieve unique values in a column.
 ```sql
 select DISTINCT columname from Table
```
> In the MEDALS table mentioned earlier, a country may have received a gold medal multiple times.

··· Example -> retrieve the list of unique countries that received gold medals (That is, removing all duplicate values of the same country).
```sql
select DISTINCT COUNTRY from MEDALS where MEDALTYPE = 'GOLD'
```
3. Limit -> It's used for restricting the number of rows retrieved from the database.

··· Example -> Retrieve just the first 10 rows in a table.

```sql
select * from tablename LIMIT 10
```
··· Example -> Retrieve just a few rows in the MEDALS table for a particular year.

```sql 
select * from MEDALS where YEAR = 10 LIMIT 5
```
Output

| COUNTRY      | GOLD  | SILVER | BRONZE | TOTAL   | YEAR  |
| ------------ | :---: | :---:  | :----: | -----:  | :---: |
| Norway       | 18    | 14     | 11     | 39      | 2018  |
| Germany      | :---: | :---:  | :----: | -----:  | 2018  |
| USA          | :---: | :---:  | :----: | -----:  | 2018  |
| Canada       | :---: | :---:  | :----: | -----:  | 2018  |
| Brazil       | :---: | :---:  | :----: | -----:  | 2018  |


| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

OTHERS PROBLEMS

COUNT

Problem 1. In this example, now we want to count the number of locations of the films. But we also want to restrict the output resultset in such a way that we only retrieve the number of locations of the films written by a certain writer.

``` sql
select count(Locations) from FilmLocations where Writer = 'James Cameron'; 
```

Problem 2. Retrieve the number of locations of the films which are directed by Woody Allen.
``` sql
select count(Locations) from FilmLocations where Director = 'Woody Allen'; 
```

Problem 3. Retrieve the number of films shot at Russian Hill.
``` sql
select count(Locations) from FilmLocations where Locations = 'Russian Hill'; 
```
Problem 4. Retrieve the number of rows having a release year older than 1950 from the "FilmLocations" table.
``` sql
select count(ReleaseYear) from FilmLocations where ReleaseYear < 1950; 
```

DISTINCT

Problem 1. In this example, we want to retrieve the title of all films in the table in such a way that duplicates will be discarded in the output resultset.
> Retrieve the name of all films without any repeated titles.

```sql
select distinct Title from FilmLocations;

vamos encontrar uma tabela com os títulos não repetidos
```

Problem 2. In this example, we want to retrieve the count of release years of the films produced by a specific company in such a way that duplicate release years of those films will be discarded in the count.
> Retrieve the number of release years of the films distinctly, produced by Warner Bros. Pictures.

```sql
select count(distinct ReleaseYears) from FilmLocations where ProductionCompany = "Warner Bros.";

vamos encontrar o número de produções feitas ao longo do tempo, mas não contará as produções duplicadas de anos
```

Problem 3. Retrieve the name of all unique films released in the 21st century and onwards, along with their release years.
```sql
select distinct Title, ReleaseYear from FilmLocations where ReleaseYear >= 2001;

```
Output

![alt text](<img width="528" alt="image" src="https://user-images.githubusercontent.com/68601128/119020585-c8bb6000-b974-11eb-82d1-6303f2070af1.png">"Logo Title Text 1")

Problem 4. Retrieve the number of distributors distinctly who distributed films acted by Clint Eastwood as 1st actor.
```sql
select count(distinct Distributor) from FilmLocations where Actor1 = 'Clint Eastwood';

```
LIMIT

Problem 1. Retrieve the first 25 rows from the "FilmLocations" table.

```sql 
select * from FilmLocations limit 25;
``` 

Problem 2. Retrieve the first 15 rows from the "FilmLocations" table starting from row 11.

```sql 
select * from FilmLocations limit 15 offset 10;

```

Problem 3. Retrieve the name of first 50 films distinctly.

```sql 
select * distinct Title from FilmLocations limit 50;

```

Problem 4. Retrieve the next 3 film names distinctly after first 5 films released in 2015.
```sql 
select * distinct Title from FilmLocations where YearRelease = 2015 limit 3 offset 5;
```

### INSERT STATEMENT

Adding a row in a table
··* Create the table (CREATE TABLE statement)

··* Populate Table with data:

··· INSERT 
··· A data manipulate language (DML) statement used to read and modify data

```sql
INSERT INTO table_name (column1, column2, ... )
VALUES (value1, value2, ... )
;

```
### UPDATE & DELETE STATEMENT

After create a table and inserting data into the table, we can alter the data
··· UPDATE & DELETE STATEMENT -> A DML statement used to read and modify data

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition
;

```
```sql
DELETE FROM table_name
WHERE condition
;

```

**Example INSERT**
In this example, suppose we want to insert a new single row into the Instructor table.
1. Problem
> Insert a new instructor record with id 4 for Sandip Saha who lives in Edmonton, CA into the "Instructor" table.

```sql 

INSERT INTO Instructor(ins_id, lastname, firstname, city, country)
VALUES(4, 'Saha', 'Sandip', 'Edmonton', 'CA');

# Then, see the change with the statement:
select * from Instructor
```

In this example, suppose we want to insert some new multiple rows into the Instructor table.

2. Problem
> Insert two new instructor records into the "Instructor" table. First record with id 5 for John Doe who lives in Sydney, AU. Second record with id 6 for Jane Doe who lives in Dhaka, BD.

Agora terá mais 2 nomes

```sql 
# lembrar de colocar '' nas strings 

INSERT INTO Instructor(ins_id, lastname, firstname, city, country)
VALUES(5, 'Doe', 'John', 'Sydney', 'AU'), (6, 'Doe', 'Jane', 'Dhaka', 'BD');

# Then, see the change with the statement:
select * from Instructor
```
OUTPUT

<img width="512" alt="image" src="https://user-images.githubusercontent.com/68601128/119172031-c6700900-ba3b-11eb-8360-99f76b15cbc1.png">

**Example UPDATE**
In this example, we want to update one column of an existing row of the table.
> 1 Problem. Update the city for Sandip to Toronto.
```SQL
UPDATE Instructor 
SET city='Toronto' 
WHERE firstname="Sandip";

select * from Instructor;
```
OUTPUT

<img width="509" alt="image" src="https://user-images.githubusercontent.com/68601128/119173441-a6d9e000-ba3d-11eb-8f47-fcd847770e07.png">

In this example, we want to update multiple columns of an existing row of the table.
> 2 Problem. Update the city and country for Doe with id 5 to Dubai and AE respectively.

```sql 
UPDATE Instructor 
SET city='Dubai', country='AE' 
WHERE ins_id=5;

SELECT * FROM Instructor;
```
OUTPUT

<img width="510" alt="image" src="https://user-images.githubusercontent.com/68601128/119173677-f7e9d400-ba3d-11eb-8e72-ed6696e99896.png">

**Example DELETE**
In this example, we want to remove a row from the table
> Remove the instructor record of Doe whose id is 6.

```sql
DELETE FROM instructor
WHERE ins_id = 6;

select * from Instructor;
``` 
OUTPUT

<img width="487" alt="image" src="https://user-images.githubusercontent.com/68601128/119174534-13091380-ba3f-11eb-8870-acc69a84614a.png">

> 1 Problem 

```sql 
delete from instructor 
where city = 'Hima'; 

select * from instructor
```
OUTPUT

<img width="510" alt="image" src="https://user-images.githubusercontent.com/68601128/119174828-74c97d80-ba3f-11eb-8b19-2fcbc03441d3.png">

## Database Concepts

Relational Model

1. Most used data model
2. Allows for data independence
3. Data is stored in a tables

### Entity-Relathioship Model 

<img width="607" alt="image" src="https://user-images.githubusercontent.com/68601128/119176845-f4f0e280-ba41-11eb-8a56-6fc6f676a24b.png">

Mapping Entity Diagrams to Table

<img width="551" alt="image" src="https://user-images.githubusercontent.com/68601128/119177027-22d62700-ba42-11eb-88f8-4f9c66a0efd6.png">

Primary Keys and Foreing Keys

<img width="595" alt="image" src="https://user-images.githubusercontent.com/68601128/119177129-3f725f00-ba42-11eb-95f1-20c875cb1b70.png">

### How to Create a Database Instance on Cloud

In order to learn SQL, you first need to have a database available to practice your SQL queries. An easy way to do so is to create an instance of a database in the Cloud and use it to execute your SQL queries.

<img width="576" alt="image" src="https://user-images.githubusercontent.com/68601128/119177508-caebf000-ba42-11eb-9e6c-a060bd8ba711.png">

To see how tu use [click here](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Sign%20up%20for%20IBM%20Cloud%20-%20Create%20Db2%20service%20instance%20-%20Get%20started%20with%20the%20Db2%20console/instructional-labs.md.html).


