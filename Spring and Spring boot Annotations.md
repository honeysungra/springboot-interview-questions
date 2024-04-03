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
