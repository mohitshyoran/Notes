# Common Java Questions

### What is the purpose of interface?
- Provide 100% abstraction and multiple inheritance.

### What is abstract class?
- Can have abstract and non abstract method both.
- Provide partial abstraction.
- Abstract method - only declaration, should be implemented in extended class.

### Will a finally block execute after a return statement in a method in Java?
Yes

### What is final variable, method, class?
- Variable - can't change it.
- Method - can't override it.
- Class - can't extend it.

### Can garbage collector can be called explicitly in Java?
- Yes

### What is finalize() method in java?
- It is called always just before garbage collector destroys object(clean up).

### Stream vs collections?
- In Collection in memory data structure - every element computed before adding to collection, Stream is fixed data structure - computes on demand.
- Stream lets you process items one by one, while a Collection is like a basket that holds a bunch of items together.
- Streams are good for functional-style processing, and Collections are good for storing and managing groups of things.

### What are Mutable and immutable objects in java?
- A mutable object can be changed after it's created, and an immutable object can't.
- In Java, everything (except for strings) is mutable by default

### Throw vs Throws?
- Throw - throws a exception explicitly, checked(ClassNotFoundException, SQLException IOException) and unchecked(NullPointerException, ArithmeticException) both.
- Throws -  used with method signature expect declared exception might be thrown from method body, only unchecked exception.

### Virtual Function in C++?
- C++ determines which function is to be invoked at the runtime based on the type of the object pointed by the base class pointer.
- Provide runtime polymorphism.

### OOPS and it's function in Java?
Programming paradigm based on the concept of objects, which can contain data and code
- Polymorphism - Means many forms. Code Reusability - improve the readability, maintainability, and efficiency of code - compile time(Method overloading) and runtime(Method overriding)
- Abstraction - Hiding internal implementation and showing only functionality to use - a. 100% by Interface, b. Partial by abstract class.
- Inheritance - Acquiring property of parent class
- Encapsulation - Binding code and data together - In build(java.io.*) and User Build(public, private, default, protected).


# OOPs
  






