MQTT (Message Queuing Telemetry Transport) is lightweight messaging protocol designed for constrained devices, it's particularly well-suited for Internet of Things applications where bandwidth is limited and devices may be intermittently connected. 

**Basic Components**
- **Client** - Either publisher (sender) or subscriber (receiver).
- **Broker** - A server that receives messages from clients. The broker is responsible for managing subscriptions and delivering messages to the appropriate clients.

**MQTT Model**
- **Topics** - These are channels through which messages are published and received. Topics are hierarchical, allowing for flexible message routing.
- Quality of Service (QoS) - MQTT supports three levels of QoS for message delivery.
	- QoS 0 - At most once delivery. The message is delivered at most once, or it may not be delivered at all.
	- QoS 1 - At least once delivery. The message is guaranteed to be delivered at least once, but it may be delivered more than once.
	- QoS 2 - Exactly once delivery. The message is guaranteed to be delivered once.
	- **Retain** - A flag that, when set, causes the broker to retain the last message published on a topic. When a client subscribes to a topic, it receives the retained message if one exists.

**How messages are sent and received**
1. The client establishes a connection with a broker. This connection is maintained until the client disconnects or the connection is lost.
2. The client subscribes to one or more topics. When subscribing, the client can specify the QoS level for the subscription.
3. The client publishes a message to a topic. The message includes the topic, the payload (the actual message data), and optionally, the QoS level and the retain flag.
4. The broker receives the message from the client and routes it to all clients that are subscribed to the topic. The routing is based on the topic hierarchy and the QoS level specified by the publisher.
5. The subscribed client receive the message from the broker. If the QoS level is 1 or 2, the client sends an acknowledgment back to the broker to confirm receipt of the message.