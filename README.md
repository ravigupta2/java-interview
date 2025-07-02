# Part 1: Core Java (Basics + OOPs)

### 1. What are the main principles of Object-Oriented Programming (OOP)?
- **Encapsulation**: Wrapping data and code together.
- **Abstraction**: Hiding internal details and showing only essential features.
- **Inheritance**: Acquiring properties and behaviors of another class.
- **Polymorphism**: Ability to take multiple forms (method overloading/overriding).

---

### 2. Difference between `==` and `.equals()` in Java?
- `==` checks reference (memory address)
- `.equals()` checks object content

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);       // false
System.out.println(a.equals(b));  // true
```

---

### 3. What is method overloading?
Same method name with different parameters (compile-time polymorphism).

```java
void print(String name) {}
void print(int age) {}
```

---

### 4. What is method overriding?
Sub-class provides specific implementation for parent class method.

```java
class Animal {
    void sound() { System.out.println("Generic sound"); }
}

class Dog extends Animal {
    @Override
    void sound() { System.out.println("Bark"); }
}
```

---

### 5. Can a class be both `final` and `abstract`?
No. `abstract` requires subclassing; `final` prohibits it.

---

### 6. Can interfaces have concrete methods?
Yes, since Java 8, interfaces can have `default` and `static` methods.

```java
interface Test {
    default void hello() { System.out.println("Hi"); }
}
```

---

### 7. What is a constructor?
A special method to initialize objects. Same name as class, no return type.

---

### 8. Difference between constructor and method?

| Feature       | Constructor              | Method                   |
|---------------|---------------------------|---------------------------|
| Name          | Same as class             | Any name                  |
| Return type   | None                      | Must have a return type   |
| Purpose       | Initializes object        | Executes logic            |

---

### 9. Can we overload constructors?
Yes.

```java
public class Person {
    Person() {}
    Person(String name) {}
}
```

---

### 10. What is the use of `this` keyword?
Refers to the current class object.

```java
this.name = name;
```

---

### 11. What is inheritance in Java?
One class inherits the fields/methods of another class using `extends`.

---

### 12. What are access modifiers?
- `private`: within class
- `default`: within package
- `protected`: package + subclass
- `public`: accessible everywhere

---

### 13. Can we extend multiple classes?
No, Java does not support multiple inheritance via classes. Use interfaces.

---

### 14. What is static keyword?
Used to define class-level variables/methods.

---

### 15. Can static methods be overridden?
No, they can be hidden (method hiding).

---

### 16. Can abstract class have a constructor?
Yes, it is called during subclass instantiation.

---

### 17. Difference between interface and abstract class?

| Feature         | Interface        | Abstract Class     |
|------------------|------------------|---------------------|
| Methods          | Only abstract (Java 7), default/static (Java 8+) | Can have both        |
| Multiple Inherit | Yes              | No                  |
| Constructors     | No               | Yes                 |

---

### 18. What is encapsulation?
Wrapping variables and methods into a single unit (class), often with private fields and public getters/setters.

---

### 19. What is polymorphism?
A concept allowing one action in different forms: overloading (compile time) and overriding (runtime).

---

### 20. What is a package?
A namespace that organizes classes and interfaces.

```java
package com.example;
```

---

### 21. Can a Java class be private?
Only inner/nested classes can be private.

---

### 22. What is a final class?
Cannot be extended.

```java
final class Utility {}
```

---

### 23. Can we create object of abstract class?
No. But we can use it via subclass.

---

### 24. What is type casting?
Converting one type into another.

```java
int x = (int) 10.5;
```

---

### 25. What is `super` keyword?
Used to refer to immediate parent class constructor or method.

---

### 26. Can we override private methods?
No. Private methods are not visible to subclass.

---

### 27. What is the default value of a reference variable?
`null`

---

### 28. Difference between instance and static variable?
- Instance: per object
- Static: shared across all instances

---

### 29. What is a nested class?
A class defined inside another class.

```java
class Outer {
    class Inner {}
}
```

---

### 30. Can a constructor be private?
Yes. Used in Singleton patterns.

```java
class Singleton {
    private Singleton() {}
}
```

---

✅ **End of Part 1 — 30 Questions Completed**

# Part 2: Java 8 Features (Streams, Lambdas, Functional Interfaces, Optional, Date API)

### 1. What are the major features introduced in Java 8?
- Lambda Expressions  
- Functional Interfaces  
- Streams API  
- Optional  
- Default and Static methods in interfaces  
- New Date and Time API

---

### 2. What is a lambda expression?
It provides a clear and concise way to represent a functional interface.

```java
(int a, int b) -> a + b
```

---

### 3. What is a functional interface?
An interface with exactly one abstract method.

```java
@FunctionalInterface
interface Calculator {
    int operate(int a, int b);
}
```

---

### 4. Give an example of using lambda with a custom functional interface:

```java
Calculator add = (a, b) -> a + b;
System.out.println(add.operate(5, 3)); // 8
```

---

### 5. What is the `Predicate<T>` interface?
Used to represent a boolean-valued function of one argument.

```java
Predicate<String> isLong = s -> s.length() > 5;
System.out.println(isLong.test("Hello")); // false
```

---

### 6. What is the `Function<T, R>` interface?
Represents a function that accepts one argument and produces a result.

```java
Function<String, Integer> length = str -> str.length();
```

---

### 7. What is the `Consumer<T>` interface?
Represents an operation that takes a single input argument and returns no result.

```java
Consumer<String> greet = name -> System.out.println("Hi " + name);
```

---

### 8. What is the `Supplier<T>` interface?
Represents a supplier of results with no input.

```java
Supplier<String> supplier = () -> "Java";
```

---

### 9. What is the Streams API?
Used to process collections of objects using a functional approach.

```java
List<String> names = Arrays.asList("Ram", "Shyam", "Mohan");
names.stream().filter(n -> n.startsWith("S")).forEach(System.out::println);
```

---

### 10. Difference between `map()` and `flatMap()` in streams?
- `map()` transforms each element into another.
- `flatMap()` flattens nested structure.

```java
List<List<String>> list = Arrays.asList(Arrays.asList("a"), Arrays.asList("b"));
list.stream().flatMap(Collection::stream).forEach(System.out::println);
```

---

### 11. How to sort a list using streams?

```java
list.stream().sorted().collect(Collectors.toList());
```

---

### 12. How to find the maximum element using streams?

```java
Optional<Integer> max = list.stream().max(Integer::compareTo);
```

---

### 13. What does `collect(Collectors.toList())` do?
Collects stream elements into a `List`.

---

### 14. What is the use of `Optional` in Java 8?
A container object to handle `null` values gracefully.

```java
Optional<String> name = Optional.ofNullable("Ravi");
System.out.println(name.orElse("Default"));
```

---

### 15. What is the purpose of `orElse()` and `orElseGet()` in Optional?
- `orElse()`: Returns default value if null.
- `orElseGet()`: Accepts a Supplier to lazily generate default value.

---

### 16. What is the use of `filter()` in streams?

```java
list.stream().filter(e -> e > 10).collect(Collectors.toList());
```

---

### 17. What does `distinct()` do in a stream?
Removes duplicate elements.

---

### 18. How to convert a list of strings to uppercase using streams?

```java
list.stream().map(String::toUpperCase).collect(Collectors.toList());
```

---

### 19. How to count elements in a stream?

```java
long count = list.stream().count();
```

---

### 20. How to skip and limit stream elements?

```java
list.stream().skip(2).limit(3).collect(Collectors.toList());
```

---

### 21. What is `reduce()` used for?

```java
int sum = list.stream().reduce(0, Integer::sum);
```

---

### 22. Can we use `forEach` on a stream?

```java
stream.forEach(System.out::println);
```

---

### 23. What is method reference in Java?

```java
list.forEach(System.out::println);
```

---

### 24. How to group by a property using streams?

```java
Map<String, List<Person>> groupByDept =
    list.stream().collect(Collectors.groupingBy(Person::getDepartment));
```

---

### 25. What is the new Date & Time API in Java 8?
`java.time` package introduced `LocalDate`, `LocalTime`, `LocalDateTime`, `Period`, etc.

---

### 26. How to get today’s date?

```java
LocalDate today = LocalDate.now();
```

---

### 27. How to add 5 days to a date?

```java
LocalDate future = LocalDate.now().plusDays(5);
```

---

### 28. How to get the difference between two dates?

```java
Period diff = Period.between(LocalDate.of(2022, 1, 1), LocalDate.now());
```

---

### 29. How to format a date?

```java
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd-MM-yyyy");
String formatted = LocalDate.now().format(formatter);
```

---

### 30. Can a stream be reused?
No, streams are single-use.

---

✅ **End of Part 2 — 30 Questions Completed**

# Part 3: Exception Handling & Multithreading

---

### 1. What is an exception?
An unwanted or unexpected event that disrupts the normal flow of a program.

---

### 2. What is the difference between `checked` and `unchecked` exceptions?

| Checked Exception       | Unchecked Exception       |
|-------------------------|---------------------------|
| Compile-time            | Runtime                   |
| Must be handled         | Optional to handle        |
| e.g., IOException       | e.g., NullPointerException|

---

### 3. What are commonly used exception classes?
- `NullPointerException`
- `ArrayIndexOutOfBoundsException`
- `IllegalArgumentException`
- `IOException`
- `SQLException`

---

### 4. How do you handle exceptions?

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

---

### 5. What is `finally` block?
Code inside `finally` is **always executed**, regardless of exception.

```java
try {
    // risky code
} catch (Exception e) {
    // handle
} finally {
    System.out.println("Cleanup");
}
```

---

### 6. Can we have multiple catch blocks?

```java
try {
    // risky code
} catch (IOException e) {
    // handle IO
} catch (Exception e) {
    // generic handler
}
```

---

### 7. Can we catch multiple exceptions in a single block?

```java
try {
    // code
} catch (IOException | SQLException e) {
    e.printStackTrace();
}
```

---

### 8. What is a custom exception?

```java
class MyException extends Exception {
    public MyException(String message) {
        super(message);
    }
}
```

---

### 9. What is `throw` vs `throws`?

| Keyword | Use                                     |
|---------|------------------------------------------|
| throw   | Used to throw an exception manually      |
| throws  | Declares exceptions a method may throw   |

```java
throw new IOException("File error");
public void read() throws IOException {}
```

---

### 10. Can we write `try` without `catch`?
Yes, but only with `finally`.

```java
try {
   // code
} finally {
   // cleanup
}
```

---

### 11. What is multithreading?
A process of executing multiple threads simultaneously for better CPU utilization.

---

### 12. What is a thread?
A lightweight process; smallest unit of CPU execution.

---

### 13. How to create a thread in Java?

**Method 1: Extend Thread**
```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Running");
    }
}
```

**Method 2: Implement Runnable**
```java
class MyTask implements Runnable {
    public void run() {
        System.out.println("Running");
    }
}
```

---

### 14. What is the difference between `start()` and `run()`?
- `start()` creates a new thread.
- `run()` runs in the current thread.

---

### 15. What is the lifecycle of a thread?

States: New → Runnable → Running → Blocked/Waiting → Terminated

---

### 16. What is synchronization?
A mechanism to control access to shared resources by multiple threads.

```java
synchronized void print() {
   // thread-safe block
}
```

---

### 17. What is the purpose of `volatile` keyword?
Tells the JVM that a variable may be modified by multiple threads and shouldn't be cached.

---

### 18. What is `join()` method?
Waits for a thread to finish its execution.

```java
t1.join();
```

---

### 19. What is `sleep()` method?
Pauses execution of the thread for a specific time.

```java
Thread.sleep(1000); // 1 second
```

---

### 20. Difference between `wait()` and `sleep()`?

| wait()            | sleep()              |
|-------------------|----------------------|
| Defined in Object | Defined in Thread    |
| Releases lock     | Doesn’t release lock |

---

### 21. What is `yield()` method?
Pauses the current thread to give others a chance to execute.

---

### 22. What is a daemon thread?
A low-priority background thread that ends when the main thread ends.

```java
t.setDaemon(true);
```

---

### 23. Can a thread be restarted?
No, once a thread is terminated, it cannot be restarted.

---

### 24. What is thread safety?
Ensuring that shared data is accessed by only one thread at a time.

---

### 25. What is the `ExecutorService`?

```java
ExecutorService service = Executors.newFixedThreadPool(5);
service.submit(() -> System.out.println("Running task"));
```

Used to manage and control thread pools.

---

✅ **End of Part 3 — 25 Questions Completed**

# Part 4: Collections Framework (Java)

---

### 1. What is the Java Collections Framework?
A set of classes and interfaces that implement commonly reusable data structures like List, Set, Map, Queue.

---

### 2. What is the difference between `ArrayList` and `LinkedList`?

| Feature     | ArrayList          | LinkedList           |
|-------------|--------------------|-----------------------|
| Access      | Fast (index-based) | Slow (traverse nodes) |
| Insert/Delete | Slow (shifting)    | Fast (node links)     |
| Memory      | Less overhead      | More overhead         |

---

### 3. Difference between `HashSet` and `TreeSet`?

| Feature   | HashSet        | TreeSet            |
|-----------|----------------|---------------------|
| Order     | No order       | Sorted (natural order) |
| Null      | Allows one null| Does not allow null |
| Performance | Faster        | Slower (O(log n))    |

---

### 4. What is the difference between `HashMap` and `Hashtable`?

| Feature     | HashMap         | Hashtable         |
|-------------|------------------|-------------------|
| Thread-safe | No               | Yes               |
| Nulls       | 1 null key, many null values | None allowed |
| Performance | Faster           | Slower            |

---

### 5. Difference between `List`, `Set`, and `Map`?

| Collection | Duplicates | Order Maintained | Key-Value |
|------------|------------|------------------|-----------|
| List       | Yes        | Yes              | No        |
| Set        | No         | Depends          | No        |
| Map        | Keys No, Values Yes | Depends     | Yes       |

---

### 6. How does `HashMap` work internally?
It uses an array of buckets and stores entries in a linked list or tree (Java 8+). Hash function determines the index.

---

### 7. What is the initial capacity and load factor in HashMap?
- Default capacity = 16  
- Default load factor = 0.75  
- Capacity × Load Factor = threshold to resize

---

### 8. How to iterate over a `Map`?

```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

---

### 9. How to sort a list of integers?

```java
Collections.sort(list);
```

---

### 10. How to sort a list of objects by a field?

```java
Collections.sort(employeeList, Comparator.comparing(Employee::getName));
```

---

### 11. What is the difference between `Comparable` and `Comparator`?

| Feature      | Comparable         | Comparator              |
|--------------|---------------------|--------------------------|
| Interface    | `compareTo()`       | `compare()`              |
| Order        | Natural order       | Custom order             |
| Modify Class | Yes (implements)    | No (external logic)      |

---

### 12. What is the difference between `ArrayList` and `Vector`?

- `ArrayList` is not synchronized (faster)
- `Vector` is synchronized (thread-safe)

---

### 13. What are `Queue` and `Deque`?
- **Queue**: FIFO structure (e.g., LinkedList, PriorityQueue)  
- **Deque**: Double-ended queue (can insert/remove from both ends)

---

### 14. What is a `PriorityQueue`?

A queue that orders elements using natural ordering or a custom comparator.

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();
pq.add(5);
pq.add(1);
System.out.println(pq.poll()); // 1
```

---

### 15. What is a `Stack` in Java?

LIFO data structure.

```java
Stack<Integer> stack = new Stack<>();
stack.push(10);
System.out.println(stack.pop()); // 10
```

---

### 16. How to make a `Collection` thread-safe?

```java
List<String> syncList = Collections.synchronizedList(new ArrayList<>());
```

---

### 17. What is `fail-fast` and `fail-safe`?

- **Fail-fast**: Throws `ConcurrentModificationException` (e.g., ArrayList, HashMap)
- **Fail-safe**: Works on a copy, no exception (e.g., ConcurrentHashMap)

---

### 18. How to convert a list to a set?

```java
Set<String> set = new HashSet<>(list);
```

---

### 19. How to remove duplicates from a list?

```java
List<String> unique = list.stream().distinct().collect(Collectors.toList());
```

---

### 20. What is the difference between `LinkedHashMap` and `HashMap`?

- `LinkedHashMap` maintains insertion order  
- `HashMap` does not

---

### 21. What is `TreeMap`?

A `Map` that stores keys in **sorted (natural)** order.

---

### 22. Can we store null keys and values in `Map`?
- HashMap: One null key, many null values  
- Hashtable: No nulls

---

### 23. How to find frequency of elements in a list?

```java
Map<String, Long> freq = list.stream()
    .collect(Collectors.groupingBy(Function.identity(), Collectors.counting()));
```

---

### 24. How to reverse a list?

```java
Collections.reverse(list);
```

---

### 25. How to shuffle elements randomly?

```java
Collections.shuffle(list);
```

---

✅ **End of Part 4 — 25 Questions Completed**

# Part 5: Spring Core (Dependency Injection, Bean Lifecycle, Annotations)

---

### 1. What is the Spring Framework?
A lightweight, open-source framework for Java enterprise development that provides comprehensive infrastructure support including **Dependency Injection**, **Aspect-Oriented Programming**, and **transaction management**.

---

### 2. What is Dependency Injection (DI)?
A design pattern where objects receive their dependencies from an external source instead of creating them internally.

---

### 3. What is Inversion of Control (IoC)?
IoC is the principle where the control of object creation and lifecycle is given to the Spring container.

---

### 4. Difference between BeanFactory and ApplicationContext?

| Feature         | BeanFactory        | ApplicationContext       |
|-----------------|--------------------|---------------------------|
| Lazy Init       | Yes                | No (by default)           |
| Advanced Features | No                | Yes (AOP, events, etc.)   |
| Usage           | Lightweight apps   | Enterprise applications   |

---

### 5. What are the types of Dependency Injection in Spring?
- **Constructor Injection**  
- **Setter Injection**  
- **Field Injection (using @Autowired)**

---

### 6. How do you define a bean in XML?

```xml
<bean id="engine" class="com.car.Engine"/>
```

---

### 7. What is the use of `@Component` annotation?

Marks a class as a Spring-managed component (bean).

```java
@Component
public class Engine {}
```

---

### 8. Difference between `@Component`, `@Service`, `@Repository`, `@Controller`?

- All are specializations of `@Component`
- `@Service`: business logic layer
- `@Repository`: data access layer + exception translation
- `@Controller`: MVC controller

---

### 9. How to enable annotation-based configuration?

```java
<context:component-scan base-package="com.example"/>
```

or in Java config:

```java
@ComponentScan("com.example")
```

---

### 10. What is `@Autowired`?

Injects dependencies automatically by type.

```java
@Autowired
private Engine engine;
```

---

### 11. Can you inject by constructor with `@Autowired`?

Yes.

```java
@Autowired
public Car(Engine engine) {
    this.engine = engine;
}
```

---

### 12. What is `@Qualifier`?

Used when multiple beans of same type exist.

```java
@Autowired
@Qualifier("dieselEngine")
private Engine engine;
```

---

### 13. What is bean lifecycle in Spring?

1. Instantiation  
2. Populate properties  
3. `@PostConstruct`  
4. `InitializingBean.afterPropertiesSet()`  
5. Bean is ready  
6. `@PreDestroy`  
7. `DisposableBean.destroy()`

---

### 14. What are bean scopes in Spring?

- `singleton` (default)  
- `prototype`  
- `request`  
- `session`  
- `application`

---

### 15. What is the default scope of Spring beans?
**singleton**

---

### 16. How to define a prototype-scoped bean?

```java
@Scope("prototype")
@Component
public class Task {}
```

---

### 17. What is `@Configuration`?

Indicates that a class contains Spring bean definitions (used for Java-based config).

```java
@Configuration
public class AppConfig {}
```

---

### 18. What is `@Bean` annotation?

Used inside `@Configuration` to define beans manually.

```java
@Bean
public Engine engine() {
    return new Engine();
}
```

---

### 19. Can we use Spring without XML?
Yes, using **Java-based configuration** with `@Configuration`, `@ComponentScan`, and `@Bean`.

---

### 20. What is `@Value` used for?

Injects values from properties files.

```java
@Value("${db.url}")
private String url;
```

---

### 21. What is the use of `@PropertySource`?

Used to load external `.properties` files.

```java
@PropertySource("classpath:application.properties")
```

---

### 22. What is the role of `Environment` in Spring?

Used to access properties dynamically.

```java
@Autowired
Environment env;
String url = env.getProperty("db.url");
```

---

### 23. What is AOP in Spring?

Aspect-Oriented Programming – separates cross-cutting concerns like logging, transactions.

---

### 24. Common AOP annotations?

- `@Aspect`  
- `@Before`  
- `@After`  
- `@Around`  
- `@Pointcut`

---

### 25. What is a proxy in Spring?

An object created by Spring to wrap a bean and apply AOP functionalities.

---

### 26. What is `@Lazy`?

Delays the creation of a bean until it’s actually needed.

```java
@Lazy
@Bean
public Engine engine() {}
```

---

### 27. What is the use of `@Primary`?

Marks a bean as default when multiple candidates exist.

```java
@Primary
@Bean
public Engine petrolEngine() {}
```

---

### 28. What is `ApplicationContextAware`?

Allows a bean to access the `ApplicationContext`.

```java
public class MyBean implements ApplicationContextAware {
    public void setApplicationContext(ApplicationContext ctx) {}
}
```

---

### 29. Can we inject a collection in Spring?

Yes.

```java
@Autowired
private List<Service> services;
```

---

### 30. How to handle circular dependencies in Spring?

Avoid field injection. Use constructor injection or `@Lazy`.

---

✅ **End of Part 5 — 30 Questions Completed**

# Part 6: Spring Boot (Starters, Autoconfiguration, REST, Properties)

---

### 1. What is Spring Boot?
A Spring-based framework that makes it easier to create stand-alone, production-grade Spring applications with minimal configuration.

---

### 2. Key Features of Spring Boot?
- Auto Configuration  
- Embedded Web Server (Tomcat/Jetty)  
- Starter Dependencies  
- Spring Boot CLI  
- Actuator for Monitoring  

---

### 3. What is `@SpringBootApplication`?

A combination of:
- `@Configuration`
- `@EnableAutoConfiguration`
- `@ComponentScan`

```java
@SpringBootApplication
public class MyApp {
    public static void main(String[] args) {
        SpringApplication.run(MyApp.class, args);
    }
}
```

---

### 4. What is auto-configuration?

Spring Boot automatically configures your application based on the dependencies present in the classpath.

---

### 5. What are starter dependencies?

Pre-defined Maven/Gradle dependencies that bundle common dependencies.

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

---

### 6. How to create a REST API using Spring Boot?

```java
@RestController
public class UserController {

    @GetMapping("/users")
    public List<User> getUsers() {
        return userService.getAll();
    }
}
```

---

### 7. What is `@RestController`?

Combines `@Controller` and `@ResponseBody` to return JSON/XML directly.

---

### 8. What is the use of `@GetMapping`, `@PostMapping`, etc.?

Shorthand annotations for handling HTTP methods.

---

### 9. What is `application.properties` used for?

Configuration of the application like port, database, logging, etc.

```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/test
```

---

### 10. How to use YAML instead of `.properties`?

Use `application.yml`:

```yaml
server:
  port: 8081
```

---

### 11. How to change the default port?

```properties
server.port=9090
```

---

### 12. What is Spring Boot DevTools?

A dependency that provides hot swapping, automatic restart, and more for faster development.

---

### 13. How do you connect Spring Boot with MySQL?

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
```

---

### 14. What is `@EnableAutoConfiguration`?

Tells Spring Boot to auto-configure based on classpath and beans defined.

---

### 15. How to handle exceptions in REST APIs?

Use `@ControllerAdvice` + `@ExceptionHandler`.

```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<?> handleNotFound(ResourceNotFoundException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(ex.getMessage());
    }
}
```

---

### 16. What is `@RequestParam` and `@PathVariable`?

```java
@GetMapping("/user")
public User getUser(@RequestParam String name) {}

@GetMapping("/user/{id}")
public User getUserById(@PathVariable int id) {}
```

---

### 17. What is Actuator in Spring Boot?

Provides production-ready endpoints to monitor app (e.g., `/actuator/health`).

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

---

### 18. How to enable CORS in Spring Boot?

```java
@CrossOrigin(origins = "*")
@GetMapping("/api")
public String hello() {
    return "Hi";
}
```

---

### 19. What is the default embedded server?

**Tomcat**

---

### 20. How to change the embedded server?

In `pom.xml` remove Tomcat and add Jetty/Undertow.

---

### 21. What is `@RequestBody` used for?

To bind the body of the HTTP request to a method parameter.

```java
@PostMapping("/user")
public ResponseEntity<User> addUser(@RequestBody User user) {}
```

---

### 22. How to enable H2 in-memory DB?

Add dependency + set properties:

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
```

---

### 23. What is the default context path?

`/` (root). Can be changed using:

```properties
server.servlet.context-path=/api
```

---

### 24. What is `CommandLineRunner`?

Executes code after the application starts.

```java
@Bean
CommandLineRunner run(UserService service) {
    return args -> {
        service.loadUsers();
    };
}
```

---

### 25. What is the `main()` method in Spring Boot?

Acts as the entry point and triggers the Spring Boot auto-configuration.

---

### 26. How to enable logging in Spring Boot?

Default logging via Logback. Configure in `application.properties`.

```properties
logging.level.org.springframework=DEBUG
```

---

### 27. How to deploy Spring Boot app as WAR?

- Extend `SpringBootServletInitializer`
- Package type: WAR in `pom.xml`

---

### 28. How to disable a specific auto-configuration?

Use `@SpringBootApplication(exclude = {DataSourceAutoConfiguration.class})`

---

### 29. What is `spring-boot-starter-parent`?

Provides default configurations like Java version, dependency versions, plugin management.

---

### 30. Can Spring Boot be used without Spring MVC?

Yes, for CLI apps, console utilities, or reactive APIs (using WebFlux).

---

✅ **End of Part 6 — 30 Questions Completed**

# Part 7: REST API (Spring Boot) + JSON Handling

---

### 1. What is a REST API?

REST (Representational State Transfer) is an architectural style that uses HTTP methods to perform CRUD operations on resources.

---

### 2. What are the main HTTP methods used in REST?

| Method | Description     |
|--------|-----------------|
| GET    | Read            |
| POST   | Create          |
| PUT    | Update (Replace)|
| PATCH  | Update (Partial)|
| DELETE | Delete          |

---

### 3. Difference between `@RestController` and `@Controller`?

- `@Controller` returns **view templates**
- `@RestController` returns **JSON/XML** (includes `@ResponseBody`)

---

### 4. How to send JSON request to a Spring Boot endpoint?

```http
POST /users
Content-Type: application/json

{
  "name": "Ravi",
  "email": "ravi@example.com"
}
```

---

### 5. How to map a JSON request body to a POJO?

```java
@PostMapping("/users")
public ResponseEntity<User> addUser(@RequestBody User user) {
    return ResponseEntity.ok(user);
}
```

---

### 6. How to return JSON in a response?

Spring Boot auto-converts Java objects to JSON using **Jackson**.

```java
@GetMapping("/user")
public User getUser() {
    return new User("Ravi", "ravi@example.com");
}
```

---

### 7. What is Jackson?

A popular library used by Spring Boot to serialize/deserialize Java objects to/from JSON.

---

### 8. What is `@JsonIgnore` used for?

To ignore a field during JSON serialization/deserialization.

```java
@JsonIgnore
private String password;
```

---

### 9. What is `@JsonProperty` used for?

To customize the property name in JSON.

```java
@JsonProperty("user_email")
private String email;
```

---

### 10. What does `ResponseEntity` do?

Allows full control over HTTP response (status, headers, body).

```java
return ResponseEntity.status(HttpStatus.CREATED).body(user);
```

---

### 11. What is the use of `@RequestParam` and `@PathVariable`?

```java
@GetMapping("/users")
public User getUser(@RequestParam String name) {}

@GetMapping("/users/{id}")
public User getUserById(@PathVariable Long id) {}
```

---

### 12. How do you handle empty/null responses?

```java
return user != null ? ResponseEntity.ok(user) : ResponseEntity.notFound().build();
```

---

### 13. Common HTTP status codes?

| Code | Meaning                  |
|------|---------------------------|
| 200  | OK                        |
| 201  | Created                   |
| 204  | No Content                |
| 400  | Bad Request               |
| 401  | Unauthorized              |
| 404  | Not Found                 |
| 500  | Internal Server Error     |

---

### 14. How to validate JSON input?

Use Bean Validation API:

```java
public class User {
    @NotNull
    private String name;

    @Email
    private String email;
}
```

Add `@Valid` in controller:

```java
@PostMapping("/users")
public ResponseEntity<?> saveUser(@Valid @RequestBody User user, BindingResult result) {}
```

---

### 15. How to handle global validation or JSON errors?

Use `@ControllerAdvice`:

```java
@ControllerAdvice
public class GlobalErrorHandler {
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<String> handleValidationErrors(MethodArgumentNotValidException ex) {
        return ResponseEntity.badRequest().body("Validation failed");
    }
}
```

---

✅ **End of Part 7 — 15 Questions Completed**

# Part 8: MySQL + Spring Data JPA

---

### 1. What is JPA?

**Java Persistence API (JPA)** is a specification for object-relational mapping (ORM) in Java. It maps Java objects to database tables.

---

### 2. What is Hibernate?

Hibernate is a popular JPA provider implementation used with Spring Boot to interact with relational databases.

---

### 3. What is Spring Data JPA?

A Spring module that simplifies JPA by reducing boilerplate code and providing built-in repository methods.

---

### 4. How to define a JPA entity?

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private String email;
}
```

---

### 5. What is `@Id` and `@GeneratedValue`?

- `@Id`: Marks the primary key  
- `@GeneratedValue`: Auto-generates the primary key using strategies like `IDENTITY`, `AUTO`, etc.

---

### 6. What is `CrudRepository`?

A Spring Data interface that provides CRUD methods like `save()`, `findById()`, `delete()`, etc.

---

### 7. What is `JpaRepository`?

Extends `CrudRepository` and adds pagination, sorting, and batch operations.

---

### 8. How to define a repository?

```java
public interface UserRepository extends JpaRepository<User, Long> {
}
```

---

### 9. How to write custom query methods?

Spring generates queries based on method names:

```java
List<User> findByName(String name);
List<User> findByEmailContaining(String keyword);
```

---

### 10. How to use `@Query` for custom SQL?

```java
@Query("SELECT u FROM User u WHERE u.name = :name")
List<User> findByNameCustom(@Param("name") String name);
```

---

### 11. How to make a native SQL query?

```java
@Query(value = "SELECT * FROM users WHERE name = :name", nativeQuery = true)
List<User> findByNameNative(@Param("name") String name);
```

---

### 12. What is `@Modifying` annotation?

Used to mark update/delete queries.

```java
@Modifying
@Query("UPDATE User u SET u.name = :name WHERE u.id = :id")
void updateName(@Param("id") Long id, @Param("name") String name);
```

---

### 13. What is the use of `@Transactional`?

Ensures that a method executes within a transaction boundary.

```java
@Transactional
public void updateSomething() {
    // logic
}
```

---

### 14. What is lazy vs eager loading?

- **Lazy**: Data loaded on demand  
- **Eager**: Data loaded immediately with parent

```java
@OneToMany(fetch = FetchType.LAZY)
private List<Order> orders;
```

---

### 15. What is `@OneToOne`?

Maps a one-to-one relationship.

```java
@OneToOne
@JoinColumn(name = "profile_id")
private Profile profile;
```

---

### 16. What is `@OneToMany` and `@ManyToOne`?

```java
@OneToMany(mappedBy = "user")
private List<Order> orders;

@ManyToOne
@JoinColumn(name = "user_id")
private User user;
```

---

### 17. How to handle bidirectional mapping?

Use `mappedBy` on the inverse side and `@JsonIgnore` to avoid infinite recursion.

---

### 18. How to enable MySQL in `application.properties`?

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
```

---

### 19. What is `ddl-auto` and its values?

Controls schema generation.

| Value   | Description                 |
|---------|-----------------------------|
| none    | No action                   |
| update  | Updates schema              |
| create  | Creates schema each time    |
| create-drop | Creates and drops on exit |

---

### 20. What is optimistic locking?

Uses versioning to prevent lost updates.

```java
@Version
private int version;
```

---

### 21. What is `EntityManager`?

The JPA interface for interacting with the persistence context.

---

### 22. Difference between `save()` and `saveAndFlush()`?

- `save()`: Persists and returns entity  
- `saveAndFlush()`: Flushes changes immediately to DB

---

### 23. How to sort query results?

```java
List<User> users = userRepository.findAll(Sort.by("name").ascending());
```

---

### 24. How to paginate query results?

```java
Page<User> page = userRepository.findAll(PageRequest.of(0, 10));
```

---

### 25. What is a composite primary key?

A key that consists of multiple fields.

```java
@IdClass(OrderId.class)
public class Order {
    @Id private Long userId;
    @Id private Long productId;
}
```

---

### 26. What is `@Embeddable` and `@Embedded`?

Used for embedding reusable value types in entities.

```java
@Embeddable
public class Address {
    private String city;
    private String state;
}
```

```java
@Embedded
private Address address;
```

---

### 27. What is `@Table` and `@Column`?

Customize table and column names.

```java
@Table(name = "users")
@Column(name = "user_email")
```

---

### 28. How to delete a record by ID?

```java
userRepository.deleteById(1L);
```

---

### 29. What is `Optional<User>` in `findById()`?

Represents a possibly-null return value, avoids `NullPointerException`.

---

### 30. How to insert initial data automatically?

Use `data.sql` or `CommandLineRunner` bean.

```sql
INSERT INTO users (name, email) VALUES ('Ravi', 'ravi@example.com');
```

---

✅ **End of Part 8 — 30 Questions Completed**

# Part 9: Final Practice Set (Java + Spring + JPA + REST + MySQL)

---

### 1. Explain how Spring handles dependency injection under the hood. What happens at runtime?

Spring uses reflection to instantiate beans and inject dependencies either through constructors, setters, or fields. The ApplicationContext container creates objects, resolves dependencies, and manages their lifecycle.

---

### 2. What's the difference between `@ComponentScan` and `@EntityScan`?

- `@ComponentScan`: Scans for Spring-managed components (`@Component`, `@Service`, etc.)
- `@EntityScan`: Tells Spring Boot where to scan for JPA entities (`@Entity`)

---

### 3. When would you use `@Transactional(readOnly = true)`?

For performance optimization in read operations where no data modification occurs. It avoids unnecessary locking and flushes.

---

### 4. How would you design a REST API to return paginated results for users?

```java
@GetMapping("/users")
public Page<User> getUsers(@RequestParam int page, @RequestParam int size) {
    return userRepo.findAll(PageRequest.of(page, size));
}
```

---

### 5. What's the difference between `@RequestParam` and `@PathVariable`?

- `@RequestParam`: For query parameters (`?id=5`)  
- `@PathVariable`: For URI template variables (`/user/5`)

---

### 6. Explain lazy vs eager loading using a real-world example.

In a User-Orders relationship:
- **Lazy**: Orders aren't loaded until accessed (`user.getOrders()`)
- **Eager**: Orders are loaded immediately when user is fetched

---

### 7. How would you implement a search filter in a Spring Data repository?

```java
List<User> findByNameContainingIgnoreCase(String name);
```

---

### 8. How would you validate incoming JSON data?

Using `@Valid` + validation annotations:

```java
public class User {
    @NotBlank
    private String name;

    @Email
    private String email;
}
```

---

### 9. What is the difference between PUT and PATCH?

- `PUT`: Replaces the entire resource  
- `PATCH`: Partially updates a resource

---

### 10. How would you expose only specific fields in a JSON response?

Use DTOs or Jackson annotations like `@JsonIgnore` or `@JsonView`.

---

### 11. What is the use of `@EnableJpaRepositories`?

Enables scanning of repository interfaces annotated with `@Repository`.

---

### 12. What happens if you forget `@Entity` on a model?

Spring Boot won't map it to a DB table — queries will fail silently or throw runtime exceptions.

---

### 13. How would you create a bidirectional OneToMany relationship?

```java
@Entity
class User {
    @OneToMany(mappedBy = "user")
    private List<Order> orders;
}

@Entity
class Order {
    @ManyToOne
    @JoinColumn(name = "user_id")
    private User user;
}
```

---

### 14. What is the default behavior of `findById()`?

Returns an `Optional<T>`, which can either hold the entity or be empty.

---

### 15. How do you handle multiple environments (dev, prod) in Spring Boot?

Use `application-dev.properties`, `application-prod.properties` and `spring.profiles.active=dev` in your config.

---

### 16. How do you secure REST endpoints?

- Spring Security  
- JWT tokens  
- Role-based access control using `@PreAuthorize`

---

### 17. What are some common mistakes in using `@Autowired`?

- Autowiring an interface without an implementation  
- Forgetting `@Component` on the class  
- Conflicts with multiple beans (resolve with `@Qualifier`)

---

### 18. How would you call a stored procedure using Spring Data JPA?

```java
@Procedure(name = "get_users_by_status")
List<User> getUsersByStatus(@Param("status") String status);
```

---

### 19. What does `CascadeType.ALL` mean?

It propagates all operations (persist, merge, remove, refresh, detach) from parent to child entity.

---

### 20. How can you expose health checks and metrics in Spring Boot?

Add Actuator dependency and visit endpoints like `/actuator/health`, `/actuator/metrics`.

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

---

✅ **End of Part 9 — Final 20 Questions Completed**
