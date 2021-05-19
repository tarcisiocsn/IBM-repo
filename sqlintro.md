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
··· Others Problems
1. Problem 1
··· Retrieve the fun facts and filming locations of all films

```sql
SELECT Locations, FunFacts FROM FilmLocation;
```
2. Problem 2
··· Retrieve the names of all films released in the 20th century and before (release year before 2000 including 2000) that, along filming locations and release years.

```sql
SELECT Title, Locations, ReleaseYear FROM FilmLocations WHERE ReleaseYear <== 2000; 
```
3. Problem 2
··· Retrieve the names, production company, names, filming locations and release years of the films which are not written by James Cameron.

```sql
SELECT Title, ProductionsCompany, Locations, ReleaseYear FROM FilmLocations WHERE Writer <> "James Cameron"; 
```
[See this link](https://labs.cognitiveclass.ai/tools/datasette/?datasette_path=%2F-%2Fadd-datasets%2F%3Fpath%3D%2Fresources%2Fdatasette%2Fcoursera%2FDB0201EN%2Flab1%2FSanFranciscoFilmLocations.sqlite&md_instructions_url=https%3A%2F%2Fcf-courses-data.s3.us.cloud-object-storage.appdomain.cloud%2FIBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork%2Flabs%2FLabs_Coursera_V5%2Flabs%2FLab%2520-%2520Basics%2520of%2520SQL%2520SELECT%2520Statement%2Finstructional-labs.md&lti=true) about the SELECT statement commmand

 ### COUNT, DISTINCT, LIMIT
 1. Count -> It's a built-in database function that `retrieves` the number of rows that match the query criteria.
··· (lembrar que esse interpoint é colocado 
 ``` sql
 SELECT * FROM database
 ```
1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list. 
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
