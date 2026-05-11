# Understanding publisher and message broker
## a. How much data your publisher program will send to the message broker in one run?
In one run, the publisher program sends 5 events to the message broker. Each event contains a user_id and a user_name.
## b. The URL amqp://guest:guest@localhost:5672 is the same as in the subscriber program, what does it mean?
It means that both the publisher and the subscriber connect to the same RabbitMQ message broker. The publisher sends events to this broker, and the subscriber consumes events from the same broker.
## Running RabbitMQ as Message Broker
RabbitMQ is running through Docker. It listens on port 5672 for AMQP connection and provides the management interface on port 15672.
![RabbitMQ Running](images/rabbitmq-running.png)
## RabbitMQ Browser with One Connection
After running the subscriber, RabbitMQ shows one active connection and one consumer. This means that the subscriber is successfully connected to the message broker and is ready to consume messages from the queue.
![RabbitMQ One Connection](images/rabbitmq-one-connection.png)
## Sending and Processing Event
When I run cargo run in the publisher directory, the publisher sends 5 events to the message broker. These events are then consumed and processed by the subscriber.
![Sending and Processing Event](images/sending-processing-event.png)