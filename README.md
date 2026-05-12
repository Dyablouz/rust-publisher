# Rust Publisher

## How much data your publisher program will send to the message broker in one run?

The publisher sends 5 events to the message broker in one run. Each event is a `UserCreatedEventMessage` containing a `user_id` and a `user_name`.

## The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

The URL tells the publisher how to connect to RabbitMQ using AMQP. The first `guest` is the username, the second `guest` is the password, and `localhost:5672` means RabbitMQ is running on the local computer on port `5672`, which is the default AMQP port.

## Running RabbitMQ

![RabbitMQ page](RabbitMQ.png)

## Event Processing

![Console Publisher](Publisher.png)

![Console Subscriber](Subscriber.png)