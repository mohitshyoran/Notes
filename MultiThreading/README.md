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


## Deamon Threads
1. It is a service provider threads that provides services to user threads.
eg: gc, finalizer etc.
2. When all user thread dies, JVM terminates this thread automatically.
3. Two Methods - setDeamon(boolean status), isDeamon()

## Java Thread Pool






   








