# System Architecture Questions

### Q1. What API first approach?
It is a development model where design of the application starts with the API, before any code is written.

### Q2. Design rate limiter?
It is a technique used in software systems to control the rate of incoming requests.
1. Token Bucket Algorithm
2. Leaky Bucket Algorithm

### Q3. What is evection policy in database?
The eviction policy determines what happens when a database reaches its memory limit.
To make room for new data, older data is evicted (removed) according to the selected policy.

### Q4 What is circuit breaker?
When a service request fails repeatedly, the Circuit Breaker opens, halting all calls to the service. This mechanism allows the failing service time to recover,
and once it does, the Circuit Breaker closes. restoring connections and resuming operations.

### Q5 What is data base sharding?
Sharding is a type of DataBase partitioning in which a large database is divided or partitioned into smaller data and different nodes.
ex: Student's data in college can be divided by years and stored differently.


### Q6 What is CAP Theorem?
The CAP theorem states that it is not possible to guarantee all three of the desirable properties – consistency, availability, and partition tolerance at the same time in a distributed system with data replication.

### Q7. Where will you use an event driven system? How does an event driven system work?
An event-driven architecture uses events to trigger and communicate between decoupled services and is common in modern applications built with microservices.


### Q8. Describe SOLID principles.
***1. Single Responsibility Principle:*** 
every class should have a single responsibility or single job or single purpose.

***2. Open/Closed Principle:***
software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

***3. Liskov’s Substitution Principle:***
“Derived or child classes must be substitutable for their base or parent classes“.

***4. Interface Segregation Principle:***
This principle is the first principle that applies to Interfaces instead of classes.

***5. Dependency Inversion Principle:***
High-level modules/classes should not depend on low-level modules/classes. Both should depend upon abstractions.





