### Tutorial 8
a. How many data your publisher program will send to the message broker in one run?
Publisher program will send five data to the message broker in one run. This can be seen in p.publish_event() where this call is for sending one instance of UserCreatedEventMessage to the message broker.
b. The url of: "amqp://guest:guest@localhost:5672" is the same as in the subscriber program, what does it mean?
The url is the same as both the publisher and subscriber programs because both of them are connecting to the same AMQP broker that is running on localhost. So the authentication using guest:guest remains the same as in the subscriber program to ensure that the publisher who sends messages to that same message broker where the subscriber is currently listening. This would enable communication between publisher and subscriber.


RabbitMQ running screen:
![Screenshot (1052)](https://github.com/samuelcodingjourney/tutorial8_publisher/assets/94734973/540aadf1-65b2-46a9-ace8-ae8650e7ab40)

Subscriber Console:
![Screenshot (1053)](https://github.com/samuelcodingjourney/tutorial8_publisher/assets/94734973/89246e19-8a73-4110-b0c1-ce6ef314aaea)

Publisher Console:
![Screenshot (1054)](https://github.com/samuelcodingjourney/tutorial8_publisher/assets/94734973/7e705e94-b928-4882-8189-c57b6f675867)

Explanation about the consoles:
Basically, the subscriber program was ran so that it listens to events from the message broker with the help of cargo run command. Thne the publisher program will be run using cargo run as well in order to start sending the events to message broker. This action of running both programs initiates the first interaction between them. Publisher program would then be run again using cargo run for seeing the interaction of the subscriber when consuming the events send by the message broker as can be seen in the subscriber console screenshot above and the proof of the runnning publisher program in above screenshot as well.  

Monitoring chart based on publisher:
![Screenshot (1056)](https://github.com/samuelcodingjourney/tutorial8_publisher/assets/94734973/13b849d4-21b0-40b9-a75f-55bce2326acd)

Explanation about the spikes:
The spikes in RabbitMQ as shown in above screenshot specifically on the second chart correspond to the increased message throughput caused by running cargo run on the publisher program, basically each time running the publisher program which can be more than one time or multiple time. Each time the publisher sends events to the message broker, the message count and activity level gets increased leading to the spikes shown on the graph where the red lines meaning the deliver (manual ack) and purple lines meaning the consumer ack. Manual ack is when the consumer explicitly acknowledge each message after being processed. On the other hand, consumer acknowledgement means that RabbitMQ automaticallt acknowledge messages when they are delivered to the consumers. 
