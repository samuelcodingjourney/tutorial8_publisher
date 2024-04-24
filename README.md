### Tutorial 8
a. How many data your publisher program will send to the message broker in one run?
Publisher program will send five data to the message broker in one run. This can be seen in p.publish_event() where this call is for sending one instance of UserCreatedEventMessage to the message broker.
b. The url of: "amqp://guest:guest@localhost:5672" is the same as in the subscriber program, what does it mean?
The url is the same as both the publisher and subscriber programs because both of them are connecting to the same AMQP broker that is running on localhost. So the authentication using guest:guest remains the same as in the subscriber program to ensure that the publisher who sends messages to that same message broker where the subscriber is currently listening. This would enable communication between publisher and subscriber.