# Design Patterns

Design patterns are predefined solutions to commonly occurring problems in software design.

## Table of contents
* [Types of Design Patterns](#types-of-design-patterns)
  
**Creational:**
* [Singleton Pattern](#singleton-pattern)
* [Prototype Pattern](#prototype-pattern)
* [Factory Pattern](#factory-pattern)
* [Builder Pattern](#builder-pattern)
  
**Structural:**
* [Decorator Pattern](#decorator-pattern)
  
**Behavioural:**
* [Decorator Pattern](#decorator-pattern)



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
***use case:*** could be used to create multiple instances of the same object with unique attribute values such as color or size.


## Factory Pattern
Provides an interface for creating objects in a superclass.\
Object is created without exposing creation logic and refers to newly created object using a common interface.\
***use case:*** Swiggy Order - dine in, takeout, delievery order. Uber rides - solo, shared, luxury rides.

```java
public interface Notification {
    void notifyUser();
}

public class SMSNotification implements Notification {
    @Override
    public void notifyUser()
    {
        System.out.println("Sending an SMS notification");
    }
}

public class EmailNotification implements Notification {
    @Override
    public void notifyUser()
    {
        System.out.println("Sending an e-mail notification");
    }
}

public class NotificationFactory {
    public Notification createNotification(String channel)
    {
        switch (channel) {
        case "SMS":
            return new SMSNotification();
        case "EMAIL":
            return new EmailNotification();
        default:
            throw new IllegalArgumentException("Unknown channel "+channel);
        }
    }
}

public class NotificationService {
    public static void main(String[] args)
    {
        NotificationFactory notificationFactory = new NotificationFactory();
        Notification notification = notificationFactory.createNotification("SMS");
        notification.notifyUser();
    }
}
```

## Builder Pattern
Construct a complex object from simple objects using step-by-step approach.\
***use case:*** --.



## Decorator Pattern
It is Structural design pattern which allows a user to add new functionality to an existing object without altering its structure.\
***use case:*** For add-ons(ex: Burger with extra cheese, with extra Mayonnaise.)

```java
interface Shape {
    void draw();
}

class Rectangle implements Shape {
 
    @Override public void draw(){
        System.out.print("Shape: Rectangle");
    }
}

abstract class ShapeDecorator implements Shape {
    protected Shape decoratedShape;

    public ShapeDecorator(Shape decoratedShape){
        this.decoratedShape = decoratedShape;
    }
 
    public void draw(){ 
        decoratedShape.draw(); 
    }
}

class RedShapeDecorator extends ShapeDecorator {
    public RedShapeDecorator(Shape decoratedShape){
        super(decoratedShape);
    }
 
    @Override public void draw(){
        decoratedShape.draw();
        setRedBorder(decoratedShape);
    }
 
    private void setRedBorder(Shape decoratedShape){
        System.out.println(", Border Color: Red");
    }
}

public class MyClass {
    public static void main(String args[]) {
        Shape rectangle = new Rectangle();
        rectangle.draw();
        System.out.println();
         
        rectangle = new RedShapeDecorator(rectangle);
        rectangle.draw();
    }
}

output: Shape: Rectangle
Shape: Rectangle, Border Color: Red
```



