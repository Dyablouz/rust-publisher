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

When I run cargo run for subscriber, the subscriber starts and connects to RabbitMQ at amqp://guest:guest@localhost:5672. It then listens to the user_created queue and waits for incoming messages.

When I run cargo run for publisher, the publisher connects to the same RabbitMQ broker and sends 5 UserCreatedEventMessage events to the user_created queue. Each event contains a user_id and a user_name.

After the publisher sends those events, the subscriber console prints the received messages. This shows that the messages were successfully sent to RabbitMQ by the publisher, then consumed and processed by the subscriber.

## Monitoring Chart Based on Publisher

The spike on the RabbitMQ message rate chart appears when the publisher is run because the publisher sends several messages to the broker in a short time. In this program, one "cargo run" execution sends 5 events to the user_created queue. RabbitMQ records that sudden message activity as an increase in the publish and delivery rate, so the chart briefly rises and then returns to zero after the messages are consumed by the subscriber.
