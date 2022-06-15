# Java Interview Questions

This is a Collection of Computer Science, Java and SQL questions I use for the interviews. 
Feel free to propose new questions, contributions are open to everyone.

* [General Questions](#general-questions)
* [OOP Questions](#oop-questions)
* [Algorithms and Data Structures / Collections / Generics](#algorithms-and-data-structures--collections--generics)
* [Streams And Lambdas](#streams-and-lambdas)
* [Threads](#threads--async)
* [Creational, Structural and Behavioral Design Patterns](#creational-structural-and-behavioral-design-patterns)
* [Java EE](#java-ee)
* [Spring](#spring)
* [Microservices](#microservices)
* [Generic WEB](#generic-web)
* [SQL](#sql)
* [Exercises](#exercises)

## General Questions

* What are the key memory segments inside JVM ? Explain **HEAP**, **STACK**.
* What is a **Memory Leak** ? How can a memory leak appear in **garbage collected** language ? Is it even possible ?
* Is Java *pass-by-value* or *pass-by-reference* ?
* Write a Java method to swap the values of two integer values (*Is it possible ?*):
```Java
public void swap(int x, int y) { /** code here **/ }
```
* What is the output of the following code:
```java
public class PasserBy {
    public static void swap(int x, int y) {
        int tmp = x;
        x = y;
        y = tmp;
    }
    public static void main(String[] args) {
        int i = 1, j = 2;
        swap(i, j);
        System.out.println(i + " " + j);
    }
}
```
* What is a *primitive type* in Java ? What are the main *primitive types* ?
* What is *auto-boxing/unboxing* ?
* What is *implicit casting* ? 
* What is *explicit casting* ?
* When developing an e-commerce site, what is the recommended type to use for the *price* if performance is not an issue. What if performance is an issue ?
* Explain the usage of the following keyword: `final`.
* Can you give example of a `final` class from the Java Standard library ?
* What is the difference between `==` and `equals()` ?
* What is the output if we execute the following code:
```Java
public class Ternary {
    public static void main(String[] args) {

        Integer x = 1987;
        Integer y = 1987;
        System.out.println(x == y ? "A" : "B");

        x = 10;
        y = 10;
        System.out.println(x == y ? "A" : "B");
    }
}
```
* Explain the usage of the following keywords: `strictfp`, `native`.

## OOP Questions

* What is a **constructor** ?
* What is the **default constructor** ?
* Explain the concept of *Inheritance*. Why doesn't Java supports the concept of *Multiple Inheritance* ?
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
* Explain of the concept of **Marker Interface**. 
* Explain the concept of **Serialization**.
* Explain how the keyword **transient** works. What fields would you mark as transient in a class ?
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
* What is a *Java Interface* ?
* Does an interface `extends` or `implements` another interface ?
* What is a *Java Abstract Class* ?
* Does a *Java Abstract Class* `extends` or `implements` another *Java Abstract Class* ?
* Explain the usage of the `default` keyword (Java 8 onwards).
* With the introduction of the `default` keyword are there any reasons to use *Abstract Classes* instead of *Interfaces* ?
* **Unchecked Exceptions** vs. **Checked Exceptions**.
* What are the differences between **Exceptions** and an **Errors** ? Is there any similitude between the two ?
* Name 3 **Unchecked Exceptions**.
* Name 3 **Checked Exceptions**.
* What are **Java Annotations** ?
* What are the **SOLID** principles and how do they apply to Java ? Explain:
    * **S**ingle-Responsibility;
    * **O**pen-Closed
    * **L**iskov Substitution
    * **I**nterface Segregation
    * **D**ependency Inversion
    
## Algorithms and Data Structures / Collections / Generics

* Explain the **O(n) Notation** (Big O).
* How does a **Stack** data-structure works ? Are there any standard Java Stack implementations ?
* How does a **Queue** data-structure works ? Are there any standard Java Queue implementations ?
* How does a **Binary Tree** data-structure works ? 
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

* The following code highlights the difference between various **Map** implementations. What is the output if we run it (`impossible to say`:
```java
public class Maps {
    public static void main(String[] args) {
        Map<String, Integer> map1, map2, map3;

        map1 = Map.of(
                "A", 0,
                "D", 1,
                "B", 2,
                "C", 3
        );

        map2 = new LinkedHashMap<>(map1);
        map3 = new TreeMap<>(map1);

        System.out.println(map2);
        System.out.println(map3);
    }
}
```
* Explain how a **HashMap** is implemented. What is the relationship between *equals()* and *hashCode()*.
* Given the following code what is the Output (`3`):
```java
public class Sets {
    public static void main(String[] args) {
        Set<CustomData> set = new HashSet<>();
        CustomData customData = new CustomData();

        set.add(customData);
        set.add(customData);
        set.add(new CustomData());
        set.add(new CustomData());

        System.out.println(set.size());
    }
}
class CustomData {
    @Override
    public int hashCode() {
        return 0;
    }
}
```
* What are *hash collisions* ?
* What are the operations for which a **LinkedList** is more efficient than an **ArrayList** ?
* What is the difference between **CopyOnWriteArrayList**, **Vector** and **ArrayList** ?
* What are the key differences between a **HashMap** and **ConcurrentHashMap** ?
* How does a **WeakHashMap** works ? What are the main differences between a **WeakHashMap** and a **HashMap** ?
* Does a **Set** accepts `null` as an element ?
* What is the difference between an `Iterator` and `ListIterator` ?
* Are there any **Immutable** Collection Classes ?
* What is a **RingBuffer** ?
* What is a **SkipList** ? 
* What happens if we run the following code:
```java
class Test {
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
}
```

### Streams and Lambdas

* What is a **Functional Interface** ?
* What happens if we try to run the following code:
```java
public class Lambada {

    private String name = "Agent Smith";

    public void doLambda() {
        Doer doer = () -> {
            System.out.println(this.name);
        };
        doer.doAction();
    }

    public void doAnonymous() {
        Doer doer = new Doer() {
            @Override
            public void doAction() {
                System.out.println(this.name);
            }
        };
        doer.doAction();
    }

    public static void main(String[] args) {
        Lambada lambada = new Lambada();
        lambada.doLambda();
        lambada.doAnonymous();
    }
}

@FunctionalInterface
interface Doer {
    void doAction();
}
```
* Can you please explain what is a **Predicate**, **Consumer**, **Function**, **Supplier** ?
* What is the difference between a **Stream** and an **Iterator** ?
* Using the `filter()` method write a method that returns only the positive numbers from a `List<Integer>`.
* What is a `parallelStream()` ? How is it different from a standard `stream()` ?
* Find out the max element from a `List<Integer>` using the `reduce()` method.
* Find out the sum of elements from a `List<Integer>` using the `reduce()` method.
* What is the output if we run the following code:
```java
class Test {
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
* Explain the concept of *Future* and *CompletableFuture*. What is the main difference between a *Future* and a *CompletableFuture* ?
* What is the output if we execute the following code:
```java
class Test {
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
* Do you know any other libraries that provide *Dependency Injection* features ?
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

### Microservices

* What are the advantages and disadvantages of using a Microservice based architecture ?
> **Advantages**: Improved Scalability, Fault Isolation, Localised Complexity, Increased Agility, Simplified Debugging and Maintenance, Smaller Development Teams, etc.
>
> **Disadvantages**: Complexity (e.g.: Dependencies), Requires accurate pre-planning, End-to-end testing is difficult, Complex deployment procedures, etc. 
* What is an API Gateway ? What "problem" does it solve ?
* What is a Circuit Breaker ? What "problem" does it solve ? How is the `@HystrixCommand` annotations works in a Spring Cloud implementation?
* Explain the concept of **Observability** ?
    * What is the **Log Aggregation** pattern ? What problem does it solve ? Can you give examples of **Log Aggregation** solutions (e.g.: AWS Cloud Watch) ?
    * What is the **Application Metrics** pattern ? What problem does it solve ? What are the two models of aggregating metrics (push. vs pull) ? Can you give examples of **Application Metrics** solutions ?
    * What is the **Distributed Tracing** pattern ?
* You have applied the **Database per Service** pattern, so each microservice has its own database. Some business transactions are spanning over multiple services, so you need a mechanism to implement transaction that Span Services. How to implement transaction that span services ? (e.g.: **Saga Pattern**)
* You have applied the **Database per Service** pattern, so each microservice has its own database. Additionally, you have implemented the **Event Sourcing** Pattern and data is no longer easily queryable. How to implement a query that retrieves data from multiple services in a micorservice architecture ? (e.g.: Command Query Responsibility Segregation - CQRS).    

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
* What is **ACID** standing for ? Explain:
    * **A**tomicity
    * **C**onsistency
    * **I**solation
    * **D**urability 

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
* What is a **DSL** ? Can you write a **DSL** in Java ? 
* What Quality Control tools do you know ? What is a Quality Gate ?

### Exercises

#### Find the longest substring(s) that doesn't contains any letter duplicates from a string

Input examples: `"abcsadjnii"`

#### The solitary integer (Simple)

Given a list of integers `LIST = [1,4,3,3,2,5,1,2,5,7,7, ...]` with size `N`.

We know `LIST` contains only duplicated numbers (numbers that appear twice) except ONE integer which is called *The Solitary Integer*.

Write an efficient algorithm that will determine this integer ?

Can you solve the exercise in O(N) ?

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

