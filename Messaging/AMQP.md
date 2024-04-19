AMQP (Advanced Message queueing protocol) is a protocol designed for *high-performance* messaging between applications. 

**Basic Components**
- **Producers** 
- **Message Broker** - The server that receives messages from producers and routes them to consumers (intermediary between producers and consumers).
- **Consumers**

**AMQP Model**
- **Exchanges** - These are message routing agents within the message broker. Producers send messages to exchanges, which then route the message to queues based on rules called *bindings*.
- **Queues** - These are buffers that store messages until they are consumed. Each message is stored in a queue until a consumer *retrieves* it.
- **Bindings** - These are rules that exchanges use to route messages to queues. Bindings can be based on message attributes like *routing keys*.
- **Routing keys** -  These are attributes of messages that exchanges use to determine which queues a message should be sent to.

**How messages are sent and received**
1. The producer creates a message and sends it to an exchange. The message includes a routing key, which is used by the exchange to determine where to route the message.
2. The exchange receives the message from the producer and uses the routing key to determine which queues the message should be sent to. This is done based on the bindings that have been set up.
3. The message is stored in one or more queues, depending on the routing rules. The message remains in the queue until a consumer retrieves it.
4. The consumer connects to the message broker and requests messages from the queue. Once the message is successfully processed, the consumer sends an acknowledgement back to the message broker, indicating that the message has been processed and can be removed from the queue.