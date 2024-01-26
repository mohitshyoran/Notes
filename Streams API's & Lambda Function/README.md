# Stream API's practice questions
Source - https://www.w3resource.com/java-exercises/stream/index.php

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


