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

2. Show only the `name` and `frequency` fields for the first 5 records.

3. Find records for people named "John" born in Washington state after 2010.

4. How many people named "John" are there in the dataset?

5. Show situations where girls were named "John". In which states and years 
did this happen the most?

6. What were the top 3 most common female names in New York in the year 2000?
***
### Names Table: Aggregations & Operators
7. How many babies are born each year?

8. How many people named "John" were there per state, per year?

9. Write a query that tells you how many different female names there 
were per state, per year.

10. How many records were there in the years 2000, 2001, and 2002?

11. How many names end with the letter "a" in the table? (Hint: LIKE operator and the % wildcard)

*** 
### Regions Table
12. What are the columns on the region table? (Hint: SELECT * can do the job!)

13. How many different regions are there in the `region` table? (Hint: DISTINCT) Can you find the one that looks like a typo?
