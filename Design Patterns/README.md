# Design Patterns

Design patterns are predefined solutions to commonly occurring problems in software design.

## Table of contents

* [Types of Design Patterns](#types-of-design-patterns)
* [Singleton Pattern](#singleton-pattern)
* [Prototype Pattern](#prototype-pattern)



## Types Of Design Patterns

**There are three types of Design Patterns.**

***Creational Patterns:*** Creational design patterns provide various object creation mechanisms.\
eg: Singleton design, Prototype design, Factory design pattern, Builder design, Abstract Factory etc.

***Structural Patterns:*** Structural design patterns explain how to assemble objects and classes into larger structures.\
eg: Adaptor design, Facade design, Decorator design, proxy design etc.

***Behavioural Patterns:*** defines how the objects should communicate and interact with one another.\
eg:Command pattern, Iterator pattern, Observer pattern, Strategy pattern, etc.



## Singleton Pattern
Singleton design pattern restricts the instantiation of a class to a single instance.\
***use case:*** DB connection, Logging.

```java
class Singleton {
    private static Singleton obj;
 
    // private constructor to force use of
    // getInstance() to create Singleton object
    private Singleton() {}
 
    public static Singleton getInstance()
    {
        if (obj == null)
            obj = new Singleton();
        return obj;
    }
}
```


## Prototype Pattern
Clone an existing object instead of creating new one, when object creation is time consuming, and costly.\
Then properties can be changed according to need.\
***use case:*** DB connection, Logging.

```java
class Singleton {
    private static Singleton obj;
 
    // private constructor to force use of
    // getInstance() to create Singleton object
    private Singleton() {}
 
    public static Singleton getInstance()
    {
        if (obj == null)
            obj = new Singleton();
        return obj;
    }
}
```


