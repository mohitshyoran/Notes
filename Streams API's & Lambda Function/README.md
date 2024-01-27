# Stream API's practice questions
Source - https://www.w3resource.com/java-exercises/stream/index.php

**What is difference in stream and collection?**
1. Collection is memory data structure - every element computed before adding to collection, Stream is fixed data structure - computes on demand.
2. Stream lets you process items one by one, while a Collection is like a basket that holds a bunch of items together.
3. Streams are good for functional-style processing, and Collections are good for storing and managing groups of things.

**There are two type of operation in Stream**\
***1. Intermediate*** : return a stream as a result.\
eg: map(), filter(), distinct(), sorted(), limit(), skip() etc.\
***1. Terminal*** : return non-stream values like primitive or object or collection or may not return anything.\
eg: forEach(), toArray(), reduce(), collect(), min(), max(), count(), anyMatch(), allMatch(), noneMatch(), findFirst(), findAny() etc.\

### Q1. Write a Java program to calculate the average of a list of integers using streams.
```java
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
        List<Integer> list = Arrays.asList(1,2,3,3,5);
        Double avg = list.stream()
                        .mapToDouble(Integer::doubleValue)
                        .average()
                        .orElse(0.0);
        System.out.println(avg);
    }
}
```

### Q2. Write a Java program to convert a list of strings to uppercase or lowercase using streams.
```java
import java.util.*;
import java.util.stream.*;
public class MyClass {
    public static void main(String args[]) {
        List<String> list = Arrays.asList("abc", "cde");
        list = list.stream()
                    .map(String::toUpperCase)
                    .collect(Collectors.toList());
        System.out.println(list);
    }
}
```

### Q3. Write a Java program to calculate the sum of all even, odd numbers in a list using streams.
```java
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
        List<Integer> list = Arrays.asList(1,2,3,4,5);
        Integer oddSum = list.stream()
                        .filter(num -> num%2 == 1)
                        .mapToInt(Integer::intValue)
                        .sum();
        Integer evenSum = list.stream()
                .filter(num -> num%2 == 0)
                .mapToInt(Integer::intValue)
                .sum();
        System.out.println(oddSum);
        System.out.println(evenSum);
    }
}
```

### Q4. Write a Java program to remove all duplicate elements from a list using streams.
```java
import java.util.*;
import java.util.stream.*;
public class MyClass {
    public static void main(String args[]) {
        List<Integer> list = Arrays.asList(1,2,3,3,5);
        list = list.stream()
                .distinct()
                .collect(Collectors.toList());
                        
        System.out.println(list);
    }
}
```

### Q5.  Write a Java program to count the number of strings in a list that start with a specific letter using streams.
```java
import java.util.*;
import java.util.stream.*;
public class MyClass {
    public static void main(String args[]) {
        List<String> list = Arrays.asList("abc", "cde", "abdc");
        long count = list.stream()
                    .filter(str -> str.startsWith("ab"))
                    .count();
        System.out.println(count);
    }
}
```

### Q6.  Write a Java program to sort a list of strings in alphabetical order, ascending and descending using streams.
```java
import java.util.*;
import java.util.stream.*;
public class MyClass {
    public static void main(String args[]) {
        List<String> list = Arrays.asList("peter", "kevin", "fish");
        List<String> asc = list.stream()
                    .sorted()
                    .collect(Collectors.toList());
        System.out.println(asc);
        List<String> dsc = list.stream()
                    .sorted(Comparator.reverseOrder())
                    .collect(Collectors.toList());
        System.out.println(dsc);
    }
}
```

### Q7.  Write a Java program to find the maximum and minimum values in a list of integers using streams.
```java
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
        List<Integer> list = Arrays.asList(1,2,3,3,5);
        
        Integer max = list.stream()
                    .max(Integer::compare)
                    .orElse(null);
        System.out.println(max);
        
        Integer min = list.stream()
                    .min(Integer::compare)
                    .orElse(null);
        System.out.println(min);
    }
}
```

### Q8.   Write a Java program to find the second smallest and largest elements in a list of integers using streams.
```java
import java.util.*;
public class MyClass {
    public static void main(String args[]) {
        List<Integer> list = Arrays.asList(1,2,3,4,5);
        
        Integer secondMin = list.stream()
                                .sorted()
                                .skip(1)
                                .findFirst()
                                .orElse(0);
        System.out.println(secondMin);//2
        
        Integer secondMax = list.stream()
                                .sorted((a,b) -> Integer.compare(b,a))
                                .skip(1)
                                .findFirst()
                                .orElse(0);
        System.out.println(secondMax);//4
    }
}
```

### Q9. How to find duplicate elements in a given integers list in java using Stream functions?
```java
import java.util.*;
import java.util.stream.*;

public class DuplicateElements {
  public static void main(String args[]) {
          List<Integer> myList = Arrays.asList(10,15,8,49,25,98,98,32,15);
          Set<Integer> set = new HashSet();
          myList.stream()
                .filter(n -> !set.add(n))
                .forEach(System.out::println);
  }
}
```

### Q10. Given a list of integers, separate odd and even numbers?
```java
import java.util.*;
import java.util.Map.*;
import java.util.stream.*;
 
public class Java8Code {
    public static void main(String[] args) {
        List<Integer> listOfIntegers = Arrays.asList(71, 18, 42, 21, 67, 32, 95, 14, 56, 87);
         
        Map<Boolean, List<Integer>> oddEvenNumbersMap = 
                listOfIntegers.stream().collect(Collectors.partitioningBy(i -> i % 2 == 0));
        
        System.out.println(oddEvenNumbersMap);
    }
}

// Output : {false=[71, 21, 67, 95, 87], true=[18, 42, 32, 14, 56]}
```

### Q10. How do you find frequency of each character in a string using Java 8 streams?
```java
import java.util.Map;
import java.util.function.Function;
import java.util.stream.Collectors;
 
public class Java8Code 
{
    public static void main(String[] args) 
    {
        String inputString = "Java Concept Of The Day";
         
        Map<Character, Long> charCountMap = inputString.chars()
                                                .mapToObj(c -> (char)c)
                                                .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
        // Function.identity() - always returns its input argument.                                        
         
        System.out.println(charCountMap);
    }
}

// Output : { =4, a=3, c=1, C=1, D=1, e=2, f=1, h=1, J=1, n=1, O=1, o=1, p=1, T=1, t=1, v=1, y=1}
```

### Q11. Given a list of strings, join the strings with ‘[‘ as prefix, ‘]’ as suffix and ‘,’ as delimiter?
```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;
 
public class Java8Code 
{
    public static void main(String[] args) 
    {
        List<String> listOfStrings = Arrays.asList("Facebook", "Twitter", "YouTube", "WhatsApp", "LinkedIn");
         
        String joinedString = listOfStrings.stream()
                                            .collect(Collectors.joining(",", "[", "]"));
         
        System.out.println(joinedString);
    }
}

// Output : [Facebook,Twitter,YouTube,WhatsApp,LinkedIn]
```

### Q12. How do you get three minimum numbers from the given list of integers??
```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.List;
 
public class Java8Code {
    public static void main(String[] args) {
        List<Integer> listOfIntegers = Arrays.asList(45, 12, 56, 15, 24, 75, 31, 89);
         
        listOfIntegers.stream().sorted().limit(3).forEach(System.out::println);
    }
}
```

### Q13. Given a list of strings, sort them according to increasing order of their length?
```java
import java.util.Arrays;
import java.util.List;
import java.util.Comparator;
import java.util.stream.Collectors;
 
public class Java8Code {
    public static void main(String[] args) {
        List<String> listOfStrings = Arrays.asList("Java", "Python", "C#", "HTML", "Kotlin", "C++", "COBOL", "C");
         
       listOfStrings.stream()
                    .sorted(Comparator.comparing(String::length))
                    .forEach(System.out::println);
    }
}
```

### Q14. How do you find common elements between two arrays?
```java
import java.util.Arrays;
import java.util.List;
 
public class Java8Code {
    public static void main(String[] args) {
        List<Integer> list1 = Arrays.asList(71, 21, 34, 89, 56, 28); 
        List<Integer> list2 = Arrays.asList(12, 56, 17, 21, 94, 34);
         
        list1.stream().filter(num -> list2.contains(num)).forEach(System.out::println);
    }
}
```

### Q15.  Reverse each word of a string using Java 8 streams??
```java
import java.util.Arrays;
import java.util.stream.Collectors;
 
public class Java8Code {
    public static void main(String[] args) {
        String str = "Java Concept Of The Day";
        String reversedStr = Arrays.stream(str.split(" "))
                                    .map(word -> new StringBuffer(word).reverse())
                                    .collect(Collectors.joining(" "));
         
        System.out.println(reversedStr);
    }
}
```

# Lambda Expression Practice Questions
A lambda in Java essentially consists of three parts: a parenthesized set of parameters, an arrow, and then a body, which can either be a single expression or a block of Java code.
No argument - () -> System.out.println("Hello")
one argument - (arg1) -> System.out.println(arg1)
Single statement - (arg1, arg2) -> arg1+arg2
Multiple statement - (arg1, arg2) -> {System.out.println(arg1); return arg1+arg2;}

### Write a Java program to implement a lambda expression to find the sum of two integers.
```java
interface SumCalculator {
    int sum(int a, int b);
}

public class MyClass {
    public static void main(String args[]) {
        SumCalculator sumCalculator = (x,y) -> x+y;
        int sum = sumCalculator.sum(10, 15);
        System.out.println("Sum of x+y = " + sum);
    }
}
```

