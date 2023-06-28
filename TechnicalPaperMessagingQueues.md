
## Q.1 What are Messaging Queues? 


Message queues provide an asynchronous communications mechanism in which the sender and the receiver of a message do not contact each other, nor do they need to communicate with the message queue at the same time. When a sender places a message onto a queue, it is stored until the recipient receives them.

![Messaging Queues](https://www.tutorialspoint.com/inter_process_communication/images/message_queue.jpg)

![Messaging Queues](https://www.tutorialspoint.com/inter_process_communication/images/multiple_message_queue.jpg)

Here's how the messaging queue can be utilized in the pizza shop example:

![Pizza Shop Example](https://www.cloudamqp.com/img/blog/microservices-series/part-1/pizza-store-with-low-traffic.png)
![Pizza Shop Example](https://www.cloudamqp.com/img/blog/microservices-series/part-1/pizza-store-with-high-traffic.png)
![Pizza Shop Example](https://www.cloudamqp.com/img/blog/microservices-series/part-1/asynchronous-request-processing.png)


- **Order Placement :** When a customer places an order online, the order details (e.g., customer name, pizza type, delivery address) are sent as a message and added to the message queue.

- **Order Processing :** A message queue consumer, known as the Order Processor, continuously monitors the message queue for new orders. It retrieves the order messages from the queue one by one, processes them, and performs tasks such as verifying the availability of ingredients and assigning a delivery personnel. Once processed, the order moves to the next stage.

- **Order Preparation :** Another message queue consumer, known as the Pizza Maker, listens to the message queue and retrieves the processed orders. It retrieves the specific order message, prepares the pizza accordingly, and adds a message to the queue indicating the completion of the pizza preparation.

- **Baking and Delivery :** The Pizza Baker, another consumer, listens to the message queue and retrieves the messages indicating that pizzas are ready for baking. The baker takes the pizzas, bakes them in the oven, and adds a message to the queue once they are baked. Meanwhile, a Delivery Coordinator listens to the queue for baked pizza messages, assigns delivery personnel, and adds a message indicating the assigned delivery.

- **Delivery Confirmation :** After the pizzas are delivered to the customers, the delivery personnel update the order status in the system, which can be done by sending a message to another queue or an API call to update the order status accordingly.


Messaging queues, also known as message queues or message brokers, are a form of asynchronous communication between distributed systems or components. They act as intermediaries, enabling reliable and scalable communication by allowing producers to send messages to a queue, which can then be consumed by one or more consumers at their own pace.


***
## Q.2 Why they are used?

#### Messaging queues are used in various scenarios, including:

- **Decoupling systems :** Messaging queues decouple the sender and receiver, allowing them to operate independently. Producers and consumers don't need to be aware of each other's existence or availability, enhancing system flexibility and resilience.

- **Load balancing :** Multiple consumers can read messages from a queue, enabling load balancing across different components or services. This ensures efficient utilization of resources and can help handle spikes in traffic.

- **Asynchronous processing :** Producers can send messages to a queue without waiting for immediate responses. Consumers can process messages at their own pace, enabling asynchronous processing and improved system performance.

- **Fault tolerance :** Messaging queues often provide persistence and durability, ensuring that messages are not lost even if a consumer or system component fails. This helps maintain reliable communication and prevents message loss.

- **Scalability :** By leveraging messaging queues, systems can be easily scaled horizontally by adding more consumers or workers to process messages in parallel.

***

## Q.3 What are popular tools?

#### Popular messaging queue tools :

- **[Apache Kafka](https://www.tutorialspoint.com/apache_kafka/apache_kafka_introduction.htm) :** A distributed streaming platform that provides high-throughput, fault-tolerant messaging. Kafka is widely used for building real-time streaming data pipelines and event-driven architectures.

- **[RabbitMQ](https://www.tutorialspoint.com/rabbitmq/index.htm) :** An open-source message broker that implements the Advanced Message Queuing Protocol (AMQP). RabbitMQ supports multiple messaging patterns, including publish/subscribe and request/reply, and is known for its ease of use and reliability.

- **[Apache ActiveMQ](https://www.tutorialspoint.com/apache_activemq/index.htm) :** An open-source message broker that supports multiple messaging protocols such as AMQP, MQTT, and STOMP. ActiveMQ provides features like message persistence, clustering, and high availability.

- **[Amazon Simple Queue Service (SQS)](https://www.geeksforgeeks.org/amazon-web-services-introduction-to-simple-queue-servicesqs/) :** A fully managed message queuing service provided by Amazon Web Services (AWS). SQS offers reliable and scalable message queuing with pay-as-you-go pricing.


***
## Q.4 What is Enterprise Message Bus?

Enterprise Message Bus (EMB), also known as an Enterprise Service Bus (ESB), is an architectural pattern that focuses on integrating various enterprise applications and systems by providing a central communication backbone. An EMB typically includes messaging capabilities, transformation, routing, and orchestration features.

Enterprise Message Buses offer features beyond basic messaging queues, such as protocol translation, content-based routing, transformation, and service orchestration, making them suitable for complex enterprise integration scenarios.

***

## References

- [Youtube Video](https://youtu.be/oUJbuFMyBDk)
- [Youtube Video](https://www.youtube.com/watch?v=5-Rq4-PZlew)
- [Adobe Developer](https://developer.adobe.com/commerce/php/development/components/message-queues/)
- [Tutorials Point](https://www.tutorialspoint.com/inter_process_communication/inter_process_communication_message_queues.htm)
- [Cloudamqp.com](https://www.cloudamqp.com/blog/microservices-and-message-queues-part-1-understanding-message-queues.html)

---
