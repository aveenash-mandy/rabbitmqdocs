# rabbitmqdocs

# Queue
Queue act as a data accumulation buffer for consumers. A queue is an ordered collection of messages. Messages are enqueued and dequeued (delivered to consumers) in a FIFO style. 

## Queue Properties

* Name
* Durable
* Exclusive (used by only one connection and the queue will be deleted when that connection closes)

## Queue Types

* Quorum -> Replicated, data safety and consistency oriented queue
* Classic -> Classic queues historically supported replication but this feature was removed for RabbitMQ 4.x

Any client connection can use any queue, including non-replicated (single replica) queues, regardless of the node the queue replica is hosted on or the node the client is connected to.

For example, in a cluster with nodes A, B and C, a client connected to node A can consume from a queue Q hosted on B, while a client connected to node C can publish in a way that routes messages to queue Q.

## Protocols
* AMQP 0-9-1 and MQTT

# Message States
Enqueued messages therefore can be in one of two states:

* Ready for delivery
* Delivered but not yet acknowledged by consumer

Message breakdown by state can be found in the management UI.


# Quorum Queues:
The RabbitMQ quorum queue is a modern queue type which implements a durable, replicated queue based on the Raft consensus algorithm and should be considered the default choice when needing a replicated, highly available queue.

Quorum queues are designed for excellent data safety as well as reliable and fast leader election properties to ensure high availability even during upgrades or other turbulence.
