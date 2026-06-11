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
