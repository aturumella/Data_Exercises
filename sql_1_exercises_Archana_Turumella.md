# SQL 1 Exercises

## Submitting Your Work
* Use this file as a starting point and submit a file to canvas of the form: ***sql_1_exercises_firstname_lastname.md***
* Under each question include the sql queries used to answer the question as well as your final answer
* Sql queries should be placed after 4 tildas (~) followed by sql and ended with 4 tildas. Like so:

~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
***
## Instructions
Open up DB Browser for SQLite
* Open the baby_names database
* Remember that you'll need to navigate to the Execute SQL tab, type in a SQL query and run the query by clicking on the triangle button.
* Query the baby_names database to answer the following questions


*** 
### Names Table: Basics
1. Show the top 10 rows from the `names` table. What does each row of data represent in this table?
~~~~ sql
SELECT * FROM names LIMIT 10;
~~~~
Each row represents the details of a baby name such as the frequency it was uses, which state it was used, which year and gender of the name.
| state | gender | year | name      | frequency |
|-------|--------|------|-----------|-----------|
| AK    | F      | 1951 | Linda     | 79        |
| AK    | F      | 1951 | Mary      | 77        |
| AK    | F      | 1951 | Patricia  | 45        |
| AK    | F      | 1951 | Susan     | 45        |
| AK    | F      | 1951 | Barbara   | 35        |
| AK    | F      | 1951 | Kathleen  | 29        |
| AK    | F      | 1951 | Sandra    | 29        |
| AK    | F      | 1951 | Margaret  | 28        |
| AK    | F      | 1951 | Carol     | 27        |
| AK    | F      | 1951 | Elizabeth | 26        |

2. Show only the `name` and `frequency` fields for the first 5 records.
~~~~ sql
SELECT  name , frequency FROM names LIMIT 5;
~~~~
| name     | frequency |
|----------|-----------|
| Linda    | 79        |
| Mary     | 77        |
| Patricia | 45        |
| Susan    | 45        |
| Barbara  | 35        |

3. Find records for people named "John" born in Washington state after 2010.
~~~~ sql
SELECT  *  FROM  names
WHERE  name  =  'John' AND
state = 'WA' AND
year  > 2010;
~~~~
| state | gender | year | name | frequency |
|-------|--------|------|------|-----------|
| WA    | M      | 2011 | John | 177       |
| WA    | M      | 2012 | John | 184       |
| WA    | M      | 2013 | John | 184       |
| WA    | M      | 2014 | John | 142       |
| WA    | M      | 2015 | John | 165       |
| WA    | M      | 2016 | John | 171       |

4. How many people named "John" are there in the dataset?
~~~~ sql
SELECT  COUNT(*)  FROM  names
WHERE  name  =  'John';
~~~~
There are 4110 people named "John" in the dataset.

5. Show situations where girls were named "John". In which states and years 
did this happen the most?
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
6. What were the top 3 most common female names in New York in the year 2000?
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
***
### Names Table: Aggregations & Operators
7. How many babies are born each year?
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
8. How many people named "John" were there per state, per year?
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
9. Write a query that tells you how many different female names there 
were per state, per year.
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
10. How many records were there in the years 2000, 2001, and 2002?
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
11. How many names end with the letter "a" in the table? (Hint: LIKE operator and the % wildcard)
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
*** 
### Regions Table
12. What are the columns on the region table? (Hint: SELECT * can do the job!)
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
13. How many different regions are there in the `region` table? (Hint: DISTINCT) Can you find the one that looks like a typo?
~~~~ sql
<INSERT SQL QUERIES HERE>
~~~~
