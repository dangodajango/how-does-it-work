
#### How does it work?

**Data Structures**
- At the core of a message queue system are the **queues** themselves. These are data structures that hold messages. The most common type of queue used in message queues is the **FIFO (First-In-First-Out)** queue, where messages are added to to the end of the queue, and removed from the front. This ensures that messages are processed in the order they arrive.
- Some message queues use **buffers** to temporarily store messages before they were written to the queue. This can help manage memory usage and improve performance by reducing the need for immediate disk writes.

***
**Protocols**
- **[[AMQP]] (Advanced Message Queuing Protocol)** 
- [[MQTT]]
- [[STOMP]]

***
**Operations**
- **Enqueue** - The operation of adding a message to the queue. This involves serialising the message into format that can be stored and transmitted, and then appending it to the queue.
- **Dequeue** - The operation of removing a message from the queue. This involves retrieving the message from the front of the queue and deserialising it back into a usable format.
- **Acknowledgment** - After a message is successfully processed, the consumer sends an acknowledgment back to the message queue. This tells the queue that the message has ben processed and can be removed from the queue.
- **Persistence** - Some message queues support persistence, where messages are stored on disk. This ensures that messages are not lost if the system crashes or restarts.