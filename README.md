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
- [BETWEEN](#between)
- [WHERE IN](#where-in)
- [NULL](#null)
- [LIKE](#like)
- [NOT LIKE](#not-like)
- [Aggregate functions](#aggregate-functions)
- [Arithmetic](#arithmetic)
- [ALIASING](#aliasing)
- [ORDER BY](#order-by)
- [GROUP BY](#group-by)
- [HAVING](#having)
- [INNER JOIN](#inner-join)
- [USING](#using)
- [SELF JOIN](#self-join)
- [CASE WHEN AND THEN](#case-when-and-then)
- [LEFT JOIN](#left-join)
- [RIGHT JOIN](#right-join)
- [FULL JOIN](#full-join)
- [CROSS JOIN](#cross-join)
- [UNION](#union)
- [UNION ALL](#union-all)

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

## WHERE IN

IN operator allows us to specify multiple values in a WHERE clause, making it easier and quicker to specify multiple OR conditions

QUERY :
```
SELECT name
FROM people
WHERE age = 2
OR age = 4
OR age = 6
OR age = 8
OR age = 10;
```

we can write 

```
SELECT name
FROM people
WHERE age IN (2, 4, 6, 8, 10);
```

## NULL

NULL represents a missing or unknown value. 

We can check is something has null value using expresion ```IS NULL```
```
SELECT *
FROM people
WHERE birthdate IS NULL;
```

## LIKE AND NOT LIKE

The SQL ```LIKE``` and ```NOT LIKE``` operators are used to find matches between a string and a given pattern.

The SQL ```LIKE``` is a logical operator that checks whether or not a string contains a specified pattern

```
SELECT name
FROM peole
WHERE surname LIKE 'Bozic'
```

Equals (=) is a comparison operator that operates on numbers and strings. When comparing strings, the equals operator compares whole strings. In comparison, LIKE compares character by character through the use of wildcards.

WILDCARDS : ```(%)``` AND ```(_)```

Wildcard characters are used to substitute for one or more characters in a pattern string:

- The percent ```(%)``` wildcard substitutes for one or more characters in a string.
- The underscore ```(_)``` wildcard substitutes for exactly one character in a string.

#### The Underscore (_) Wildcard

Imagine we want to retrieve, from the table ```people```, the first names of the persons with the following conditions:

The FirstName must start with the letter “T”,
The third letter of FirstName must be “m”, and
The second letter FirstName can be anything.

```
SELECT FirstName
FROM people
WHERE FirstName LIKE 'T_m'
```

result Tom, Tim

The second letter of the name can be anything. Our SQL query is ignoring that letter and looking for the pattern we have specified.

#### The Percent (%) Wildcard

The percent (%) wildcard is used to substitute for multiple characters.

Imagine we want to find all the people whose last name ends in “son”. To achieve this, we can simply write the following query:

```
SELECT *
FROM people
WHERE surname LIKE '%ic'
```

Result : Bozic, Jankovic

Notice how the number of characters before “ic” does not matter with this wildcard

## NOT LIKE

```NOT LIKE``` behaves  essentially returning the opposite of what the LIKE operator would.

```
SELECT *
FROM people
WHERE surname NOT LIKE '%ic'
```

will return every person that doesn't have at the end of surname "ic"


## Aggregate functions

We use aggregate functions to perform some calculation on the data in a database.

#### AVG (average value of column)
```
SELECT AVG(salary)
FROM people;
```

will give us average value from salary column of the people table.

#### MAX (maximum value of column)

```
SELECT MAX(salary)
FROM people;
```
return us maximum salary of the people table

#### MIN (minimum value of column)

```
SELECT MIN(salary)
FROM people;
```
return us minimum salary of the people table

#### SUM (sum of all columns)

```
SELECT SUM(salary)
FROM people;
```

## Arithmetic

We can perform basic arithmetic with symbols like ```+```, ```-```, ```*```, and ```/```

```
SELECT (4*3)
```

RESULT : 12

The following query 

```
SELECT (4/3)
```

RESULT : 1

SQL assumes that if you divide an integer by an integer, you want to get an integer back. 

IfWE want more precision when dividing, WE can add decimal places to your numbers. 

```
SELECT (4.0 / 3.0) AS result;
```

RESULET : 1.333

## ALIASING

```
SELECT MAX(budget), MAX(duration)
FROM films;
```

Now we have two columns named max, which isn't very useful.

To avoid situations like this, SQL allows you to do something called aliasing. Aliasing simply means you assign a temporary name to something.

To alias we use ```AS``` keyword.

```
SELECT MAX(budget) AS max_budget,
       MAX(duration) AS max_duration
FROM films;
```

## ORDER BY

```ORDER BY``` is used to sort results in ascending or descending order according to the values of one or more columns.

By default ```ORDER BY``` will sort in ascending order. If you want to sort the results in descending order, you can use the ```DESC``` keyword.

```
SELECT name
FROM people
ORDER BY name
```
and query for descending

```
SELECT name
FROM people
ORDER BY name DESC
```

#### SORTING MULTIPLE COLUMNS

```
SELECT birthdate, name
FROM people
ORDER BY birthdate, name;
```

wil first sort birthdates from oldest to newest and then names in alphabetical order.


## GROUP BY

We use for aggregating results.

For example, we might want to count the number of male and female in people table. In that case we want to group all the males together and count them, and group all the females together and count them. In SQL, ```GROUP BY``` allows us to group a result by one or more columns.

Query would be: 

```
SELECT sex, count(*)
FROM people
GROUP BY sex;
````

```GROUP BY``` always comes after ```FROM```

We can use it with ```ORDER BY```

```
SELECT sex, count(*)
FROM people
GROUP BY sex
ORDER BY count DESC;
```

```ORDER BY``` always come after ```GROUP BY```


## HAVING

If we want to filter based on the result of an aggregate function, we can't use ```WHERE```

We use ```HAVING``` instead

```
SELECT birthyear
FROM people
GROUP BY birthyear
HAVING COUNT(birthyear) > 1990;
```
This will show us all people born after 1990


## INNER JOIN

The ```INNER JOIN``` keyword selects records that have matching values in both tables.
It returns only those rows that have a match in both joined tables.

![inner_join](/inner-join.jpg)


```
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```

![inner-join](/inner-join2.jpg)

## USING

When the key field we'd like to join on is the same name in both tables, we can use a ```USING``` clause instead of the ON clause.

Since id is the same name in both the left table and the right table we can specify USING instead of ON here. Note that the parentheses are required around the key field with USING.

## SELF JOIN

A self join is a regular join, but the table is joined with itself. Self join links a table to itself. 

To use a self join, the table must contain a column (call it X) that acts as the primary key and a different column (call it Y) that stores values that can be matched up with the values in Column X.

## CASE WHEN AND THEN

You can use CASE with ```WHEN```, ```THEN```, ```ELSE```, and ```END``` to define a new grouping field.

```
SELECT name, salary
CASE
    WHEN salary > 3000 THEN 'high'
    WHEN salary > 1500 THEN 'medium'
    ELSE 'low' END
FROM employees

```

## LEFT JOIN

The ```LEFT JOIN``` returns all rows from the left table and the matching rows from the right table. If no matching rows are found in the right table, ```NULL``` are used.

![left-join](/left_join.jpg)


```
SELECT * FROM table1
LEFT JOIN table2
ON table1.name = table2.name;
```

## RIGHT JOIN

A RIGHT JOIN performs a join starting with the right table.

Then, any matching records from the left table will be included.

Rows without a match will have NULL column values.

![right-join](/right-join.jpg)

```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```

## FULL JOIN

A FULL JOIN returns all records from both tables.

This includes records that do not match.

Rows without a match will have NULL column values.


![full-join](/full-join.jpg)

```
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;
```

## CROSS JOIN

CROSS JOIN is used to combine all possibilities of the two or more tables and returns the result that contains every row from all contributing tables. The CROSS JOIN is also known as CARTESIAN JOIN, which provides the Cartesian product of all associated tables. The Cartesian product can be explained as all rows present in the first table multiplied by all rows present in the second table. It is similar to the Inner Join, where the join condition is not available with this clause.


![cross-join](/cross-join.jpg)

```
SELECT *
FROM table1
CROSS JOIN table2
```

## UNION

The ```UNION``` operator is used to combine the result-set of two or more ```SELECT``` statements.

>Every SELECT statement within UNION must have the same number of columns

>The columns must also have similar data types

>The columns in every SELECT statement must also be in the same order

![union](/union.jpg)


```
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

## UNION ALL

Does same as ```UNION```  but return duplicate values

![union-all](/union-all.jpg)

```
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```











































