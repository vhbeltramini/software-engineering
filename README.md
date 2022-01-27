# Software Engineering

# Software Architecture
  - Fundamental organization of a system, or the way the highest level components are wired together.
  - It's how you organize your softwares components to then be more easily maintainable and to be easy to add new features 
  - Design decisions that need to be made early in a project
  - “Architecture is about the important stuff. Whatever that is” - Ralph Johnson.

An architect has to be able to recognize what elements are important, recognizing what elements are likely to result in serious problems should they not be controlled.


## Hexagonal(Ports & Adapters) Architecture 

<p align="center">
<img src="https://miro.medium.com/max/1200/1*LF3qzk0dgk9kfnplYYKv4Q.png" width="600px;" alt="Hexagonal Architecture example image" />
</p>

- The main idea when using this architecture is to isolate our business logic, to do that we can use ports and adapters to have request send to our core of the application.
- A simple example is when you will have a system and your account can be created from a few different places like an API or the system interface, but both will end up in the same main business logic of the application.

Primary adapters are the entry point of our application like a http request, an API or some other type of application. than the data will pass our core bussines logic and will pass throw to some other external mechanism that will be our driven Adapter that coulbe a database, a message queue etc.

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

  - Entities encapsulate the business rule. So it can be a set of data structures and functions or a object with methods, it does't really matter as long as the entities could be used by many different applications in the enterprise.
  - They are the least likely part of the system that will change when something external changes, so no operational change to any particular application should affect the entity layer.

### Use Cases

  - This layer will be responsible for application-specific business rules. 
  - It encapsulates and implements all of the use cases of the system. This will coordinate the data flow to and from the entities, and direct those entities to use their business rules to achieve the goals of the use case.
  - We also expect tha this layer will not be affected by exertnal changes like database, UI or other frameworks.

### Interface Adapters
  
  - This layer is a set of adapters that convert data from the format most convenient for the use cases and entities, to the format most convenient for some external agency such as the Database or the Web. 
  - For example this layer will contain all the MVC architecture of a GUI 
  - This layer will be responsable to convert the data from the form most convenient for entities and use cases, into the form most convenient for whatever persistence framework is being used. All the SQL related stuffs should be restricted to this layer too.

### Frameworks and Drivers / Outermost layer

  - This layer is generally composed of frameworks and tools for example the Database, the Web Framework, etc. Normaly you will not write much code here other than make the conections for the code communicates to the next circle inwards.

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
- Software design usually involves problem solving and planning a software solution. This includes both low-level component and algorithm design and high-level, architecture design.

Software Design is importante because it focus on the specification of software artifact that will help to developers to implement the software following the pattern and so maintaining a more organized development

# Questions
- Main diferences between Software architecture and Software design

  - Architecture: A higher vision about the system. Focus on the fundamental structures of the system.

  - Design: Low level view of the system. Focus on the specification of software artifact which will help to developers to implement the software.












# References: 

  - Who Needs an Architect? - https://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf
  - Architecture - https://martinfowler.com/architecture/
  - The Clean Code Blog / The Clean Architecture - https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html
