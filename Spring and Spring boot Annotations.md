# Spring and Spring Boot Annotations



### @Component : 
-   The `@Component` annotation in Spring is used to mark a class as a Spring bean.
- During the component scan, Spring Framework automatically detects classes annotated with _@Component_ annotation and creates Spring beans for those classes.
- _@Component_ is a class-level annotation
- It helps in creating a loosely coupled and easily maintainable application by promoting the use of dependency injection and inversion of control.

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
