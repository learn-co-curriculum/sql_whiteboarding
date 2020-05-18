# 1.
One table: salaries (id, league, salary)  
Query to return the number of players in League L1.

#__SOLUTION__
```SQL
SELECT COUNT(*)
FROM salaries
WHERE league = ‘L1’;
```

# 2.
One table: muppets (name, show)
Query to return the unique values of show.

#__SOLUTION__
```SQL
SELECT DISTINCT show
FROM muppets;
```

# 3.
One table: tweets (id, num_tweets)
Query to return the ids of the top ten people in terms of number of tweets.

#__SOLUTION__
```SQL
SELECT id
FROM tweets
ORDER BY num_tweets DESC
LIMIT 10; (MySQL)
```

# 4.
Two tables: players (id, name, team) and salaries (player_id, league, salary)  
Query to return a list of names with salaries, even if salary information is missing.

#__SOLUTION__  
```SQL
SELECT p.name, s.salary
FROM players p
LEFT JOIN salaries s
ON p.id = s.player_id;
```
# 5.
Two tables: scientists (id, github_pg) and employers (scientist_id, supervisor)
Suppose no missing data.
Query to return the IDs of all scientists who have both a GitHub page and a supervisor.

#__SOLUTION__
```SQL
SELECT s.id
FROM scientists s
INNER JOIN employers e
ON s.id = e.scientist_id
```
# 6.
Same as #5, but now there may be missing data.

#__SOLUTION__
```SQL
SELECT s.id
FROM scientists s
INNER JOIN employers e
ON s.id = e.scientist_id
WHERE s.github_pg IS NOT NULL
AND e.supervisor IS NOT NULL
```
# 7.
Write a query to return all duplicate records from a table.

#__SOLUTION__
```SQL
SELECT COUNT(*)
FROM <table>
GROUP BY col1, … , coln
HAVING COUNT(*) > 1;]
```
# 8.
One table: more_tweets (id, date, first_line)   
Query to return total tweets by tweeter    

#__SOLUTION__
```SQL
SELECT id, COUNT(first_line)
FROM more_tweets
GROUP BY id;
```
# 9.
You have two tables: authors (author_name, book_name) and books (title, sold_copies).  
The relationship between authors and books is one-many.
Query to return the top 3 authors who sold the most books.

#__SOLUTION__
```SQL
SELECT a.author_name, SUM(b.sold_copies)
FROM authors a
JOIN  books b
ON a.book_name = b.title
GROUP BY a.author_name
ORDER  BY SUM(sold_copies) DESC
LIMIT 3;
```
# 10.
There are two tables: employees (department_name, employee_id, employee_name) and salaries (salary, employee_id, employee_name). 

Query to return every department where the average salary per employee is lower than $500.

#__SOLUTION__
```SQL
SELECT e.department_name, AVG(s.salary)
FROM employees e
JOIN salaries s
ON e.employee_id  = s.employee_id
GROUP BY e.department_name
HAVING AVG(s.salary) < 500;
```

# 11.
There’s one table: event_log (user_id, event_date_time), recording git commits from users.  

Query to return the number of users who made more than 1000 but less than 2000 commits. 

(Warning: The most natural way of doing this is with a subquery!).   

#__SOLUTION__
```SQL
SELECT COUNT(*) FROM
	(SELECT user_id, COUNT(event_date_time) AS image_per_user
	FROM event_log
	GROUP BY user_id)
AS image_per_user
WHERE image_per_user <  2000
AND image_per_user > 1000;]
```