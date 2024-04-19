### Drivers:

**Driver** is software that enables communication between 2 systems or components that do not understand each other. Drivers are used to translate commands and data between a high-level application and a low-level system. 

In the context of databases, a **driver** is a software component that allows an application to interact with a database management system (DBMS) by translating the application's database commands into a format that the DBMS can understand and execute.

That's why there are different drivers for the different DBMS like Oracle, MySQL, PostgreSQL, etc. Each database system has it's own unique architecture, data formats, and communication protocols. To enable an application to interact with these databases, we need specific drivers that are tailored to each database system.

### Connections:

A connection is communication link between a client application a database server. The link allows client to send requests to the database server and receive responses, enabling the client to perform operations such as querying, updating, deleting, inserting data.

***
**How it works:**
1. **Client Request**
	- The client application creates a socket, which is an endpoint for sending and receiving data across a network. The socket is created using the socket API provided by the operating system.
	- The client sends a connection request to the database server. This request includes the server's IP address and port number, as well as any necessary authentication information.
2.  **Server Listening**
	- The database server has a socket that listens for incoming connection requests. The socket is bound to a specific IP address and port number.
	- When the server receives a connection request. it accepts the connection, creating a new socket for the connection. The new socket is used for the actual data exchange between the client and server.
3. **Protocol Handshake**
	- The client and server perform a protocol handshake to agree on the communication parameters. This includes the protocol version, security settings, and any other relevant parameters.
	- Once the handshake is complete, both the client and server have agreed on the terms of the connection, and the connection is considered established.
4. **Data Transmission**
	- With the connection established, the client and server can now send and receive data. This data is transmitted over the socket connection. 
	- If the connection is secured (using SSL/TLS), the data is encrypted before being sent and decrypted upon receipt. This ensures that the data remains confidential and secure.
5. **Connection Termination**
	- When the client or server is done with the connection, it sends a request to close the connection. This involves sending a specific message or signal over the socket.
	- Both client and server close their respective sockets, terminating the connection.

***
Establishing a database connection is considered a heavy operation due to several factors that contribute to the overhead involved in the process.

1. **Network Overhead**
	- The initial TCP/IP handshake involves multiple round-trip messages between the client and server to establish a connection. The process can introduce significant latency, especially over long distances or through networks with high latency.
	- If the connection is secured, additional handshakes are required to negotiate encryption parameters and establish a secure channel.
2. **Resource Allocation**
	- Establishing a connection requires the server to allocate resources for the connection, such as memory for session data, file descriptors, and possibly threads or processes to handle the connection.
	- Similarly, the client must allocate resources to manage the connection, including memory for the connection state, and possibly threads or processes to handle the connection.
3. **Authentication and Authorisation**
	- The process of authenticating the client credentials with the server can be computationally intensive, especially if it involves complex authentication mechanism or if the server needs to verify credentials against a secure storage system.
	- After authentication, the server may perform additional checks to determine what resources the client is authorised to access.
4. **Session Initialisation**
	- The handshake process may involve the exchange of session parameters, such as timeout values, window sizes, and other settings that affect the performance and reliability of the connection.

### Connection pooling:

We know that creating a new connection every time we want to send and receive date from the database may cause performance issues. To deal with that we can use a technique called **connection pooling**.

**Connection pooling** - Creating a collection of pre-established connections to a database that are kept open and ready for use by client applications. The primary purpose of it is to reduce the overhead and improve the efficiency of database operations by reusing existing connections instead of creating a new connection for each database request.

***
**How it works:**
1. When the connection pool is initialised, a set number of connections to the database are established. These connections are kept open and idle, ready to be used.
2. When a client application needs to interact with the database, it requests a connection from the pool. Instead of establishing a new connection the application borrows an existing connection form the pool.
3. The client uses the borrowed connection to execute database operations, such as querying data, inserting records, or updating data.
4. After the client application is done with the database operations, it returns the connection to the pool. The connection is not closed but is kept open and idle, ready for reuse.


### Transactions:

Imagine you are cooking a meal that involves several steps. You start by chopping vegetables, then you sauté them in oil, add some spices, and finally you mix everything together to make a dish. Each of these steps is like an operation in a database.

In this cooking scenario, a "transaction" is the whole process of making the dish. It's a series of actions that you want to do together. If can chop the vegetables, sauté them, add the spices, and mix everything without any mistake, you have a delicious meal. But if something goes wrong at any step (like if you burn the vegetables or forget to add a crucial spice), you have to undo all the steps you've taken and start over.

In databases, a "transaction" is like this cooking process. It's a group of actions (like adding a new record, updating a record, or deleting a record) that you want to do together. If all the actions in the transaction are successful, the changes are made permanent in the database. But if something goes wrong, all the changes made during the transaction are undone, and the database stays the same as it was before the transaction started.
### Sessions:

A session in a database is essentially a period during which a client interacts with the database. It's a way for the client to communicate with the database, asking it to perform operations such as querying data, inserting new records, updating existing records, or deleting records.

Once the connection is established, a session is created. This session represents the ongoing interaction between the client and the database server. The session is used to manage the state of the interaction, including any active transactions, locks, and other session-specific data.


