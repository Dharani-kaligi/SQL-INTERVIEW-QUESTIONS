# SQL-INTERVIEW-QUESTIONS
SQL Interview questions

# Order of execution in sql 
FROM	1	The query begins with the FROM clause, where the database identifies the tables involved and accesses the necessary data.
WHERE	2	The database applies the conditions specified in the WHERE clause to filter the data retrieved from the tables in the FROM clause.
GROUP BY	3	If a GROUP BY clause is present, the data is grouped based on the specified columns, and aggregation functions (such as SUM(), AVG(), COUNT()) are applied to each group.
HAVING	4	The HAVING clause filters the aggregated data based on specified conditions.
SELECT	5	The SELECT clause defines the columns to be included in the final result set.
ORDER BY	6	If an ORDER BY clause is used, the result set is sorted according to the specified columns.
LIMIT/OFFSET	7	If LIMIT or OFFSET clause is present, the result set is restricted to the specified number of rows and optionally offset by a certain number of rows.


# What is the difference between S Q L and my S Q L?
SQL (Structured Query Language) is a language used to manage and manipulate relational databases. SQL is a standardized language
MYSQL is a relational database management system (RDBMS) that uses SQL to interact with databases.MySQL is a specific implementation of that language.
MySQL allows you to store, retrieve, and manage data in databases.

# What are the different subsets of sql?

Data definition language DDL commands- It allows you to perform various operations on the database such as  **create alter truncate drop rename**(DACT)
Data manipulation language dml commands - It allows you to access and manipulate the data such as **select update insert delete**(USID)
Data control languages D C L It allows you to control access to the database- **Grant, revoke**
Transaction control language It is used to manage the transactions ensuring that the changes made by DML (Data Manipulation Language) commands are handled reliably and consistently- **Commit, rollback, savepoint, release savepoint, set transaction\**

# what is DBMS what are its different types?

D B M S is a database management system it is actually a software that is designed to manage the databases There are two types of Dbms
 There are two types of Dbms
**Relational database management system:** In this relational database management system the data is stored in the form of tables like columns and rows there is a relation between them rows as records columns as attributes It has structured data it uses sql language, ACID Properties.it has schema
**non relational database management system:** Non relational database management system is where the data is told in the form of key value pair json files that is unstructured data.schema lesss

# what is rdbms and what is difference between rdbms and dbms
Rdbms the relational database management system which stores the data in the form of table which has columns and rows as records and attributes. It stores the data in a structured way it has schema.The relationship between different tables in an RDBMS is established using primary keys and foreign keys.

Whereas DBMS is a database management system it is a software that is used to manage and manipulate the databases.

1. Explain order of execution of SQL.
2. What is difference between where and having?
3. What is the use of group by?
4. Explain all types of joins in SQL?
5. What are triggers in SQL?
6. What is stored procedure in SQL
7. Explain all types of window functions?
(Mainly rank, row_num, dense_rank, lead & lag)
8. What is the difference between DROP vs DELETE vs TRUNCATE?
9. What is difference between DML, DDL and DCL?
10. Which is faster between CTE and Subquery?
11. What are constraints and types of Constraints?
## 12. What is normalization?
13. Difference between Group By and Where Clause?
## 14. Explain View concepts ?
15. What are different types of constraints?
16. Difference between char and Varchar?
17. What is an index? Explain its different types.
18. Write an SQL query to find the names of employees starting with ‘A’. 
19. How many types of clauses in SQL?
26. Difference between UNION and UNION ALL in SQL?
27. What are the various types of relationships in SQL?
28. Difference between Primary Key and Foreign Key?
29. What is the difference between where and having?
## 30. Find the second highest salary of an employee?
 SELECT salary, id
FROM table_name
ORDER BY salary DESC
OFFSET 1 ROWS FETCH NEXT 1 ROW ONLY;

## 32. Difference between Function and Store procedure ?
## 33. How would you optimize a slow SQL query?
34. Difference between INNER JOIN and OUTER JOIN?
35. How do you handle duplicate rows in a SQL query?
36. Write a SQL query to find the top 3 departments with the highest average salary.
37. Write a SQL query to find the employees who have the same name and work in the same department.
38. Write a SQL query to find the departments with no employees.
## 39. How do you use indexing to improve SQL query performance?
## 40. Write a SQL query to find the employees who have worked for more than 5 years.


select * from 
[dbo].[employ]
where datediff(year,hire_date, getdate())>10

41. What is the difference between SUBQUERY and JOIN?
42. Write a SQL query to find the top 2 products with the highest sales.
## 43. How do you use stored procedures to improve SQL query performance?
## 44. Write a SQL query to find the customers who have placed an order but have not made a payment.
45. Write a SQL query to find the employees who work in the same department as their manager.
## 46. How do you use window functions to solve complex queries?
## 47. Write a SQL query to find the top 3 products with the highest average price.
## 48. Write a SQL query to find the employees who have not taken any leave in the last 6 months.
## 49. Write down various types of relationships in SQL?
## 50. What is the difference between Cluster and Non-Cluster Index?
51. Why do we use Commit and Rollback commands?
52. What are indexes in SQL?
53. What are aggregate functions? Can you name a few?

    ## calclulate no of iteams in a string?

select id, [values],
case 
    when [values] is null or [values] = '' then 0 
    else (LEN([values]) - len(replace([values], ',', '')) + 1) 
end as item_count
from  [dbo].[your_table]


## query to get to know the 3 consecutive empty seats in movie theatre

with cte as 
(
select * 
lag(is_empty, 1)over(order by sear_no) as previous_1,
lag(is_empty, 2) over(order by seat_no) as previous_2,
lead(is_empty, 1)over(order by seat_no) as next_1,
lead(is_empty, 2) over(order by seat_no) as next _2
from table
)
select * from cte 
where (is_empty = 'Y' and previous_1 = 'y' and previous_2 = 'y') or
      (is_empty = 'Y' and previous_1 = 'y' and next_1 = 'y') or
	  (is_empty =' Y' and next_1 = 'y' and next_2 = 'y')


## Self recursive / self join problem

select * from employees

SELECT e.e_name as Employee_name, m.e_name as Manager_name
from employees e
join employees m
on e.m_id = m.e_id

























