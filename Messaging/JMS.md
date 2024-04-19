Java Message Service (JMS) is a Java API that allows applications to create, send, receive and read messages in a loosely coupled and asynchronous way.

#### Core Classes and Interfaces

**ConnectionFactory**
- Used to establish connections to the message broker.

**Connection**
- Created from *ConnectionFactory*, it's used to create sessions and start/stop connections.

**Session**
- A single-threaded context for producing and consuming messages. You can create multiple sessions from a single connection, and each session can have its own producers and consumers. 

**Destination**
- Represents the target for sending messages, can be a queue of a topic.

**MessageProducer**
- it is used to send messages to a destination. The destination can be a queue or a topic, if it's a topic, the message is published to all subscribers of the topic.

**MessageConsumer**
- It is used to receive messages from a destination. The receive can be either synchronous, by invoking the receive() method, which blocks until a message is available, or it can be asynchronous - the consumer set up  a listener that is notified when a message arrives.
- **Polling** - The application actively checks for new messages at regular intervals. This can be less efficient and more resource-intensive, especially if the application needs to perform other tasks concurrently. It is performed by using *receive()* method.
- **Listening** - The JMS provider automatically notifies the application when a message arrives, allowing for more efficient and scalable message processing. It is done by registering a listener.

**Message**
- Represents a message that can be sent or received, it can be a text message, an object message, a map message, a stream message, or a bytes message, depending on the type of data being sent.

***
Each message broker that supports JMS API, implements it to provide a standard way for Java applications to send and receive messages.