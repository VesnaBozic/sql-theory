# SQL BASIC


## What is SQL ?

SQL stands for Structured Query Language and it is a language for interacting with data stored in something called a relational database.

## What is relational datebase?

It is a collection of tables that contains data.

## What is a table?

A table is just a set of rows and columns and it represents one type of entity.

## What is a row?

Each row is one record. For example if we have table representing movies one row will represent one movie.

## What is column?

Column is single attribute for all rows in the table.

## What us a query?

A query is a request for a data from datebase table ( or combination of tables)

## SELECT

```SELECT``` is a statement we use to select data from table.

```SELECT name FROM people;```

will return to us all the names in the people table

## KEYWORDS

```SELECT``` and ```FROM``` are keywords.

In SQL keywords are not case-sensitive, but it is good practice to write keywords UPPERCASE 

Semicolon ```;``` at the end of query isn't necessary but it is also good practice to put it at the end of our query.

## Selecting multiple columns.

To do that we just separate the column names with commas.

```SELECT name, surname FROM people;```

## Selecting all columns.

```
SELECT * FROM people;
```

will select everything from a table.

## Limit number of columns

If we want select all columns but limit return we use

```SELECT * FROM people LIMIT 10```

## SELECT DISTINCT

When we want to select all the unique values from a column we use DISTINCT

```
SELECT DISTINCT language from films;
```

## COUNT

We use COUNT to count number of rows 

```
SELECT COUNT(*) FROM people;
```

will return number od rows in people table;

## Count non-missing values

if we want to count the number of non-missing values in a particular column, we can call ```COUNT()``` on just that column

```
SELECT COUNT(adress) FROM people;
```

will count number of adresses in people table

if use DISTINCT

```
SELECT COUNT(DISTINCT adress) FROM people;
```

it will count just unique adresses









