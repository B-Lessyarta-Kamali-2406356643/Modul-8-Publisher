# Understanding publisher and message broker
## a. How much data your publisher program will send to the message broker in one run?
In one run, the publisher program sends 5 events to the message broker. Each event contains a user_id and a user_name.
## b. The URL amqp://guest:guest@localhost:5672 is the same as in the subscriber program, what does it mean?
It means that both the publisher and the subscriber connect to the same RabbitMQ message broker. The publisher sends events to this broker, and the subscriber consumes events from the same broker.