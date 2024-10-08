# Spring and Spring Boot Annotations



### @Component : 
-   The `@Component` annotation in Spring is used to mark a class as a Spring bean.
- During the component scan, Spring Framework automatically detects classes annotated with _@Component_ annotation and creates Spring beans for those classes.
- _@Component_ is a class-level annotation
- It helps in creating a loosely coupled and easily maintainable application by promoting the use of dependency injection and inversion of control.

### @ResponseBody : 
-  It is typically used in combination with the @Controller annotation to create RESTful web services that return data in a format like JSON or XML.
-  By default, Spring uses the MappingJackson2HttpMessageConverter to convert Java objects to JSON.
-  In Spring MVC, if a method is annotated with @RestController, which is a stereotype annotation that combines @Controller and @ResponseBody, then @ResponseBody is implicit for all mapping methods in that controller.

### @Autowired: 
- The `@Autowired` annotation in Spring is used to automatically inject a dependency into a Spring bean. It allows Spring to resolve and provide the dependency at runtime, without the need for manual instantiation or lookups.
- Spring automatically wires the dependency based on type. You can also use `@Qualifier` to specify a bean name if there are multiple beans of the same type.
- Dependencies annotated with `@Autowired` are considered optional by default. If a suitable bean is not found, the dependency is not injected.
- Promotes loose coupling, enhances code readability, and reduces boilerplate code for manual dependency management.
**Types of Injection**:
1. **Constructor Injection**: Dependencies are injected through a constructor.
Example: 
	``` java
	@Component
	public class ConstructorInjectedService {

	    private final GreetingService greetingService;

	    @Autowired
	    public ConstructorInjectedService(GreetingService greetingService) {
	        this.greetingService = greetingService;
	    }

	    public String getMessage() {
	        return greetingService.sayHello();
	    }
	}
	```
2. **Setter Injection**: Dependencies are injected through a setter method.
Example:
	```java
	@Component
	public class SetterInjectedService {

	    private GreetingService greetingService;

	    @Autowired
	    public void setGreetingService(GreetingService greetingService) {
	        this.greetingService = greetingService;
	    }

	    public String getMessage() {
	        return greetingService.sayHello();
	    }
	}
	```
3.  **Field Injection**: Dependencies are injected directly into a field.
Example: 
	```java
	@Component
	public class FieldInjectedService {

	    @Autowired
	    private GreetingService greetingService;

	    public String getMessage() {
	        return greetingService.sayHello();
	    }
	}
	```
In general, constructor injection is often preferred because it provides a clear and concise way to define dependencies and ensures that objects are fully initialized when they are created. However, the best approach may vary depending on the specific needs of your application and the complexity of your classes.	

### @Qualifier: 
The  _@Qualifier_  annotation is used in conjunction with  @Autowired to avoid confusion when we have two or more beans configured for the same type.
If there are multiple implementations for a single interface then we can use _@Qualifier_  to choose the required implementation at runtime.

### @Primary:
 The `@Primary` annotation in Spring is used to specify a default bean to be used for autowiring when there are multiple beans of the same type.
 When Spring finds more than one bean that can be autowired into a property, it will use the primary bean, marked with `@Primary`, by default.
 It is an alternative for `@Qualifier` annotation.

### @Bean:
- The @Bean annotation is a method-level annotation in the Spring Framework that indicates that the annotated method produces a bean to be managed by the Spring container. This is part of Spring’s Inversion of Control (IoC) mechanism, which allows for dependency injection.
- The `@Bean` annotation in Spring is used to explicitly declare a bean in the Spring application context.
- It is commonly used in Java-based configuration to define beans that are not created by Spring through component scanning or auto-configuration.
- The @Bean annotation is usually declared in the Configuration class to create Spring Bean definitions.
- By default, the bean name is the same as the method name. We can specify the bean name using the **name** attribute of _@Bean_ annotation
- The default scope of a bean created with `@Bean` is singleton, but you can specify other scopes using the `@Scope` annotation.
- @Bean annotation provides _initMethod_ and _destroyMethod_ attributes to perform certain actions after bean initialization or before bean destruction by a container.

### @Configuration:
- Spring _@Configuration_ annotation is part of the spring core framework.
-  The `@Configuration` annotation in Spring is used to indicate that a class defines one or more bean definitions and that Spring should manage the instantiation and configuration of beans defined in that class.
- Beans defined in `@Configuration` classes can be injected into other beans using `@Autowired`.
- `@Configuration` is meta-annotated with `@Component`, so `@Configuration` classes are candidates for component scanning and can be autodetected by Spring.

### @Component:
- The `@Component` annotation in Spring is a generic stereotype annotation.
- It Marks a class as a Spring component.
- Annotate classes should be managed as beans by Spring.
- `@Component` is a generic stereotype annotation and does not provide any specific behavior or specialization beyond indicating that a class is a Spring component. For more specific behaviors, you can use `@Service`, `@Repository`, or `@Controller`, which are specializations of `@Component` with additional semantics.

  
  **The `@Controller`, `@Service`, and `@Repository` annotations are specializations of the `@Component` annotation in Spring, used to define classes as Spring-managed components with specific roles and behavior. Here's a summary of each:**
### @Controller:
- Used to mark a class as a web controller handling incoming HTTP requests and return responses.
- Used to mark classes as Spring MVC controllers.
- Methods within a controller class are annotated with  `@RequestMapping`  to map specific URLs to handler methods.
-   Controller methods often interact with services and repositories to retrieve or manipulate data.
-   @Controller annotation is simply a specialization of the @Component class, which allow us to auto-detect implementation classes through the classpath scanning
- Enables automatic detection and registration of controllers in the Spring MVC context.

### @Service:
-   Used to mark classes as service components in the business layer.
- Typically used to contain business logic, perform operations, and coordinate the flow of data between controllers and repositories.
- Enables automatic detection and registration of services in the Spring context.

### @Repository:
-   Used to mark a class as a data access layer component (often used with JPA).
-   Repository classes provide an abstraction layer for interacting with your database.
- They typically extend interfaces like  `JpaRepository`  provided by Spring Data JPA, inheriting methods for CRUD (Create, Read, Update, Delete) operations and other data access functionalities.
-Enables automatic detection and registration of repositories in the Spring context.

### @RestController:
- The @RestController is a stereotype annotation in Spring and it is a specialized version of the @Controller annotation that is used to create RESTful web services.
- It combines the @Controller and @ResponseBody annotations, meaning that it not only marks the class as a controller but also ensures that the return data in a format like JSON or XML.

### Difference between @Controller and @RestController annotation?

| Feature              | @Controller                                                  | @RestController                                              |
|----------------------|--------------------------------------------------------------|---------------------------------------------------------------|
| Purpose              | Used for traditional web applications, returning views      | Used for building RESTful APIs, returning data (JSON, XML)    |
| Response Type         | Typically returns templates (JSP, Thymeleaf)                           | Returns data in formats like JSON, XML, etc. |
| Additional Annotation    | Often used with @ResponseBody for returning data            | Can be used alone for data return           |
| Example              | @Controller public class MyController { ... }                | @RestController public class MyRestController { ... }        |

![image](https://github.com/user-attachments/assets/4006a1e1-d1d4-4370-b52e-f10fd20cdcf1)



In summary, `@Controller` is used for traditional web applications where views are rendered, while `@RestController` is used for building APIs where data is returned directly in a format like JSON or XML.

### @Lazy:
- By default, the Spring IoC container creates and initializes all singleton beans at the time of application startup. We can prevent this pre-initialization of a singleton bean by using the @Lazy annotation.
- The @Lazy annotation may be used on any class directly or indirectly annotated with @Component or on methods annotated with @Bean.
- The `@Lazy` annotation in Spring is used to indicate that a bean should be lazily initialized. When a bean is lazily initialized, its initialization is deferred until the bean is actually requested for the first time.
- This can be useful for improving performance by delaying the creation of beans that are not immediately needed.
- Beans that are injected with `@Lazy` dependencies are also lazily initialized.
- By default, Spring beans are eagerly initialized. Use `@Lazy` to override this behavior for specific beans.

### @Scope: 
In Spring, the `@Scope` annotation is used to specify the scope of a bean, determining how long the bean should live and how it should be shared in the application context. We use  _@Scope_  to define the scope of a  @Component class or a  @Bean definition.

**Scope Types**: The `@Scope` annotation accepts a `String` value representing the scope type, which can be one of the following:

-   **Singleton** (`"singleton"`): When a Spring bean is scoped as a singleton, the Spring IoC container creates exactly one instance of the object defined by that bean definition and shared across the entire application. (default behavior if not specified).
-   **Prototype** (`"prototype"`): A new instance of the bean is created each time it is requested.
-   **Request** (`"request"`): The bean is scoped to the lifecycle of a single HTTP request. Only valid in a web-aware Spring application.
-   **Session** (`"session"`): The bean is scoped to the lifecycle of an HTTP session. Only valid in a web-aware Spring application.
-   **Application** (`"application"`): The bean is scoped to the lifecycle of a ServletContext. Only valid in a web-aware Spring application. A single instance of the bean is created and shared across the entire application context.
-   **Websocket** (`"websocket"`): The bean is scoped to the lifecycle of a WebSocket. Only valid in a web-aware Spring application.

Example: In this example, `MyPrototypeComponent` is scoped as a prototype, so a new instance will be created each time it is requested.
```java
@Component
@Scope("prototype")
public class MyPrototypeComponent {
    // Class implementation
}
```
- If you don't specify a scope, beans are by default singleton scoped, meaning there is only one instance per Spring container.

### @Value: 
The `@Value` annotation in Spring is used to inject values into fields in a Spring-managed bean from properties files, environment variables, or other Spring-managed beans. It allows you to retrieve values from various sources and assign them to fields, method arguments, or even entire method return types.

1.  **Injecting Values**:
    
    -   Use `@Value` to inject values into fields, constructor parameters, or method parameters.
    -   The value to inject can be a literal value, a property placeholder, or an expression.
    -   Example:
        ```java
        @Component
        public class MyComponent {
            @Value("${my.property}")
            private String myProperty;
            // Getter and setter
        }
      ```  
Here, `${my.property}` is a placeholder for a property defined in a properties file.

2.  **Property Resolution**:
    
    -  Spring resolves placeholders like `${my.property}` by looking for a property with the key `my.property` in the application's property sources (e.g., properties files, environment variables, system properties).
    -   You can also use the `@PropertySource` annotation to specify the location of properties files.
3.  **Default Values**:
    
    -   You can specify a default value to use if the property is not found:
        
		 ```java
		@Value("${my.property:default}")
		private String myProperty;
		```
4.  **Expressions**:
    
    -   You can use SpEL (Spring Expression Language) in `@Value` annotations to perform more complex evaluations:
		```java
		@Value("#{systemProperties['java.home']}")
		private String javaHome;
		```        
5.  **Environment Variables**:
    
    -   `@Value` can also be used to inject values from environment variables:
        ```java
        @Value("${JAVA_HOME}")
        private String javaHome;
        ```
6.  **Constructor Injection**:
    
    -   `@Value` can be used in constructor parameters to inject values when creating a bean:
        ```java
        @Component
        public class MyComponent {
        
            private final String myProperty;
        
            @Autowired
            public MyComponent(@Value("${my.property}") String myProperty) {
                this.myProperty = myProperty;
            }
        
            // Getter
        }
    ```
### @PropertySource and @PropertySources

The `@PropertySource` and `@PropertySources` annotations in Spring are used to specify the location of properties files that contain configuration properties for your application. These annotations are used in conjunction with the `@Configuration` annotation to load external properties files into the Spring environment. Here's a summary of each annotation:

1.  **@PropertySource**:
    
    -   Use `@PropertySource` to specify the location of a single properties file.
    -   You can specify the file location as a classpath resource or a file system path.
    -   Example:
     ```java
        @Configuration
        @PropertySource("classpath:application.properties")
        public class AppConfig {
            // Configuration class
        }
    ```
    - This example loads the `application.properties` file from the classpath.
2.  **@PropertySources**:
    
    -   Use `@PropertySources` to specify multiple properties files.
    -   You can specify an array of `@PropertySource` annotations within `@PropertySources`.
    -   Example:
	```java
	@Configuration
	@PropertySources({
		@PropertySource("classpath:app.properties"),
		@PropertySource("file:/path/to/external.properties")
	})
	public class AppConfig {
		// Configuration class
	    } 
	```        
   -  This example loads properties from both `app.properties` in the classpath and `external.properties` from a file system path.
3.  **Usage**:
    
    -   You typically use `@PropertySource` or `@PropertySources` in a configuration class (annotated with `@Configuration`) to load properties files into the Spring environment.
    -   Once loaded, you can use the `@Value` annotation to inject specific properties into your beans.

### @ConfigurationProperties

The `@ConfigurationProperties` annotation in Spring is used to bind external configuration properties to a Java object. It allows you to map properties defined in properties files, environment variables, or command-line arguments to fields in a Java class. Here's how it works:

1.  **Define Configuration Properties Class**:
    
    -   Create a Java class with fields corresponding to the configuration properties you want to bind.
    -   Annotate the class with `@ConfigurationProperties` and specify the prefix used for the properties.
    -   Example:
   ```java
        @Component
        @ConfigurationProperties(prefix = "myapp")
        public class AppConfig {
            private String name;
            private int timeout;
        
            // Getters and setters
        } 
 ```       
2.  **Specify Properties Prefix**:
    
    -   Use the `prefix` attribute of `@ConfigurationProperties` to specify the prefix used for the properties.
    -   In the example above, properties like `myapp.name` and `myapp.timeout` would be mapped to the `name` and `timeout` fields, respectively.
3.  **Enable Configuration Properties Binding**:
    
    -   Add `@EnableConfigurationProperties` to one of your configuration classes to enable binding of configuration properties.
```java
        @SpringBootApplication
        @EnableConfigurationProperties(AppConfig.class)
        public class MyApplication {
            // Application configuration
        }
```        
4.  **Externalize Configuration**:
    
    -   Define your configuration properties in properties files, environment variables, or command-line arguments.
    -   Example `application.properties`:
		```java
		myapp.name=MyApp
		myapp.timeout=5000 
		```        
5.  **Usage**:
    
    -   Spring will bind the properties defined in your properties files to the fields in your `@ConfigurationProperties` class.
    -   You can then inject the `AppConfig` bean into your application and use the mapped properties.
```java
        @Service
        public class MyService {
            private final AppConfig appConfig;
        
            public MyService(AppConfig appConfig) {
                this.appConfig = appConfig;
            }
        
            public void doSomething() {
                System.out.println("Name: " + appConfig.getName());
                System.out.println("Timeout: " + appConfig.getTimeout());
            }
        } 
```        

The `@ConfigurationProperties` annotation provides a convenient way to externalize and bind configuration properties in Spring applications, making it easier to manage and change configuration settings without modifying the code.

### @RequestMapping:
`@RequestMapping` is an annotation in Spring MVC (Model-View-Controller) framework used to map web requests to handler methods in controller classes.
-   It is used to map HTTP requests (GET, POST, PUT, DELETE, etc.) to specific handler methods.
-  It can be applied at the class level or method level.
-   At the class level, it maps requests to all handler methods in the controller class.
-   At the method level, it maps requests to a specific handler method.
1.  **Basic Usage**:
    
    -   Annotate a method in your `@Controller` class with `@RequestMapping` to map a specific URL pattern to that method.
    -   Example:
 ```java
	        @Controller
        public class MyController {
        
            @RequestMapping("/hello")
            public String sayHello() {
                return "Hello, World!";
            }
        } 
   ```        
   -   In this example, the `sayHello` method will be invoked when a GET request is made to the `/hello` URL.
2.  **HTTP Methods**:
    
    -   You can specify the HTTP method for the mapping using the `method` attribute of `@RequestMapping`.
    -   Example:
 ```java
        @RequestMapping(value = "/hello", method = RequestMethod.POST)
        public String createMessage() {
            return "Message created!";
        }
```        
   -   Here, the `createMessage` method will be invoked only for POST requests to the `/hello` URL.
3.  **URL Patterns**:
    
    -   `@RequestMapping` supports various URL patterns, including path variables, wildcards, and regular expressions.
    -   Example:
```java
        `@RequestMapping("/hello/{name}")
        public String sayHello(@PathVariable String name) {
            return "Hello, " + name + "!";
        }` 
```        
   -   In this example, the `name` path variable will be extracted from the URL.
4.  **Request Parameters**:
    
    -   You can also map requests based on specific request parameters.
    -   Example:
```java
        `@RequestMapping(value = "/hello", params = "name")
        public String sayHello(@RequestParam String name) {
            return "Hello, " + name + "!";
        }` 
 ```       
   -   This mapping will match requests to `/hello` only if they contain a `name` parameter.
5.  **Consumes and Produces**:
    
    -   You can use the `consumes` and `produces` attributes of `@RequestMapping` to specify the media types that a method can consume and produce.
    -   Example:
```java
        `@RequestMapping(value = "/hello", method = RequestMethod.POST, consumes = "application/json", produces = "application/json")
        public ResponseEntity<String> processJson(@RequestBody String json) {
            // Process JSON request and return JSON response
        }` 
```        
   -   This mapping will match POST requests to `/hello` that have a `Content-Type` of `application/json`.

### @GetMapping
-  `@GetMapping`  is a composed annotation in Spring MVC that maps HTTP GET requests to handler methods in a controller class.
-   It is a shortcut for  `@RequestMapping(method = RequestMethod.GET)`.
-  Can be applied at the class level or method level.
    -   Class level: Maps all GET requests to handler methods in the controller.
    -   Method level: Maps GET requests to a specific handler method.
- **Path Variables**: You can use `@PathVariable` in combination with `@GetMapping` to extract values from the URL path. For example:
```java
@GetMapping("/hello/{name}")
public String sayHello(@PathVariable String name) {
    return "Hello, " + name + "!";
}
```
- Can specify additional parameters like headers, consumes, produces, etc.
-   Provides a more readable and concise way to map GET requests compared to  `@RequestMapping`.

### @PostMapping: 
-   Composed annotation in Spring MVC that maps HTTP POST requests to handler methods in a controller class.
-   Shortcut for  `@RequestMapping(method = RequestMethod.POST)`.
-   Used to handle POST requests, typically for creating or submitting new resources.
-   Can be applied at the class level or method level.
-   Supports specifying the URL path pattern and additional parameters like headers, consumes, produces, etc.
-   Commonly used in web forms, file uploads, and creating new resources in RESTful APIs.
-  **RequestBody**: Use `@RequestBody` to bind the HTTP request body to a method parameter. Example:
 ```java
    @PostMapping("/create")
    public ResponseEntity<String> createUser(@RequestBody User user) {
        // Create user logic
    }
 ```    
-  **Response Entity**: Can return a `ResponseEntity` to specify the HTTP status code and response body.

### @RequestBody: 
- The @RequestBody annotation is responsible for retrieving the HTTP request body and automatically convert it to the Java object using an  `HttpMessageConverter`
-   Enables handling incoming data in the request body, which is common in RESTful APIs and web services.
-   `@RequestBody` can be used with other HTTP methods like PUT and PATCH as well, not just POST.
-   **Example**:
    ```java
    @PostMapping("/create")
    public ResponseEntity<String> createUser(@RequestBody User user) {
        // Create user logic
    } 
    ```
-   **Request Body**: The `User` object in the example is populated with the data from the HTTP request body, typically in JSON or XML format.

### @PutMappping: 
-   `@PutMapping`  is a composed annotation in Spring MVC that maps HTTP PUT requests to handler methods in a controller class.
-   It is a shortcut for  `@RequestMapping(method = RequestMethod.PUT)`.
-   Used to handle PUT requests, typically for updating or replacing an existing resource.
-   Can be applied at the class level or method level.
-   Supports specifying the URL path pattern and additional parameters like headers, consumes, produces, etc.
-   Commonly used in RESTful APIs for updating resources based on a unique identifier (e.g.,  `/users/{id}`).
-   Often used in conjunction with  `@RequestBody`  to bind the request body (usually a JSON or XML representation of the updated resource) to a method argument.
-   The `@PathVariable` annotation is used to extract values from the URL path.

### @DeleteMapping:
-   `@DeleteMapping`  is a composed annotation in Spring MVC that maps HTTP DELETE requests to handler methods in a controller class.
-   It is a shortcut for  `@RequestMapping(method = RequestMethod.DELETE)`.
-   Used to handle DELETE requests, typically for deleting or removing an existing resource.
-   Can be applied at the class level or method level.
-   Supports specifying the URL path pattern and additional parameters like headers, consumes, produces, etc.
-   Commonly used in RESTful APIs for deleting resources based on a unique identifier (e.g.,  `/users/{id}`).
-   Often used without a request body, as DELETE requests typically don't have a request body.
-  **Path Variables**: Can use `@PathVariable` to extract values from the URL path, such as the ID of the resource to be deleted.
-   **Response Entity**: Can return a `ResponseEntity` to specify the HTTP status code and response body.
**Example**
	```java
	@DeleteMapping("/delete/{id}")
	public ResponseEntity<String> deleteUser(@PathVariable Long id) {
	    // Delete user logic
	}
	```
	
### @PathVariable:
-   Used to extract values from the URL path and bind them to method arguments in a controller method.
- Used to capture dynamic values from the URI and pass them to the controller method for processing.
-   Commonly used in RESTful APIs to handle URLs with variable parts (e.g.,  `/users/{id}`,  `/orders/{orderId}/items/{itemId}`).
-   The method parameter annotated with  `@PathVariable`  should match the name of the URI template variable (e.g.,  `@PathVariable("id") Long id`).
-   Can be used with multiple path variables in a single method.
- Path variables can be optional by setting the `required` attribute to `false`.
Example - 
	```java
	@GetMapping("/users/{id}/posts/{postId}")
	public String getPostById(@PathVariable Long id, @PathVariable(required = false) Long postId) {
	    // Logic to fetch post with the given ID under the user with id
	}
	```
### @RequestParam:
- It Binds HTTP request parameters to method parameters in a Spring `@Controller` class.
-  `@RequestParam` is used to extract request parameters from the URL query string or form data.
-  The `value` attribute can be used to specify the name of the request parameter.
-   If the parameter name matches the method parameter name, the `value` attribute can be omitted.
-   `defaultValue` can be used to provide a default value for the parameter if it is not present in the request.
-   `required` attribute can be used to specify if the parameter is required or not. It defaults to `true`.
Example:
	```java
	@GetMapping("/search")
	public String searchProducts(@RequestParam("q") String query,
	                             @RequestParam(defaultValue = "0") int page,
	                             @RequestParam(required = false) String category,
	                             Model model) {
	    // logic to search products based on query, page, and category
	    // ...
	    model.addAttribute("products", products);
	    return "search-results";
	}
	```
