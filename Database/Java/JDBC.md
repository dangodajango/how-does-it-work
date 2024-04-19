**Java Database Connectivity (JDBC)** is a Java API that enables Java applications to interact with databases. It provides standard interface for accessing relational databases, allowing developers to execute SQL queries and updates, and retrieve results in a database-independent manner.

***
**Core components:**
- **JDBC Driver** - A driver is a software component that enables a Java application to interact with a specific database. Each database has its own JDBC driver.
- **JDBC API** - The api provides the classes and interfaces needed to connect to a database, execute SQL statements, handle the results.

***
**Core interfaces/classes:**
- **DriverManager** - Provides methods to establish a connection with the database. It manages a list of database drivers and uses them to establish connections.
- **Connection** - Represents a connection with a database. It is used to create *Statement* and *PreparedStatement* objects, and control transactions.
- **Statement** - Used for executing simple SQL queries and updates and retrieve results.
- **PreparedStatement** - Extends *Statement* and is used for executing parameterised SQL queries and updates and retrieve results.
- **CallableStatement** - Used for executing stored procedures and functions. It provides methods to register output parameters and retrieve the result of the procedure or function.
- **ResultSet** - Represents the result set of a query. It provides methods to navigate through the rows of the result set and retrieve column values.
- **DatabaseMetaData** - Provides methods to get information about the database, such as the database product name, version, and names of the tables in the database.

***
**How to handle transactions:**
1. To start a transaction, you typically disable the auto-commit mode on the *Connection* object. By default, JDBC connections are in auto-commit mode, which means that each SQL statement is treated as a separate transaction and is automatically committed right after it's executed.
2. Since the auto-commit mode is off, all the executed SQL statements will be part of the transaction until the transaction is committed.
3. When we have executed the queries that we wanted using *Statement* or *PreparedStatement* we need to commit the transaction, meaning to make all changes permanent in the database.
4. If something goes wrong during the transaction, or if you decide that the changes should not be made permanent, you can roll back the transaction. This undoes all changes made during the transaction and leaves the database in its original state, before the transaction began.

***
JDBC does not include built-in support for connection pooling. To implement it we can use third-party libraries, some popular connection pool libraries include:
- **HikariCP** 
- **C3PO**
- **Apache Commons DBCP**

These libraries provide a *DataSource* implementation that manages a pool of database connections. You configure the DataSource with details of your database and the pooling parameters, such as the maximum number of connections in the pool. Your application then uses this *DataSource* to obtain connections, which are automatically managed by the pool.

So when using the libraries, you obtain database connections through a *DataSource* object rather than directly using *DriverManager*.  The *DataSource* internally uses a JDBC driver to establish connections to the database.