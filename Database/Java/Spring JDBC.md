Spring JDBC is a part of the Spring Framework and provides a simple approach to working with [[JDBC]] api. It abstracts away much of the boilerplate code that is typically involved in using JDBC directly, making it easier to perform database operations in Java applications. 

Spring JDBC provides a template-based approach to database access, which simplifies the process of executing SQL queries, handling transactions, and managing resources.

***
**Core interfaces / classes:**
- **JdbcTemplate** 
	- Abstracts - Connection management, statement creation, execution, and resource cleanup. It handles the creation and release of resources like connections, statements, and result sets, which are essential tasks in JDBC but can be error-prone and cumbersome to manage manually.
	- Logic - It simplifies the execution of SQL queries by providing methods to run queries, update statements, and call stored procedures. It also catches JDBC exceptions and translates them into Spring's Data Access Exception hierarchy, making error handling more consistent and informative.
- **NamedParameterJdbcTemplate**
	- Abstracts - The complexity of handling named parameters in SQL queries.
	- Logic - It extends *JdbcTemplate* to support the use of named parameters in SQL queries making it easier to write and read SQL statements. This is particularly useful for complex queries with multiple parameters, as it eliminates the need to manually manage parameters indices and types.
- **SimpleJdbcInsert and SimpleJdbcCall**
	- Abstracts - The boilerplate code associated with performing insert and call operations.
	- Logic - *SimpleJdbcInsert* simplifies the insertion of a single row into a database table, handling the creation and execution of the insert statement. *SimpleJdbcCall* simplifies the execution of stored procedures and functions, reducing the amount of code needed to call these database operations.
- **DataSource**
	- Abstracts - The management of database connections.
	- Logic - While not directly implemented in Spring, *DataSource* is a crucial component that Spring JDBC uses to obtain database connections. It abstracts the process of obtaining, managing, and releasing database connections, which is fundamental aspect of JDBC but can be complex and error-prone to manage manually.

