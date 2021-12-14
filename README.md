# SQL BASIC

## Summary

- [What is SQL?](#what-is-sql)
- [What is relational datebase?](#what-is-relational-datebase)
- [What is a table?](#what-is-a-table)
- [What is a row?](#what-is-a-row)
- [What is a column?](#what-is-a-cloumn)
- [What is a query?](#what-is-a-query)
- [SELECT](#select)
- [KEYWORDS](#keywords)
- [Selecting multiple columns.](#selecting-multiple-columns)
- [Selecting all columns.](#selecting-all-columns)
- [Limit number of columns](#limit-number-of-columns)
- [SELECT DISTINCT](#select-distinct)
- [COUNT](#count)
- [Count non-missing values](#count-non-missing-values)
- [WHERE](#where)
- [WHERE AND OR](#where-and-or)

## What is SQL?

SQL stands for Structured Query Language and it is a language for interacting with data stored in something called a relational database.

## What is relational datebase?

It is a collection of tables that contains data.

## What is a table?

A table is just a set of rows and columns and it represents one type of entity.

## What is a row?

Each row is one record. For example if we have table representing movies one row will represent one movie.

## What is a column?

A Column is single attribute for all rows in the table.

## What is a query?

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

## WHERE

Allows us to filter based on both text and numeric values in a table.

Comparison operators that we can use:

- ```=``` equal
- ```<>``` not equal
- ```<``` less than
- ```>``` greater than
- ```<=``` less than or equal to
- ```>=``` greater than or equal to

```
SELECT * FROM people WHERE name = 'Vesna';
```

will return us all rows where persons name is Vesna.

```WHERE``` always comes after ```FROM```

```
SELECT names, surname FROM people WHERE name = 'Vesna';
```

will return us rows with just name and surname where name is Vesna

## WHERE AND

We use for multiple conditions.

```
SELECT * FROM people WHERE name= 'Vesna' AND surname = 'Bozic';
```

## WHERE AND OR

we ```OR``` use when some condition, but not all needs to be met.

```
SELECT name FROM people WHERE birthdate = 1996 OR birthdate = 1987;
```

We can combine ```AND``` and ```OR``` but we need to enclose individual clauses in parentheses

```
SELECT name
FROM people
WHERE (birthdate = 1994 OR birthdate = 1995)
AND (name = 'Vesna' OR name = 'Marko');
```

## BETWEEN

Shorthand for filtering values within a specified range.

```
SELECT *
FROM people
WHERE birthdate >= 1994
AND birthdate <= 2000;
```

with between we can write like :

```
SELECT name
FROM people
WHERE birthdate
BETWEEN 1994 AND 2000;
```

BETWEEN is inclusive, meaning the beginning and end values are included in the results.











