# Design Patterns

Design patterns are predefined solutions to commonly occurring problems in software design.\
There are three types of Design Patterns.
  
**1. Creational:**
Creational design patterns provide various object creation mechanisms.\
eg: Singleton design, Prototype design, Factory design pattern, Builder design, Abstract Factory etc.

* [Singleton Pattern](#singleton-pattern)
* [Prototype Pattern](#prototype-pattern)
* [Factory Pattern](#factory-pattern)
* [Builder Pattern](#builder-pattern)
  
**2. Structural:**
Structural design patterns explain how to assemble objects and classes into larger structures.\
eg: Adaptor design, Facade design, Decorator design, proxy design etc.

* [Decorator Pattern](#decorator-pattern)
* [Adapter Pattern](#adapter-pattern)
  
**3. Behavioural:**
defines how the objects should communicate and interact with one another.\
eg:Command pattern, Iterator pattern, Observer pattern, Strategy pattern, etc.

* [Observer Pattern](#observer-pattern)


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
It allows a user to add new functionality to an existing object without altering its structure.\
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


## Observer Pattern
A behavioral design pattern that lets you define a subscription mechanism to notify multiple objects about any events that happen to an object. \
***use case:*** update change in score to Score Display and Predictor.
```java
class CricketData{
	int runs, wickets;
	float overs;
	CurrentScoreDisplay currentScoreDisplay;
	AverageScoreDisplay averageScoreDisplay;

	public CricketData(CurrentScoreDisplay currentScoreDisplay, AverageScoreDisplay averageScoreDisplay){
		this.currentScoreDisplay = currentScoreDisplay;
		this.averageScoreDisplay = averageScoreDisplay;
	}

	public void dataChanged(int runs, int wickets, float overs){
		this.runs = runs;
		this.wickets = wickets;
		this.overs = overs;

		currentScoreDisplay.update(runs,wickets,overs);
		averageScoreDisplay.update(runs,wickets,overs);
	}
}

class AverageScoreDisplay{
	private float runRate;
	private int predictedScore;

	public void update(int runs, int wickets, float overs){
		this.runRate = (float)runs/overs;
		this.predictedScore = (int) (this.runRate * 50);
		display();
	}

	public void display(){
		System.out.println("\nAverage Score Display:\n" + "Run Rate: " + runRate + "\nPredictedScore: " + predictedScore);
	}
}

class CurrentScoreDisplay{
	private int runs, wickets;
	private float overs;

	public void update(int runs,int wickets,float overs){
		this.runs = runs;
		this.wickets = wickets;
		this.overs = overs;
		display();
	}

	public void display(){
		System.out.println("\nCurrent Score Display: \n" + "Runs: " + runs +"\nWickets:" + wickets + "\nOvers: " + overs );
	}
}

public class Main{
	public static void main(String args[]){
	    // Observer
		AverageScoreDisplay averageScoreDisplay = new AverageScoreDisplay();
		CurrentScoreDisplay currentScoreDisplay = new CurrentScoreDisplay();

        // Subject
		CricketData cricketData = new CricketData(currentScoreDisplay, averageScoreDisplay);

		cricketData.dataChanged(50, 5, (float)10.2);
	}
}

output:
Current Score Display: 
Runs: 50
Wickets:5
Overs: 10.2

Average Score Display:
Run Rate: 4.901961
PredictedScore: 245
```

## Adapter Pattern
Adapter pattern works as a bridge between two incompatible interfaces. \

```java
interface Bird{
	// birds implement Bird interface that allows them to fly and make sounds adaptee interface
	public void fly();
	public void makeSound();
}

class Sparrow implements Bird{
	public void fly(){
		System.out.println("Flying");
	}
	public void makeSound(){
		System.out.println("Chirp Chirp");
	}
}

interface ToyDuck{
	// target interface
	// toyducks dont fly they just make squeaking sound
	public void squeak();
}

class PlasticToyDuck implements ToyDuck{
	public void squeak(){
		System.out.println("Squeak");
	}
}

class BirdAdapter implements ToyDuck{
	// You need to implement the interface your client expects to use.
	Bird bird;
	public BirdAdapter(Bird bird){
		// we need reference to the object we are adapting
		this.bird = bird;
	}

	public void squeak(){
		// translate the methods appropriately
		bird.makeSound();
	}
}

class Main
{
	public static void main(String args[])
	{
		Sparrow sparrow = new Sparrow();
		ToyDuck toyDuck = new PlasticToyDuck();

		// Wrap a bird in a birdAdapter so that it behaves like toy duck
		ToyDuck birdAdapter = new BirdAdapter(sparrow);

		System.out.println("Sparrow...");
		sparrow.fly();
		sparrow.makeSound();

		System.out.println("ToyDuck...");
		toyDuck.squeak();

		// toy duck behaving like a bird
		System.out.println("BirdAdapter...");
		birdAdapter.squeak();
	}
}
```

