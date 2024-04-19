
- **Producer-Consumer Model** - In a distributed messaging system, the communication follows a producer-consumer model. The producer sends messages to the message queue, and the consumer retrieves and processes these messages. This model allows for asynchronous communication, where the producer does not wait for an immediate response from the consumer.
- **Decoupling** - Message queues decouple the sender and receiver, enabling them to operate independently. This decoupling is crucial for building scalable and resilient systems, as it allows components to operate asynchronously and handle varying loads without direct interaction.

***
**Fundamentals of Message Queues and Messaging Systems**
- **Message Queue** - A message queue is a component that accepts messages from producers, stores them in a buffer, and allows consumers to process these messages in order they arrive. 
- **Message Passing** - Message passing in distributed systems involves the exchange of messages between nodes to coordinate actions, exchange data, and propagate information.

### Message Brokers:

Message brokers implement the infrastructure for message queues and messaging in general. They provide the necessary mechanisms for managing, routing, and delivering messages between producers and consumers.

***
Some message brokers support **Topic-based** messaging, which is a pattern, where messages are categorised into topics, and consumers subscribe to one or more topics to receive messages. This approach enables *publish-subscribe (pub-sub)* model, where producers (publishers) send messages to topics, and consumers (subscribers) receive messages from topics they are interested in.

***
Most popular message brokers:
- **IBM MQ**
- **Active/Artemis MQ**
- **RabbitMQ**