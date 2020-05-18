# SQL Whiteboarding Session

# 1.
One table: salaries (id, league, salary)  

Query to return the number of players in League L1.

# 2.
One table: muppets (name, show)

Query to return the unique values of show.
# 3.
One table: tweets (id, num_tweets)

Query to return the ids of the top ten people in terms of number of tweets.
# 4.
Two tables: players (id, name, team) and salaries (player_id, league, salary)
 
Query to return a list of names with salaries, even if salary information is missing.
# 5.
Two tables: scientists (id, github_pg) and employers (scientist_id, supervisor)   

Suppose no missing data  

Query to return the IDs of all scientists who have both a GitHub page and a supervisor  
# 6.
Same as #5, but now there may be missing data.

# 7.
Write a query to return all duplicate records from a table.
# 8.
One table: more_tweets (id, date, first_line)  

Query to return total tweets by tweeter    
# 9.
You have two tables: authors (author_name, book_name) and books (title, sold_copies)  

The relationship between authors and books is one-many

Query to return the top 3 authors who sold the most books

# 10.
There are two tables: employees (department_name, employee_id, employee_name) and salaries (salary, employee_id, employee_name)

Query to return every department where the average salary per employee is lower than $500.

# 11.
There’s one table: event_log (user_id, event_date_time), recording git commits from users.  

Query to return the number of users who made more than 1000 but less than 2000 commits. 

(Warning: The most natural way of doing this is with a subquery!).   
