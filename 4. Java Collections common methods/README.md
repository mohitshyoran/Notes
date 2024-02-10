# Hierarchy of Collection Framework
Common java collections and their most useful methods.

![](images/image01.png)

## 1. ArrayList
- It is dynamic array(like vector in c++).
- Does not work with premitive data types, need to use wrapper class.

```java
ArrayList<int> al = ArrayList<int>(); // does not work  
ArrayList<Integer> al = new ArrayList<Integer>(); // works fine
```

***Common Used Methods***
- void add(int index, E element)
- boolean add(E e)
- void clear()
- E get(int index)
- boolean isEmpty()
- Iterator()
- Object[] toArray()
- boolean contains(Object o)
- E remove(int index)
- boolean remove(Object o)
- E set(int index, E element)
- int size()

```java
Example

List<String> list=new ArrayList<String>();
list.add("Mango");  
list.add("Apple");

list.get(1);
list.set(1,"Dates");

Collections.sort(list);

//Traversing list through Iterator  
Iterator itr=list.iterator();
while(itr.hasNext()){ 
  System.out.println(itr.next());
}

list.remove(0);
```

## 2. LinkedList





 
  




