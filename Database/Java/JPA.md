**Java Persistence API**, is a specification that provides a standardised way to manage relational data in Java applications. 
JPA allows developers to map Java objects to database tables and vice versa, enabling the persistence of Java objects in a database.

***
**Key features of JPA:**
- **Object-Relational Mapping (ORM)** - JPA provides a way to map Java objects to database tables and columns. This means that developers can work with Java objects in their code, and JPA takes care of translating these objects into SQL queries to interact with the database. This abstraction simplifies the development process and makes the code more readable and maintainable.
- **Persistence Layer** - JPA acts as a persistence layer between the application and the database. It provides a set of APIs and annotations that developers can use to define how their Java objects should be persisted in the database. This includes defining relationships between objects (one-to-one, one-to-many, many-to-many), cascading operations, and more.
- **CRUD Operations** - JPA simplifies the process of performing Create, Read, Update, Delete (CRUD) operations on the database.
- **Transactions** - JPA supports transaction management, allowing developers to group multiple operations into a single transaction.
- **Query Language** - JPA provides a query language called *JPQL (Java Persistence Query Language*, which is similar to SQL but operates on Java objects rather then database tables. This allows developers to write queries in more object-oriented way.
- **Vendor Independence** - JPA is designed to be vendor-independent, meaning that the same JPA code can be used with different database systems. This is achieved through the use of JPA providers([[Hibernate]], EclipseLink, OpenJPA), which implement the JPA specification and provide the actual database access code.

***
**Core Interfaces/classes:**
- **EntityManager** - The primary interface for interacting with the persistence context - the set of all entity instances that are being managed (entity is a Java class that is mapped to a database table,  entities are the primary objects that JPA manages and persists to a relational database). It is used to create, read, update, and delete entities, as well as to execute queries. The *EntityManager* is responsible for managing the lifecycle of entities and for managing transactions.
- **Query** - Represents a database query. It is used to execute queries against the database and to retrieve results. The *Query* interface supports both JPQL and native SQL queries.
- **TypedQuery** - Sub-interface of *Query* that is used for queries that return a specific type of result. It provides a type-safe query execution, allowing developers to specify the type of the result elements.