# MultiThreading

### What is Thread?
A thread is a lightweight subprocess, the smallest unit of processing. It is a separate path of execution.\
1. Threads are independent. If there occurs exception in one thread, it doesn't affect other threads.
2. It uses a shared memory area.

### Ways or Creating Thread()
1. By extending Thread class
2. By implementing Runnable interface

**Thread** extends **Object** implements **Runnable**\
***Thread*** - sleep(), start(), join(), getId(), toString() etc.\
***Object*** - Sleep(), start(), join() etc.\
***Runnable*** - only run() method()

```java
class MultithreadingDemo extends Thread 
{   
  public void run() 
 {   
     System.out.println("My thread is in running state.");    
 } 
  public static void main(String args[]) 
 {   
    MultithreadingDemo obj=new MultithreadingDemo();  
    obj.start();  
  }  
}
```

```java
class MultithreadingDemo implements Runnable 
{  
   public void run() 
 {  
      System.out.println("My thread is in running state.");  
  }  
    public static void main(String args[]) 
 {  
      MultithreadingDemo obj=new MultithreadingDemo();   
      Thread tobj =new Thread(obj);
      tobj.start();  
 }   
}
```

### Java Thread methods
**start()** - Starts newly created threads, thread moves form New to Runnable state, when gets chance to execute target run() method will run.\
**run()** - Starts execution of thread(run method body).\
**sleep(t)** - Pause execution for t milliseconds\
**join()** - Allows one thread to wait for the completion of another.\
**wait()** - Releases the lock on the object and waits until another thread calls notify() or notifyAll() on the same object.\
**notify()** - Wakes up only one thread waiting on the object and that thread starts execution.\
**notifyAll()** - Wakes up all threads waiting on the object.\
**setPriority()** - Sets thread priority.\
  Valid values - 1 to 10.\
  MIN_PRIORITY - 1, MAX_PRIORITY - 10, NORM_PRIORITY - 5



### Thread states(Life cycle of Thread)
New, Active, Blocked / Waiting, Timed Waiting, Terminated.

**New** - State right after creation.

**Active**
1. ***Runnable*** - ready to run.
2. ***Running*** - starts running when gets CPU from thread scheduler.
   
**Blocked**
1. ***Blocked*** - Resource is not free, with other thread.
2. ***Waiting*** - Join() - waiting for other thread to finish.

**Timed waiting** - wait(), sleep() - enters in wating state for specific time even if CPU avaialble.

**Terminated** - Completed execution or Exception occured.


### Thread scheduler
Decides which thread should run.
Only one thread can run at a time in single process.

**Scheduling algorithm**
1. ***Preepmptive** - Higher priority gets CPU first.
2. ***Time Slicing*** - Context switcing after a fixed time.
3. ***First come First Serve*** - The thread comes first gets CPU.

**Q1. Can we start a thread twice?**\
No!, It will run once, second time it will throw IllegalThreadStateException.

**Q2. What if we call run method instead of start() method?**\
Direct run method will run and it will be treated as normal object not as a thread.


### Deamon Threads
1. It is a service provider threads that provides services to user threads.
eg: gc, finalizer etc.
2. When all user thread dies, JVM terminates this thread automatically.
3. Two Methods - setDeamon(boolean status), isDeamon()

### Java Thread Pool
1. Repesemt a group of worker thread that are waiting for the job and reused many times.
2. or Take a thread, use it and put again in group.\
***Advantage:*** Saves time because of no need to create new thread.

### Thread Group
1. Multiple threads are grouped in single object.
2. In such way, we can suspend(), resume() group og threads by a signle method calls.

### Java garbage collection
1. Garbage means unrefrenced data.
2. It is way to destroy unused objects and free memory.
3. In java it is performed automatically.
4. Garbage collector of JVM collects only those object that are created by new keyword.\
-> All other destroyed(cleanup processing) by ***finalize()***.
***Advantage:*** - Memory efficient and Automatic.

**Q. How can a object be unreferenced?**
1. By nulling refrence.
   ```java
   employee e = new employee();
   e = null;
   ```
3. By assigning a refrence to another.
   ```java
   employee e1 = new employee();
   employee e2 = new employee();
   e1 = e2; \\ e1 will be deleted
   ```
3. By anonymus object.
   ```java
   new employee();
   ```


# Java synchronization
Synchronization in Java is the capability to control the access of multiple threads to any shared resource.\
Provides lock to threads.

**Two types**
1. Thread synchronization.
2. Process synchronization.

**Thread synchronization**
1. Mutual exclusive.
2. Cooperation (Inter-thread communication in java).

**Mutual exclusive**
1. Synchronized method.
2. Synchronized block.
3. Static synchronization.

**1. Synchronized method**
Synchronized method is used to lock an object for any shared resource.\
When a thread invokes a synchronized method, it automatically acquires the lock for that object and releases it when the thread completes its task.

```java
class Line 
{ 
    synchronized public void getLine() 
    { 
        for (int i = 0; i < 3; i++) 
        { 
            System.out.println(i); 
        } 
    } 
}
```
**2. Synchronized block**
Prevent multiple threads from executing a portion of a code in a method at the same time.
```java
public class Geek 
{
    public int count = 0; 
    public void geekName() 
    {
        // Only one thread is permitted to enter at a time. 
        synchronized(this) 
        { 
            count++;
        }  
    } 
}
```

**3. Static Synchronization**
The lock will be on the class not on object.\
Static is property of class not object so it will work on class level.

```java
class Table  
{     
 synchronized static void printTable(int n){    
   for(int i=1;i<=10;i++){    
     System.out.println(n*i);    
   }    
 }    
} 
```

# Multithreading coding questions.

**Q1. Write a java code with three threads, which will alternatively write number from 1 to 15.
Like first thread 1, then second 2, then third 3 and then again first thread 4.**
```java
class SharedResource {
    private int count = 1;
    private final int maxCount = 15;

    public synchronized void printNumber(int expectedThreadNumber) {
        while (count <= maxCount) {
            int actualThreadNumber = (count - 1) % 3;
            if (actualThreadNumber == expectedThreadNumber) {
                System.out.println("Thread " + (expectedThreadNumber + 1) + ": " + count++);
                notifyAll();
            } else {
                try {
                    wait();
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                }
            }
        }
    }
}

class NumberPrinter extends Thread {
    private final SharedResource sharedResource;
    private final int threadNumber;

    public NumberPrinter(SharedResource sharedResource, int threadNumber) {
        this.sharedResource = sharedResource;
        this.threadNumber = threadNumber;
    }

    @Override
    public void run() {
        sharedResource.printNumber(threadNumber);
    }
}

public class MyClass {
    public static void main(String args[]) {
        SharedResource sharedResource = new SharedResource();

        NumberPrinter thread1 = new NumberPrinter(sharedResource, 0);
        NumberPrinter thread2 = new NumberPrinter(sharedResource, 1);
        NumberPrinter thread3 = new NumberPrinter(sharedResource, 2);

        thread1.start();
        thread2.start();
        thread3.start();
    }
}
```







   






   








