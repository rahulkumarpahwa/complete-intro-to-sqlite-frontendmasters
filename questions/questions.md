1. What is a key characteristic of SQLite's deployment?
1. SQLite is estimated to exist in approximately a trillion databases, running on devices like iPhones, Android phones, Windows computers, browsers, cars, and various electronic devices with very low resource requirements

2. What is unique about SQLite's operational model compared to other databases?
2. SQLite is not a server-based database, but instead functions more like a library for reading and writing to a file, with no network access, no user management, and designed to work on the same computer as the application using it

3. What licensing model does SQLite use?
3. SQLite is released under a public domain license, which is uncommon, and does not accept outside contributions, with development controlled by a small core team

4. What are some limitations of SQLite in production environments?
4. SQLite is intentionally limited, with a small subset of SQL features, no built-in replication, no consensus mechanisms, single node operation, and may not be suitable for high-scale applications requiring complex data management

5. How does SQLite handle performance?
5. SQLite is designed to be extremely fast, particularly because it operates locally without network overhead, and is optimized to read and write data at high speeds, making it suitable for performance-sensitive environments

6. What is the version number of SQLite discussed?
6. SQLite 3, specifically version 3.46 was mentioned by the instructor

7. What database is being used as the example dataset in this course?
7. Chinook, which is an invoicing system for digital media that includes references to musicians like Led Zeppelin and AC/DC

8. What command can you use in SQLite to list all available tables?
8. .tables

9. How can you exit the SQLite command line interface?
9. You can use either .exit command or press Control+D

10. What does 'transit in memory' mean when running SQLite3 without a database?
10. It creates a temporary, in-memory database session that is deleted when you exit, allowing you to experiment without preserving data.

11. What does the * symbol typically mean when used in a SQL SELECT statement?
11. The * symbol means to retrieve all columns from a table

12. What is the purpose of the WHERE clause in a SQL query?
12. The WHERE clause limits the results to a specific subset of rows that match a given condition

13. What is the difference between single and double quotes in SQL?
13. Single quotes are used for string literals or actual values, while double quotes are used for table-level or column names

14. When writing SQL queries for applications, what is recommended for selecting columns?
14. Be specific about the columns you want to retrieve, rather than using SELECT * to improve code readability and performance

15. How can you view the schema of a table in SQLite?
15. Use the .schema command followed by the table name, such as .schema Artist, to view the table's column structure and constraints

16. What SQL keyword can be used to perform partial string matching?
16. LIKE allows searching for partial string matches using percent signs (%), enabling flexible text searches in database queries

17. How can you use LIKE to find a string anywhere within another string?
17. By placing percent signs on both sides of the search term, like WHERE name LIKE '%orchestra%', which finds the search term anywhere in the text

18. What SQL clauses can be used to implement pagination in a query?
18. LIMIT and OFFSET can be used for basic pagination, such as SELECT * FROM Artists LIMIT 5 OFFSET 10 to retrieve a specific subset of results

19. How can you order query results in SQL?
19. Use ORDER BY followed by a column name, with optional ASC (ascending) or DESC (descending) to specify sort direction, like SELECT * FROM Artist ORDER BY name DESC

20. What comparison operators can be used beyond simple equality in SQL queries?
20. Operators like less than (<), less than or equal to (<=), greater than (>), and greater than or equal to (>=) can be used in WHERE clauses to filter results

21. What is the basic syntax for inserting a new record into a SQLite database?
21. INSERT INTO table_name (column_name) VALUES (value)

22. What happens if you omit the WHERE clause in an UPDATE statement?
22. It will update ALL records in the table with the specified value

23. How can you return the updated or deleted record after a database operation?
23. Use the RETURNING keyword after the UPDATE or DELETE statement, such as UPDATE table SET column = value WHERE condition RETURNING *

24. What is important to remember when inserting values into multiple columns?
24. The order of values must match the order of columns specified in the INSERT statement

25. How does SQLite store data?
25. SQLite stores data in a file (typically with .db extension) using a library that modifies the file, rather than running as a server

26. What are the four primary data types in SQLite?
26. Integers, real (decimals/floats), text, and blob

27. How does SQLite handle type conversion for Boolean values?
27. SQLite converts Boolean values to integers, with true being 1 and false being 0

28. What is a unique characteristic of SQLite's data typing system?
28. SQLite has a dynamically typed system that tries to accommodate different data types, often converting between them without strict constraints

29. What happens when you insert a number into a text field in SQLite?
29. SQLite will convert the number to text, so inserting the number 100 into a text field will result in the text value '100'

30. What is a limitation of altering tables in SQLite compared to other databases?
30. In SQLite, you can only alter one column or table at a time, whereas other databases like Postgres allow multiple column modifications in a single query

31. What is a many-to-many relationship in database design?
31. A relationship where multiple entities in one table can be associated with multiple entities in another table, such as band members belonging to multiple bands or ingredients being used in multiple recipes.

32. What is the purpose of using table aliases in SQL joins?
32. Table aliases make SQL queries more readable and less verbose by allowing shorter reference names for tables, such as using 'a' for album and 'b' for artist instead of typing full table names repeatedly.

33. Why do relational databases use multiple tables instead of storing all information in a single table?
33. Multiple tables help maintain data integrity, make updates easier, and prevent redundancy. For example, if an artist changes their name, only one row needs to be updated instead of updating every track and album row.

34. How do you join multiple tables in SQL?
34. You can join tables using the JOIN keyword and specifying a common identifier between tables, such as 'JOIN Artist ON Album.ArtistId = Artist.ArtistId', which connects related data across different tables.

35. What is a one-to-many relationship in database design?
35. A relationship where one entity in a table can be associated with multiple entities in another table, such as an album containing multiple tracks, or a band having multiple members.

36. What is an INNER JOIN in the context of SQL?
36. An INNER JOIN returns only the results that exist in both tables, similar to the intersection in a Venn diagram. It excludes any records that only exist in one table but not the other.

37. What is the primary difference between a LEFT JOIN and an INNER JOIN?
37. A LEFT JOIN includes all records from the left table and matching records from the right table, even if no match exists. An INNER JOIN only returns records with matches in both tables.

38. What does a RIGHT JOIN do in SQL?
38. A RIGHT JOIN returns all records from the right table and matching records from the left table, including records from the right table that have no match in the left table.

39. What is a FULL OUTER JOIN in SQL?
39. A FULL OUTER JOIN returns all records from both tables, including records that do not have a match in the other table, effectively combining the results of LEFT and RIGHT JOINs.

40. What is a NATURAL JOIN and why might it be considered problematic?
40. A NATURAL JOIN automatically joins tables based on columns with the same name, without specifying join conditions. It can be prone to errors if table schemas change, as it might unexpectedly join on unintended columns.

41. What is a foreign key in a database?
41. A foreign key is a column in a table that references a primary key in another table, creating a relationship between two tables and maintaining referential integrity.

42. What does the ON DELETE NO ACTION constraint do in a foreign key?
42. ON DELETE NO ACTION prevents deleting a record in the primary table if there are related records in the foreign key table, ensuring data integrity by failing the query if dependent records exist.

43. Why does SQLite not respect foreign key constraints by default?
43. SQLite is aggressively backwards compatible and did not want to break older applications that were written when foreign key constraints were not respected, so foreign key enforcement is disabled by default.

44. How do you enable foreign key constraints in SQLite?
44. You must execute the PRAGMA foreign_keys=on command for each database connection to enable foreign key constraint enforcement.

45. What are the alternative ON DELETE behaviors for foreign keys?
45. Alternative ON DELETE behaviors include CASCADE (automatically delete related records), SET NULL (set foreign key to null when primary record is deleted), and SET DEFAULT (set foreign key to a default value when primary record is deleted).

46. What SQL aggregation function is used to count the number of rows in a database?
46. COUNT, which can be used with variations like COUNT DISTINCT to count unique values

47. What is the purpose of the SQL DISTINCT keyword when used with COUNT?
47. DISTINCT collapses the result set to show only unique values, preventing duplicate entries from being counted multiple times

48. In SQL aggregation queries, what clause is used to filter results after grouping and aggregation?
48. HAVING clause is used to filter results based on aggregated values, unlike WHERE which filters before aggregation

49. What other aggregation functions exist besides COUNT in SQL?
49. Other aggregation functions include MAX (maximum value), MIN (minimum value), which can be used to find extreme values in a dataset

50. When performing SQL aggregation queries with GROUP BY, what key rule must be followed about filtering?
50. You cannot reference aggregated columns in the WHERE clause; aggregation-based filtering must use the HAVING clause