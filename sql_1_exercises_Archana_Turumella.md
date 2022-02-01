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
SELECT state, sum(frequency) AS sum_freq 
FROM names 
WHERE trim(gender) = 'F' AND upper(name) = 'JOHN' 
GROUP BY state 
ORDER BY sum(frequency) DESC
LIMIT 5;
~~~~
| state | sum_freq |
|-------|----------|
| CA    | 929      |
| NY    | 805      |
| TX    | 618      |
| PA    | 485      |
| IL    | 453      |

This shows that assigned girls who were named John happened mostly in CA and NY
~~~~ sql
SELECT year, sum(frequency) AS sum_freq 
FROM names 
WHERE trim(gender) = 'F' AND upper(name) = 'JOHN' 
GROUP BY year 
ORDER BY sum(frequency) DESC
LIMIT 5;
~~~~
| year | sum_freq |
|------|----------|
| 1970 | 254      |
| 1969 | 248      |
| 1968 | 242      |
| 1967 | 240      |
| 1961 | 235      |

This shows that assigned girls who were name John happened mostly in the years 1970 and 1969
6. What were the top 3 most common female names in New York in the year 2000?
~~~~ sql
SELECT  name, frequency ,gender, state, year 
FROM names
WHERE gender = 'F' AND state='NY' AND year=2000
ORDER BY frequency DESC
LIMIT  3;
~~~~
| name     | frequency | gender | state | year |
|----------|-----------|--------|-------|------|
| Emily    | 1719      | F      | NY    | 2000 |
| Samantha | 1422      | F      | NY    | 2000 |
| Ashley   | 1290      | F      | NY    | 2000 |

Emily,Samantha and Ashley
***
### Names Table: Aggregations & Operators
7. How many babies are born each year?
~~~~ sql
SELECT  year, sum(frequency) as num_babies_born FROM names
GROUP BY year;
~~~~
| year | num_babies_born |
|------|-----------------|
| 1951 | 3507395         |
| 1952 | 3616498         |
| 1953 | 3667565         |
| 1954 | 3791860         |
| 1955 | 3822067         |
| 1956 | 3925942         |
| 1957 | 4002301         |
| 1958 | 3933841         |
| 1959 | 3955359         |
| 1960 | 3948285         |
| 1961 | 3930176         |
| 1962 | 3826088         |
| 1963 | 3747900         |
| 1964 | 3674959         |
| 1965 | 3419997         |
| 1966 | 3268121         |
| 1967 | 3184524         |
| 1968 | 3160115         |
| 1969 | 3245440         |
| 1970 | 3359904         |
| 1971 | 3177871         |
| 1972 | 2890435         |
| 1973 | 2759591         |
| 1974 | 2774155         |
| 1975 | 2744746         |
| 1976 | 2754165         |
| 1977 | 2882924         |
| 1978 | 2877596         |
| 1979 | 3019009         |
| 1980 | 3130607         |
| 1981 | 3146074         |
| 1982 | 3192940         |
| 1983 | 3153566         |
| 1984 | 3176691         |
| 1985 | 3246156         |
| 1986 | 3228063         |
| 1987 | 3266349         |
| 1988 | 3341106         |
| 1989 | 3475391         |
| 1990 | 3566753         |
| 1991 | 3502904         |
| 1992 | 3442429         |
| 1993 | 3364179         |
| 1994 | 3307545         |
| 1995 | 3249605         |
| 1996 | 3225359         |
| 1997 | 3193607         |
| 1998 | 3229968         |
| 1999 | 3233728         |
| 2000 | 3297484         |
| 2001 | 3251626         |
| 2002 | 3238625         |
| 2003 | 3289668         |
| 2004 | 3294861         |
| 2005 | 3306386         |
| 2006 | 3388984         |
| 2007 | 3413961         |
| 2008 | 3342040         |
| 2009 | 3234208         |
| 2010 | 3119095         |
| 2011 | 3082465         |
| 2012 | 3078459         |
| 2013 | 3073647         |
| 2014 | 3134043         |
| 2015 | 3124166         |
| 2016 | 3077573         |

8. How many people named "John" were there per state, per year?
~~~~ sql
--Group by both state and year
SELECT  year, state , sum(frequency)  as count_john FROM names
WHERE name='John'
GROUP BY year, state
ORDER BY state;

--Group by State alone
SELECT  state, sum(frequency)  as count_john FROM names
WHERE name='John'
GROUP BY state;

-- Group by Year alone
SELECT  year, sum(frequency) as count_John FROM names
WHERE name='John'
GROUP BY year;
~~~~
9. Write a query that tells you how many different female names there 
were per state, per year.
~~~~ sql
SELECT state, year, count(DISTINCT(name))
FROM names
WHERE gender = 'F'
GROUP BY state,year ;
~~~~
10. How many records were there in the years 2000, 2001, and 2002?
~~~~ sql
SELECT  year, count(*) as records 
FROM names
GROUP BY year
HAVING year in (2000,2001,2002);
~~~~
| year | records |
|------|---------|
| 2000 | 79998   |
| 2001 | 81083   |
| 2002 | 81982   |

11. How many names end with the letter "a" in the table? (Hint: LIKE operator and the % wildcard)
~~~~ sql
SELECT (count(name)) as names_end_with_a FROM names
WHERE upper(name) like '%A'
~~~~
Answer is 926,736
*** 
### Regions Table
12. What are the columns on the region table? (Hint: SELECT * can do the job!)
~~~~ sql
SELECT * FROM regions;
~~~~
state and region are the two columns of regions table.
13. How many different regions are there in the `region` table? (Hint: DISTINCT) Can you find the one that looks like a typo?
~~~~ sql
SELECT DISTINCT(region) FROM regions;
~~~~
| region       |
|--------------|
| South        |
| Pacific      |
| Mountain     |
| New_England  |
| Mid_Atlantic |
| Midwest      |
| New England  |

The last region in the above table looks like a typo- 'New England' instead of New_England
