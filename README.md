# Java Interview Questions

* [General Questions](#general-questions)
* [OOP Questions](#oop-questions)
* [Algorithms and Data Structures / Collections / Generics](#algorithms-and-data-structures--collections--generics)
* [Streams And Lambdas](#streams-and-lambdas)
* [Threads](#threads-async)
* [Creational, Structural and Behavioral Design Patterns](#creational-structural-and-behavioral-design-patterns)
* [Java EE](#java-ee)
* [Spring](#spring)
* [Generic WEB](#generic-web)
* [SQL](#sql)
* [Exercises](#exercises)

## General Questions

* What are the key memory segments inside JVM ? Explain **HEAP**, **STACK**.
* What is a **Memory Leak** ? How can a memory leak appear in **garbage collected** language ?
* Is Java *pass-by-value* or *pass-by-reference* ?
* Write a Java method to swap the values of two integer values (*Is it possible ?*):
```Java
public void swap(int x, int y) { /** code here **/ }
```
* What is a *primitive type* in Java ? What are the main *primitive types* ?
* What is *auto-boxing/unboxing* ?
* What is *implicit casting* ? What is *explicit casting* ?
* If developing an e-commerce site, what is the recommend type to use for the *price* if performance is not an issue. What if performance is an issue ?
* Explain the usage of the following keywords: `strictfp`, `native`.
* Explain the usage of the following keyword: `final`.
* Can you give example of a `final` class from the Java Standard library ?
* What is the difference between `==` and `equals()` ?

## OOP Questions

* What is a **constructor** ?
* What is the **default constructor** ?
* Explain the the concept of *Inheritance*. Why doesn't Java supports the concept of *Multiple Inheritance* ?
* What is **Polymorphism** ?
* What is **Overloading** ? What is **Overriding** ?
* What is the output if we execute the following code:
```Java
public abstract class Engineer {
    public static String name() {
        return "Engineer";
    }
    public String favorite() {
        return "Math and Physics";
    }
    public static void main(String[] args) {
        Engineer e2 = new ElectricalEngineer();
        Engineer e3 = new SoftwareEngineer();
        System.out.format("%s %s \n", e2.name(), e2.favorite());
        System.out.format("%s %s", e3.name(), e3.favorite());
    }
}
class ElectricalEngineer extends Engineer {
    public static String name() { return "Electrical Engineer" }
    public String favorite() { return "Electricity"; }
}
class SoftwareEngineer extends Engineer {
    public static String name() { return "Software Engineer"; }
    public String favorite() { return "Java"; }
}
```
* Can a `static` method be overwritten ?
* Explain the concept of *Encapsulation*.
* How would you encapsulate the following class:
```Java
public class Circle {
  double radius;
  double area;
}
```
* What is *immutability* ?
* How can we write an **Immutable** class ?
* Explain of the concept of **Marker Inteface**.
* Explain the concept of **Serialization**.
* Explain how the keyword **transient** works.
* Explain the concept behind the **Cloneable** interface and how does it work.
* What is the output if we execute the following code:

```Java
public class Constructors {
    public static void main(String[] args) {
        new Dog();
    }
}
class Animal {

    public Animal() { System.out.println("1"); }

    public Animal(String s) {
        this();
        System.out.println("2");
    }
}
class Dog extends Animal {
    public Dog() {
        super("3");
        System.out.println("4");
    }
}
```
* What is the output if we execute the following code:

```Java
public class Ternary {
    public static void main(String[] args) {
        Integer x = 1987;
        Integer y = 1987;
        System.out.println(x == y ? "A" : "B");
    }
}
```

* What is the output if we execute the following code:

```Java
public class Strings {
    public static final String DELOITTE = new String("Deloitte");
    public static void main(String[] args) {
        String s1 = "Deloitte";
        String s2 = new String(s1);
        String s3 = new String("Deloitte");
        String s4 = "Deloitte";
        System.out.println(s1==s2);
        System.out.println(s1==s3);
        System.out.println(s1==s4);
        System.out.println(s1==DELOITTE);
        System.out.println(s2==DELOITTE);
        System.out.println(s3==DELOITTE);
    }
}
```
* What is a *Java Interface* ?
* Does an interface `extends` or `implements` another interface ?
* What is a *Java Abstract Class* ?
* Does a *Java Abstract Class* `extends` or `implements` another *Java Abstract Class* ?
* Explain the usage of the `default` keyword (Java 8 onwards).
* With the introduction of the `default` keyword are there any reasons to use *Abstract Classes* instead of *Interfaces* ?
* **Unchecked Exceptions** vs. **Checked Exceptions**.
* What are the differences between **Exceptions** and an **Errors** ? Are there any similitudes ?
* Name 3 **Unchecked Exceptions**.
* Name 3 **Checked Exceptions**.
* What are **Java Annotations** ?

## Algorithms and Data Structures / Collections / Generics

* Explain the **O(n) Notation** (Big O).
* How does a **Stack** data-structure works ? Are there any standard Java Stack implementations ?
* How does a **Queue** data-structure works ? Are there any standard Java Queue implementations ?
* How can you recursively calculate the sum of numbers from a `List<Integer>` (don't use for/do/while loops).
* What is tail recursion ?
* Why is not possible to use primitives as generic types ?
* Explain the concept of **Type Erasure**.
* Explain the following data structures: *List*, *Map*, *Queue*, *Set*.
* Name a few implementations for each interface:

| List<T>    | Set<T>     | Map<K,V>     | Queue<T>  |
| ------  | ------  | ------  | ------ |
|         |         |         |        |
|         |         |         |        |
|         |         |         |        |
|         |         |         |        |

* What is the output if we run the following code:
```java
import java.util.HashSet;
import java.util.Set;

class A {
    @Override
    public int hashCode() {
        return 0;
    }
}

public class HashTest {
    public static void main(String[] args) {
        Set<A> set = new HashSet<>();

        set.add(new A());
        set.add(new A());
        set.add(new A());

        System.out.println(set.size());
    }
}
```
* Explain how a **HashMap** is implemented. What is the relationship between *equals()* and *hashCode()*.
* What are *hash collisions* ?
* What are the operations for which a **LinkedList** is more efficient than an **ArrayList** ?
* What is the difference between **CopyOnWriteArrayList**, **Vector** and **ArrayList** ?
* What are the key differences between a **HashMap** and **ConcurrentHashMap** ?
* How does a **WeakHashMap** works ? What are the main differences between a **WeakHashMap** and a **HashMap** ?
* Does a **Set** accepts `null` as an element ?
* What is the difference between an `Iterator` and `ListIterator` ?
* Are there any **Immutable** Collection Classes ?
* What is a **RingBuffer** ?
* What happens if we run the following code:
```java
public static void main(String[] args) {
        List<String> list = new LinkedList<>();

        list.add("A");
        list.add("C");
        list.add("D");

        Iterator<String> it = list.iterator();

        System.out.println(it.next());

        list.add(1, "B");
        
        System.out.println(it.next());
        System.out.println(it.next());
        System.out.println(it.next());
}
```

### Streams and Lambdas

* What is a **Functional Interface** ?
* Can you please explain what is a **Predicate**, **Consumer**, **Function**, **Supplier** ?
* What is the difference between a **Stream** and an **Iterator** ?
* Using the `filter()` method write a method that returns only the positive numbers from a `List<Integer>`.
* What is a `parallelStream()` ? How is different from a standard `stream()` ?
* Find out the max element from a `List<Integer>` using the `reduce()` method.
* Find out the sum of elements from a `List<Integer>` using the `reduce()` method.
* What is the output if we run the following code:
```java
    public static void main(String[] args) {
        final List<String> l = new LinkedList<>();

        l.add("A");
        l.add("B");
        l.add("C");

        l.stream().forEach(e -> {
            l.add("Z");
            System.out.println(e);
        });
    }
```
* What is the output if we run the following code: 
```java
    public static void main(String[] args) throws InterruptedException {

        List<String> list = new LinkedList<>();

        list.add("A");
        list.add("B");
        list.add("C");
        list.add("D");
        list.add("E");
        list.add("F");
        list.add("G");
        list.add("H");

        ListIterator<String> iterator = list.listIterator();

        for (int i = 0; i < list.size(); i++) {
            CompletableFuture.runAsync(() -> System.out.println(iterator.next()));
        }

        Thread.sleep(2000);
    }
```

### Threads & Async

* What is a Thread ?
* Is the `++` operator thread-safe ?
* How can we implement a Thread ?
* How *synchronized* keyword works ?
* How is the method `thread.join()` working ?
* Explain the concept of **Thread Starvation** ?
* Explain the concept of **Thread Pool** ?
* What can you tell about the **Executor Interface** ?
* What is a *Semaphore* in Java ?
* What is the output if we execute the following code:
```java
    public static void main(String[] args) throws ExecutionException, InterruptedException {

        CompletableFuture<Void> cf1 = CompletableFuture.runAsync(() -> {
            System.out.println("B");
        });

        CompletableFuture<Void> cf2 = CompletableFuture.runAsync(() -> {
            System.out.println("A");
        });

        cf1.get();
        cf2.get();
    }
```    

### Creational, Structural and Behavioral Design Patterns

* What is a **Design Pattern** ?
* What is a **Creational Design Pattern** ?
* Pick two or three **Creational Design Patterns** from the following list and describe how you've used them in your code: *Abstract Factory*, *Builder*, *Factory Method*, *Prototype*, *Singleton* ?
* What is a **Structural Design Pattern** ?
* Pick two or three **Structural Design Patterns** from the following list and describe how you've used them in your code: *Adapter*, *Decorator*, *Facade*, *Flyweight*, *Proxy*?
* What is a **Behavioral Design Pattern** ?
* Pick two or three **Behavioral Design Patterns** from the following list and describe how you've used them in your code: *Chain Of Responsability*, *Command*, *Iterator*, *Mediator*, *Memento*, *Observer*, *Visitor*

### Spring

* Explain the concept of *Inversion of Control*. What is the **Spring IoC Container** ?
* Explain the concept of *Dependency Injection* (in Spring).
* What are the main advantages and disadvantages for *setter dependency injection* vs *constructor dependency injection* ?
* What is a **Spring Bean** ?
* What are the main **Spring Bean Scopes** ? Explain `singleton`, `prototype`, `request`, `session`, `global session`.
* What are the **Spring Stereotyping Annotations** ? Explain the differences between: `@Component`, `@Controller`, `@Repository`, `@Service`.
* Explain how the following Spring Annotations are working: `@Autowired`, `@Qualifier`, `@Required`.
* Explain how the `@Async` annotations functions.
* Explain the concept of **Spring Profiles**.
* What is **Spring Boot** ? Give example of a Scenario where you would propose to use **Spring Boot** ?
* What is **Spring Data** ? Give example of a Scenario where you would propose to use **Spring Data** ?
* What is **Spring Integration** ? Give example of a Scenario where you would propose to use **Spring Integration** ?
* What is **Spring Batch** ? Give example of a Scenario where you would propose to use **Spring Batch** ?
* What is **Spring Security** ? Give example of a Scenario where you would propose to use **Spring Security** ?

### Generic WEB

* What is **JWT** ? How does **JWT** works ?
* Where is recommended to store **JWT** tokens received from the Server on the client-side ?
* What are the main HTTP verbs ?
* What is the difference between **POST** and **PUT** ?
* What is the difference between **POST** and **PATCH** ?
* What is the difference between **POST** and **GET** ?
* You have to develop a *REST API* for a book store. This API needs to implement CRUD-like operations. How would you design the API ?

| Operation | HTTP VERB | ENDPOINT |
| --------- | --------- | -------- |
| Add a book | | |
| Remove a book | | |
| List books with pagination | | |
| Edit a book | | |
| Get info for a book | | |

### SQL

*Given the following SQL table:*

| id | full_name | mng_id |
| -- | --------- | ------ |
| 100 | Patrick Read | 101 |
| 101 | Bradley Hayes | `null` |
| 102 | Kieran Bennett | 101 |
| 103 | George Barnes | 101 |
| 104 | Alex Griffiths | 102 |
| 105 | Issac Jacobs | 102 |
| 106 | Will Mack | 104 |

*Write an SQL query that returns the following result:*

| id | full_name | mng_full_name |
| -- | --------- | ------------- |
| 100 | Patrick Read | Bradley Hayes |
| ... | ............ | ............. |

*Write an SQL query that returns one row containing the manager with the most direct subalterns.*

### Generic Questions
* From a protocol perspective what is the difference between **UDP** and **TCP** ? 
* What library would use to write a Scheduler in Java ?
* What are the main **Maven** alternatives ?
* What are the main **JUnit** alternatives ?
* How is **Mockito** used ? Are there any other alternatives to **Mockito**
* What is **Continuous Integration** (CI) ?
* Name other **JVM**-based languages ?
* What is **Functional Programming** ? Can you give a few examples of Functional Programming languages ?

### Exercises

#### Pangrams (Simple)

Roy wanted to increase his typing speed for programming contests. So, his friend advised him to type the sentence "The quick brown fox jumps over the lazy dog" repeatedly, because it is a pangram. (Pangrams are sentences constructed by using every letter of the alphabet at least once.)
After typing the sentence several times, Roy became bored with it. So he started to look for other pangrams.
Given a sentence s, tell Roy if it is a pangram or not.

**Input Format**
Input consists o a string s.
Example:
```
We promptly judged antique ivory buckles for the next prize
```

**Output Format**
Output a line containing “pangram” if s is pangram, otherwise print “not pangram”.
Example:
```
pangram
```

#### Balanced Parentheses (Medium)

Given a sequence consisting of parentheses, determine whether the expression is balanced.
A sequence of parentheses is balanced if every open parentheses can be paired uniquely with a closed parentheses that occurs after the former. Also, the interval between them must be balanced. You will be given three types of parentheses: (, {, and [.


```
{[()]} - This is a balanced parentheses.
{[(])} - This is not a balanced parentheses.
```

Example:

**Input**
```
3
{[()]}
{[(])}
{{[[(())]]}}
```

**Ouput**
```
YES
NO
YES
```
