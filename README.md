# Software Engineering

# Software Architecture
  - Fundamental organization of a system, or the way the highest level components are wired together.
  - It's how you organize your pieces of software components to then be more easily maintainable and to be easy to add new features 
  - Design decisions that need to be made early in a project
  - “Architecture is about the important stuff. Whatever that is” - Ralph Johnson.

An architect has to be able to recognize what elements are important, recognizing what elements are likely to result in serious problems should they not be controlled.


## Hexagonal(Ports & Adapters) Architecture 

<p align="center">
<img src="https://miro.medium.com/max/1200/1*LF3qzk0dgk9kfnplYYKv4Q.png" width="600px;" alt="Hexagonal Architecture example image" />
</p>

- The main idea when using this architecture is to isolate our business logic, to do that we can use ports and adapters to have request send to our core of the application.
- A simple example is when you will have a system and your account can be created from a few different places like an API or the system interface, but both will end up in the same main business logic of the application.

Primary adapters are the entry point of our application like a http request, an API or some other type of application. Then the data will pass our core business logic and will pass throw to some other external mechanism that will be our driven Adapter that could be a database, a message queue etc.

## Most used/known software architectures.
<ul>
  <li><a href="http://alistair.cockburn.us/Hexagonal+architecture">Hexagonal Architecture</a> (a.k.a. Ports and Adapters) by Alistair Cockburn and adopted by Steve Freeman, and Nat Pryce in their wonderful book <a href="http://www.amazon.com/Growing-Object-Oriented-Software-Guided-Tests/dp/0321503627">Growing Object Oriented Software</a></li>
  <li><a href="http://jeffreypalermo.com/blog/the-onion-architecture-part-1/">Onion Architecture</a> by Jeffrey Palermo</li>
  <li><a href="http://blog.cleancoders.com/2011-09-30-Screaming-Architecture">Screaming Architecture</a> from a blog of mine last year</li>
  <li><a href="http://www.amazon.com/Lean-Architecture-Agile-Software-Development/dp/0470684208/">DCI</a> from James Coplien, and Trygve Reenskaug.</li>
  <li><a href="http://www.amazon.com/Object-Oriented-Software-Engineering-Approach/dp/0201544350">BCE</a> by Ivar Jacobson from his book <em>Object Oriented Software Engineering: A Use-Case Driven Approach</em></li>
</ul>

## Clean Architecture
<p align="center"> 
<img src="https://blog.cleancoder.com/uncle-bob/images/2012-08-13-the-clean-architecture/CleanArchitecture.jpg"  width="600px;" alt="" />
</p>

### Entities

  - Entities encapsulate the business rule. So it can be a set of data structures and functions or an object with methods, it doesn't really matter as long as the entities could be used by many applications in the enterprise.
  - They are the least likely part of the system that will change when something external changes, so no operational change to any particular application should affect the entity layer.

### Use Cases

  - This layer will be responsible for application-specific business rules. 
  - It encapsulates and implements all the use cases of the system. This will coordinate the data flow to and from the entities, and direct those entities to use their business rules to achieve the goals of the use case.
  - We also expect tha this layer will not be affected by external changes like database, UI or other frameworks.

### Interface Adapters
  
  - This layer is a set of adapters that convert data from the format most convenient for the use cases and entities, to the format most convenient for some external agency such as the Database or the Web. 
  - For example this layer will contain all the MVC architecture of a GUI 
  - This layer will be responsible to convert the data from the form most convenient for entities and use cases, into the form most convenient for whatever persistence framework is being used. All the SQL related stuffs should be restricted to this layer too.

### Frameworks and Drivers / Outermost layer

  - This layer is generally composed of frameworks and tools for example the Database, the Web Framework, etc. Normally you will not write much code here other than make the connections for the code communicates to the next circle inwards.

## Specifics

- The main concern on the clean architecture is the separation of concerns. You can achieve that by dividing the software into layers, each has at least one layer for business rules, and another for interfaces.
- Some get there the software will have to be 
  - Independent of Frameworks. The architecture does not depend on the existence of some library of feature laden software. This allows you to use such frameworks as tools, rather than having to cram your system into their limited constraints.
  - Testable. The business rules can be tested without the UI, Database, Web Server, or any other external element.
  - Independent of UI. The UI can change easily, without changing the rest of the system. A Web UI could be replaced with a console UI, for example, without changing the business rules.
  - Independent of Database. You can swap out Oracle or SQL Server, for Mongo, BigTable, CouchDB, or something else. Your business rules are not bound to the database.
  - Independent of any external agency. In fact your business rules simply don’t know anything at all about the outside world. <a href="https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html">source/credits</a>

# Software Design

- Software design is the process in the development which creates a specification of a software artifact, intended to accomplish goals.
- Software design usually involves problem-solving and planning a software solution. This includes both low-level component and algorithm design and high-level, architecture design.

Software Design is important because it focuses on the specification of software artifact that will help to developers to implement the software following the pattern and so maintaining a more organized development


# Message Brokers

## Key definitions 
- A key feature used in many software designs and architecture are the messages brokers. A message broker is a cross-application communication technology that helps build common integration mechanisms to support cloud-native, microservices-based, serverless, and hybrid cloud architectures. 
- Message Brokers enable the programmers to build applications, systems and services to communicate with each other and exchange information. On that same process they can validate, store, route, and deliver messages to the appropriate destinations.
- To provide reliability they often rely on message queue structures where they store the massages in order until they are fully consumed by the application. So they will normally follow a FIFO(**F**irst **I**n **F**irst **O**ut) method to organize and process the queue in order to process all messages that are in the queue

## Message broker models

### Peer-to-peer messaging

- This is the distribution pattern used in message queues with a one-to-one relationship between the sender and the consumer of the message. Each message in the queue is sent to only one recipient and processed only once. This method is used when the message only had to be executed once
  - A good example for this messaging pattern is a payroll/financial transaction processing. In these kinds of systems, both senders and receivers need a guarantee that each payment will be only be process once.

### Publish/subscribe messaging

- In this message distribution pattern, commonly referred to as "pub/sub", works with the idea that each message is published to a topic, and all the multiple message consumers that are subscribed to the topic will/want to receive those messages. All messages published on a topic will be distributed to all subscribed applications. This is basically a broadcast distribution method where we have a one-to-many relationship between the publisher of a message and its consumer.
  - A good scenario and example where we can use this kind of message distribution pattern will be in an airline company where they will have to release updated information about the flights, and that information could be used by multiple systems since ground crew performing aircraft maintenance, refueling, baggage handlers, flight attendants, pilots preparing the aircraft for the flight, operator visual displays to inform the public, and many others possibles systems 

<p align="center">
<img src="https://www.cloudamqp.com/img/blog/exchanges-topic-fanout-direct.png" width="600px;" />
</p>
<p align="center">Here we have a more basic visual example of how does work those mainly used message broker models</p>


# Questions
- Main differences between Software architecture and Software design

  - Architecture: A higher vision about the system. Focus on the fundamental structures of the system.

  - Design: Low level view of the system. Focus on the specification of software artifact which will help to developers to implement the software.












# References: 

  - Who Needs an Architect? - https://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf
  - Architecture - https://martinfowler.com/architecture/
  - The Clean Code Blog / The Clean Architecture - https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html
  - Message Brokers - https://www.ibm.com/cloud/learn/message-brokers


###### @TODO
###### Event Modeling - https://eventmodeling.org/posts/what-is-event-modeling/
