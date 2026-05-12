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
## Monitoring Chart Based on Publisher
When I run the publisher, it sends events to RabbitMQ. The RabbitMQ message rates chart shows activity because messages are published by the publisher and then consumed by the subscriber.
![RabbitMQ Chart](images/rabbitmq-chart.png)

# Bonus
## Bonus: Message Broker Monitoring with Multiple Subscribers

In this bonus experiment, I ran multiple subscribers at the same time and then executed the publisher several times. Each time the publisher is run, it sends five `UserCreatedEventMessage` events to the RabbitMQ message broker.

Because there are multiple subscribers connected to the same broker, RabbitMQ can distribute the messages to more than one consumer. This can be observed from the RabbitMQ dashboard, where the number of consumers increases and the message rate graph changes when the publisher sends messages.

![RabbitMQ Multiple Subscribers](images/rabbitmq-multiple-subscribers.png)

After running the publisher several times, the RabbitMQ message rate graph shows publish and deliver activity. This indicates that the publisher successfully sent messages to the broker, and the messages were then delivered to the active subscribers.

![RabbitMQ Message Rate Bonus](images/rabbitmq-message-rate-bonus.png)
