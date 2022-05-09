# Football Matches - Tasks

Each of the questions/tasks below can be answered using a `SELECT` query. When you find a solution copy it into the code block under the question before pushing your solution to GitHub.

1) Find all the matches from 2017.

```sql
<!-- Copy solution here --> SELECT * FROM matches WHERE season = 2017;


```

2) Find all the matches featuring Barcelona.

```sql
<!-- Copy solution here --> SELECT * FROM matches WHERE 'Barcelona' IN (hometeam,awayteam);


```

3) What are the names of the Scottish divisions included?

```sql
<!-- Copy solution here --> SELECT name FROM divisions WHERE country = 'Scotland';



```

4) Find the division code for the Bundesliga. Use that code to find out how many matches Freiburg have played in the Bundesliga since the data started being collected.

```sql
<!-- Copy solution here --> SELECT DISTINCT code FROM divisions WHERE name = 'Bundesliga'; SELECT COUNT (*) FROM matches WHERE division_code='D1' AND 'Freiburg' IN (hometeam,awayteam);


```

5) Find the unique names of the teams which include the word "City" in their name (as entered in the database)

```sql
<!-- Copy solution here --> SELECT hometeam FROM matches WHERE LOWER(hometeam) LIKE '%city%' UNION SELECT awayteam FROM matches WHERE LOWER(awayteam) LIKE '%city%';


```

6) How many different teams have played in matches recorded in a French division?

```sql
<!-- Copy solution here --> SELECT DISTINCT code FROM divisions WHERE country = 'France'; SELECT COUNT(DISTINCT hometeam) FROM matches WHERE division_code = 'F1' OR division_code = 'F2';


```

7) Have Huddersfield played Swansea in the period covered?

```sql
<!-- Copy solution here --> SELECT COUNT(*) FROM matches WHERE (hometeam,awayteam) = ('Huddersfield','Swansea') OR (hometeam,awayteam) = ('Swansea','Huddersfield'); yes


```

8) How many draws were there in the Eredivisie between 2010 and 2015?

```sql
<!-- Copy solution here --> SELECT DISTINCT code FROM divisions WHERE name = 'Eredivisie'; SELECT COUNT(*) FROM matches WHERE division_code = 'N1' AND ftr = 'D';


```

9) Select the matches played in the Premier League in order of total goals scored from highest to lowest. Where there is a tie the match with more home goals should come first.

```sql
<!-- Copy solution here --> SELECT DISTINCT code FROM divisions WHERE name = 'Premier League'; SELECT * FROM matches WHERE division_code = 'E0'; SELECT * FROM matches WHERE division_code = 'E0'  ORDER BY (ftag+fthg) DESC ,fthg DESC;


```

10) In which division and which season were the most goals scored?

```sql
<!-- Copy solution here --> SELECT (division_code,season),(fthg+ftag) FROM matches WHERE (fthg+ftag) = (SELECT MAX(fthg+ftag) FROM matches);


```

### Useful Resources

- [Filtering results](https://www.w3schools.com/sql/sql_where.asp)
- [Ordering results](https://www.w3schools.com/sql/sql_orderby.asp)
- [Grouping results](https://www.w3schools.com/sql/sql_groupby.asp)