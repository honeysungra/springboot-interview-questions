
# Spring Boot Interview Question


### Q1. What is Spring Boot and mention the need for it?

Answer:- Spring boot is an open source spring module that aims to simplify the use of the Spring framework. It is used to create standalone Spring-based applications with minimal setup and configuration that you can just run.
It basically removes a lot of configurations and dependencies, allowing developers to focus more on writing the application logic rather than dealing with infrastructure setup.

### Q2. What is the need for spring boot application?

Answer:-  The need for Spring Boot arises from the complexity involved in setting up a Spring application. 
Traditionally, developers had to configure various components such as data sources, application servers, and logging frameworks manually, which could be time-consuming and error-prone.
Spring Boot streamlines this process by providing defaults for these configurations, making it easier to get started with Spring-based projects. 
It also offers a range of features such as embedded servers, auto-configuration, and starter dependencies, which further simplify and accelerate the development process.

### Q3. Key features of Spring boot.

Answer:- Few important features of Spring Boot are as follows:

#### 1.  Auto-configuration: Spring Boot automatically configures your application based on its dependencies, reducing the need for manual configuration.

#### 2. Spring Boot CLI - The Spring Boot Command Line Interface (CLI) allows you to quickly create, test, and run Spring Boot applications using a command-line interface.

#### 3. Starter dependencies -  Spring Boot offers a set of "starter" dependencies that simplify the inclusion of libraries for common tasks such as web development, data access, and security and eventually improves productivity.

#### 4. Spring Initializer - This is basically a web application, which can create an internal project structure for you. So, you do not have to manually set up the structure of the project, instead, you can use this feature.

#### 5. Spring Actuator - Spring Boot Actuator provides a set of production-ready features to help you monitor and manage your application, including health checks, metrics, and more.

#### 6. Logging and Security – The logging and security feature of Spring Boot, ensures that all the applications made using Spring Boot are properly secured without any hassle.

#### 7. Spring Boot DevTools: DevTools provides development-time features like automatic restarts, LiveReload support, and remote debugging to enhance the developer experience.

#### 8. Embedded servlet container support: Spring Boot provides out-of-the-box support for embedded servlet containers like Tomcat, Jetty, and Undertow, making it easy to run web applications.

### Q4. Mention the advantages of Spring Boot?

Answer:- Spring Boot offers several advantages that make it a popular choice for developing Java applications:

#### 1. Simplified configuration: Spring Boot uses sensible defaults and provides auto-configuration, reducing the need for manual configuration and boilerplate code.

#### 2. Rapid development: Spring Boot simplifies the setup and configuration of Spring applications, allowing developers to focus more on writing application logic and less on boilerplate code and configuration.

#### 3. Embedded servers: Spring Boot includes embedded servlet containers like Tomcat, Jetty, and Undertow, allowing you to package and run your application as a standalone JAR file without needing to deploy it to a separate server.

#### 4. Microservices support: Spring Boot's lightweight and modular design make it well-suited for building microservices architectures, where applications are composed of small, independently deployable services.

#### 5. Spring ecosystem: Spring Boot is part of the larger Spring ecosystem, which includes libraries and frameworks for building enterprise-grade applications, such as Spring MVC, Spring Data, and Spring Security.

#### 6. Easy testing: Spring Boot provides support for unit and integration testing out of the box, making it easier to write tests for your applications.

#### 7. Production-ready features: Spring Boot includes features like health checks, metrics, and externalized configuration, making it easier to monitor and manage your application in a production environment.

#### 8. Community and support: Spring Boot has a large and active community of developers, which means there is a wealth of resources, tutorials, and third-party libraries available to help you build your applications.

#### 9. Backward compatibility: Spring Boot maintains backward compatibility with the wider Spring ecosystem, so you can easily upgrade to newer versions without worrying about breaking changes.

#### 10. Easy deployment: With its embedded server and standalone JAR packaging, deploying Spring Boot applications is simple and can be done using standard deployment tools.


### Q5. How Spring Boot internally works or explain run() method in Spring Boot?

Answer:- The run() method in Spring Boot is the entry point for your application. It is typically used to bootstrap and start the Spring application.
It's a static method provided by the SpringApplication class that you call from your application's main method.

@SpringBootApplication
public class MyApplication {

    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }

In this example, the 'run()' method is called with the MyApplication class and the command-line arguments ('args') passed to the application. SpringApplication.run() is a static method that bootstraps and launches the Spring application.
The run() method handles all the complex tasks of setting up the application context, loads beans, and starting the server, so you can focus on writing the business logic of your application.

### Q6. Explain how to create a Spring Boot application using Maven.

Answer:- There are various approaches to create a Spring Boot application using maven, but if I have to name a few, then following are the ways to create a Spring Boot project/ application using maven:

1. Spring Boot CLI
2. Spring Starter Project Wizard
3. Spring Initializr
4. Spring Maven Project

### Q7. What does the @SpringBootApplication annotation do internally?

Answer:- The @SpringBootApplication annotation is a convenience annotation in Spring Boot that adds all of the following:

![image](https://github.com/honeysungra/springboot-interview-questions/assets/79264165/cbbb3d08-69c9-4a4e-bbc6-c7a76f6f570e)

1. @Configuration: Indicates that the class is a configuration class, which typically defines beans and their dependencies.

2. @EnableAutoConfiguration: Enables Spring Boot's auto-configuration feature, which automatically configures the Spring application based on its dependencies and the environment.

3. @ComponentScan: Enables component scanning, which scans the specified package (and its sub-packages) for Spring components, such as @Component, @Service, @Repository, and @Controller.

Internally, when the @SpringBootApplication annotation is used, Spring Boot performs the following tasks:

1. Sets up the application context: Initializes the Spring application context, which manages the application's beans and their dependencies.

2. Enables auto-configuration: Configures the application automatically based on the dependencies and the environment. Spring Boot analyzes the classpath, environment properties, and existing configurations to determine which beans and configurations to apply.

3. Performs component scanning: Scans the specified package (and its sub-packages) for Spring components, such as controllers, services, repositories, and other beans.

4. Starts the embedded servlet container: If the application is a web application, Spring Boot starts an embedded servlet container (e.g., Tomcat, Jetty, or Undertow) to serve HTTP requests.

5. Runs the application: Starts the application, making it ready to handle requests and execute business logic.

### Q8. What is the starter dependency of the Spring boot module?

Answer:- In Spring Boot, starter dependencies are a set of convenient dependency descriptors that you can include in your application to get a specific set of dependencies. Starter dependencies help you quickly set up and use common frameworks and libraries in your Spring Boot application.
Here are some of the commonly used Spring Boot Starter dependencies:

1. spring-boot-starter-web: It is used for building web, including RESTful, applications using Spring MVC. It uses Tomcat as the default embedded container.
2. spring-boot-starter-data-jpa: It simplifies the development of Spring applications that use data access technologies, relational databases, and distributed databases providing powerful capabilities such as Spring Data JPA, Hibernate, DataSource setup, and others.
3. spring-boot-starter-security: It is used for Spring Security. It is a powerful and customizable authentication and access-control framework.
4. spring-boot-starter-test: It is used for testing Spring Boot applications with libraries including JUnit, Hamcrest and Mockito.

### Q9. What is spring boot starter parent?

Answer:- It's used to manage the versions of dependencies and plugins in your project, ensuring that they are all compatible with each other and with the Spring Boot version you are using.
When you use spring-boot-starter-parent as the parent POM  (Project Object Model) for your project, you inherit its configuration, including the dependency management section. This means that you don't need to specify versions for most dependencies in your pom.xml file, as they are already managed by the parent POM.

Additionally, spring-boot-starter-parent provides some useful plugins and configurations for building and packaging your Spring Boot application, such as the Spring Boot Maven plugin for running your application and creating executable JAR files.

### Q10. Explain types of Embedded Servers in Spring boot?
Answer-: The types of embedded servers supported by Spring Boot include:
  1. Tomcat: Tomcat is a widely used embedded server for Java web applications. It is the default embedded server in Spring Boot and is well-suited for running servlet-based applications.

  2. Jetty: Jetty is another popular embedded server option in Spring Boot. It is known for its lightweight and fast startup time, making it suitable for both development and production environments.

  3. Undertow: Undertow is a high-performance web server that is included as an embedded server option in Spring Boot. It is known for its scalability and low resource usage.

To use a specific embedded server in your Spring Boot application, you can include the corresponding starter dependency in your pom.xml (for Maven). For example, to use Tomcat as the embedded server, you would include the spring-boot-starter-tomcat dependency.

### Q11. How to remove embedded tomcat server and enable jetty server/ undertow server?
Answer:- Once we add spring-boot-starter-web dependency as part of pom.xml for web application development with spring boot, it gets the tomcat along with all required dependencies. 
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
#### Exclude Tomcat Server
Now we will exclude the tomcat server for that we  just need to add an additional block to the Spring Boot Starter dependency. In the dependency section, We can add <exclusions> tags that make sure the given artifact is removed at build time.

This is the easiest way to do it.
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <exclusions>
        <exclusion>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```
You can use that approach to exclude Tomcat from Spring Boot and also for any other exclusions.

#### To Add Jetty Server in Spring Boot - 
If you want to use the Jetty server in Spring boot application, first you must need to disable the default tomcat server and then add jetty dependency “spring-boot-starter-jetty“.
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jetty</artifactId> 
</dependency>
```
After adding jetty in pom.xml then at build time it disables tomcat and maps to the Jetty configurations.

#### Add Undertow Server in Spring Boot - 
If you want to use the Undertow server in Spring boot application, first you must need to disable the default tomcat server and then add jetty dependency “spring-boot-starter-undertow“.
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-undertow</artifactId> 
</dependency>
```
After adding Undertow in pom.xml then at build time it disables tomcat and maps to the Jetty configurations.

### Q12. How to run Spring Boot Project from command line?

Answer:- To run a Spring Boot project from the command line, you typically use the mvn (Maven), depending on your build tool. Here are the general steps for running a Spring Boot project from the command line:

#### Using java -jar command
1. Navigate to the project directory: Open a terminal or command prompt and navigate to the root directory of your Spring Boot project.

2. Build the project: If you haven't already built the project, you can use the following command to build it using Maven:
    ``` 
    mvn clean package
    ```
3. Go to target folder using cd target command    
    
4. Running an Executable JAR - 
You can run it using the java command. Navigate to the directory containing the JAR file and use the following command:
```
java -jar your-application.jar
```
Replace your-application.jar with the actual name of your JAR file.

#### Using Spring boot maven plugin (-mvn spring-boot:run)

1. Ensure that your project has the Spring Boot Maven plugin configured in its pom.xml file. The plugin should be included with the spring-boot-maven-plugin groupId and artifactId.

2. Open a terminal and navigate to the directory containing your project's pom.xml file.

3. Run the following Maven command to start your Spring Boot application using the Maven plugin:
```
mvn spring-boot:run
```
5. Maven will build your project and start the embedded server with your application deployed. You should see log output indicating that the application has started.

### Q13. Describe the flow of REST API HTTP request through the Spring Boot project?

Answer:- In a Spring Boot application, the 3-tier architecture can be implemented using the following approach:

![image](https://github.com/honeysungra/springboot-interview-questions/assets/79264165/e4726645-971a-4706-aad3-177d2d111b59)

1. Presentation Tier (UI Tier)/Controller : The presentation tier in a Spring Boot application typically consists of controllers or REST controllers that handle incoming HTTP requests and define the application's API endpoints.
Controllers are responsible for processing user inputs, invoking the appropriate business logic, and returning the response to the client.

2. Service Layer (Business Logic): This layer encapsulates the core functionalities and business logic of your application. It sits between the presentation and data access layers, receiving requests from the presentation layer and manipulating data retrieved from the data access layer.
Service classes interact with repositories (data access objects) to retrieve and manipulate data from the database.
Additionally, aspects such as logging, security, and transaction management can be implemented in this tier using Spring Boot's AOP (Aspect-Oriented Programming) features.

3. Data Access Layer (Persistence): This layer is responsible for interacting with the persistence mechanism, which is typically a database. It handles data persistence (storing data), retrieval, updates, and deletions using the database's functionalities.
Spring Boot provides features like JPA (Java Persistence API) and Spring Data repositories to simplify data access logic. These abstractions allow you to interact with the database using domain objects (POJOs) instead of writing raw SQL queries.

#### Benefits of Three-Tier Architecture:

- Separation of Concerns: Each layer has a well-defined purpose, making the codebase easier to understand, maintain, and test.
- Loose Coupling: Changes in one layer don't necessarily require changes in other layers, promoting flexibility.
- Reusability: Business logic in the service layer can be reused across different presentation layers.
- Scalability: You can independently scale different tiers based on their needs.

### Q14. What Is Spring Boot DevTools used for?

Answer:- Spring Boot DevTools is a set of tools designed to improve developer productivity when working on Spring Boot applications. It provides several features that help streamline the development process, including:
1. Automatic Restart
2. LiveReload
3. Remote Development
4. Additional Tools
To include the DevTools, you just have to add the following dependency into the pom.xml file:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
</dependency>
```

### Q15. How to Add Security to Spring Boot and Explain Security Auto Configuration?

Answer:- To add security to a Spring Boot application, you can use the Spring Security framework, which provides comprehensive security features for Java applications. Here's how to add security to a Spring Boot application and an explanation of security auto-configuration:

Add Spring Security Dependency: In your pom.xml (for Maven), add the following dependency for Spring Security:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```
Here's what it does by default:

- Secures all Endpoints: All HTTP endpoints are secured, requiring user authentication for access.
- Default Login: A basic login form is enabled using HTTP Basic authentication. Spring Boot generates a random initial user with a password logged to the console.
- BCrypt Password Encoding: It uses a strong password hashing algorithm (BCrypt) to securely store passwords.

Default username is user and password is generated on console. You can change the username, passwords and roles in application.properties file also.
```xml 
spring.security.user.name=honey
spring.security.user.password=password
spring.security.user.roles=ADMIN
```

### Q16. what is logging.level.org.springframework.security=DEBUG used for in application.properties file?

Answer:- Here's a breakdown of what each part does:

-> logging.level: This is a common property prefix used for configuring logging levels in Spring Boot applications. 
-> org.springframework.security: This specifies the logger name. In this case, it targets the entire Spring Security package.
-> =DEBUG: This assigns the level DEBUG to the logger. DEBUG is a specific level in logging that captures very detailed information, including method calls, variable states, and other low-level details.

Spring Security also offers other logging levels like INFO, WARN, and ERROR. You can adjust the level based on your needs. For example, INFO might be sufficient for general security operation monitoring.

### Q17. Have you used profiles in your Spring Boot project? Explain briefly

Answer:- Profiles in Spring Boot allow you to define different configurations for different environments (e.g., development, testing, production) and activate them based on the environment in which the application is running. Profiles are defined using application-{profile}.properties or application-{profile}.yml files, where {profile} is the name of the profile.

For example, you can have application-dev.properties for development settings, application-test.properties for testing settings, and application-prod.properties for production settings. You can also define common properties in application.properties that apply to all profiles.

To activate a profile, you can use the spring.profiles.active property in your application.properties,y. For example, to activate the dev profile, you can use:

```xml 
spring.profiles.active=dev
```
### Q18. Explain Spring Actuator and its advantages.

Answer:- Spring Boot Actuator is a set of production-ready features that provide operational insights into your Spring Boot application. Spring Actuator is a cool feature of Spring Boot with the help of which you can see what is happening inside a running application. So, whenever you want to debug your application, and need to analyze the logs you need to understand what is happening in the application right? In such a scenario, the Spring Actuator provides easy access to features such as identifying beans, CPU usage, etc.

1. Health Check: Actuator provides a /health endpoint that gives information about the health of the application. This can be used by monitoring tools to check if the application is running correctly.

2. Metrics: Actuator includes endpoints for collecting and exposing metrics about the application, such as request rates, error rates, and JVM metrics. These metrics can be used for performance monitoring and troubleshooting.

3. Monitoring and Auditing: Actuator provides endpoints for monitoring the application's configuration (/configprops), environment variables (/env), and logging levels (/loggers). It also includes auditing features for tracking changes to configuration properties (/auditevents).

4. Management Endpoints: Actuator includes a variety of other management endpoints for tasks such as shutting down the application (/shutdown), viewing thread dump (/threaddump), and viewing application information (/info).

5. Custom Endpoints: Actuator allows you to create custom management endpoints to expose additional information or functionality specific to your application.

### Q19. Explain what is thymeleaf and how to use thymeleaf?

Answer:- Thymeleaf is a modern server-side Java template engine for web applications. It is designed to be highly extensible and easy to integrate with Spring Boot, making it a popular choice for building web applications with Spring Boot. 
Thymeleaf allows you to create dynamic web pages by combining HTML templates with Java code.

To use Thymeleaf in a Spring Boot application, follow these steps:
1. Add Thymeleaf dependency to your pom.xml (for Maven):
    ``` xml
    <!-- For Maven -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>
    ```
2. Create a Thymeleaf template file (e.g., index.html) in the src/main/resources/templates directory. This file will contain your HTML template with Thymeleaf expressions.
   
3.Use Thymeleaf expressions in your template to dynamically display data. For example, you can use ${variable} to display a variable value, th:each to iterate over a list, and th:if to conditionally display content.

4. Create a controller in your Spring Boot application that returns the name of the template file (without the .html extension) as a string. For example:
``` java
@Controller
public class HomeController {

    @GetMapping("/")
    public String home(Model model) {
        model.addAttribute("message", "Hello, Thymeleaf!");
        return "index";
    }
}
```
5. Access your application in a web browser and verify that the Thymeleaf template is rendered correctly, with the dynamic content displayed as expected.

### Q20. Can we change the port of the embedded Tomcat server in Spring boot?

**Answer:-** Yes, we can change the port of the embedded tomcat server by using the application properties file. In this file, you have to add a property of “server.port” and assign it to any port you wish to. For example, if you want to assign it to 8081, then you have to mention server.port=8081. Once you mention the port number, the application properties file will be automatically loaded by Spring Boot and the required configurations will be applied on to the application.


### 21.  What are the @RequestMapping  and @RestController annotation in Spring Boot used for?

**Answer:-**  In Spring Boot, @RequestMapping and @RestController are annotations used together to develop RESTful APIs. Here's a breakdown of their individual functionalities and how they work together:

#### @RestController - 
This annotation is a specialized version of the @Controller annotation that is used to build RESTful web services. It combines the @Controller and @ResponseBody annotations.
- **@Controller:** Marks a class as a Spring MVC controller, enabling it to handle web requests.
- **@ResponseBody:** Tells Spring Boot to automatically convert the return value of any request handling method annotated with @RestController into JSON or XML.

#### @RequestMapping: 
The @RequestMapping annotation is used to map HTTP requests to handler methods in your controller.
It can be placed at the class level or the method level.
When placed at the class level, it defines a base path for all the request mappings within that class.

Key attributes of @RequestMapping:

- **value:** This attribute specifies the path mapping for the request.
- **method:** This attribute restricts the mapping to specific HTTP methods (GET, POST, PUT, DELETE, etc.).

### Q22. What is JPA and hibernate and there difference?

**Answer:-** __JPA__ (Java Persistence API) is a Java specification for accessing, persisting, and managing data between Java objects and a relational database. It provides a standard way to map Java objects to database tables and vice versa, as well as a set of APIs for querying and managing data in the database.

**Hibernate** is a popular implementation of the JPA specification.  It is an ORM (Object-Relational Mapping) framework that simplifies database interactions between Java objects and database tables.
 
The main difference is that JPA is a specification, while Hibernate is an implementation of that specification. This means that Hibernate provides additional features beyond the JPA standard. However, using JPA allows for more flexibility and portability, as it is not tied to a specific implementation like Hibernate.

**In essence:**

Think of JPA as the blueprint for building a house (data persistence), and Hibernate as a contractor (implementation) who can build the house (ORM) following the JPA blueprint. While you can use other contractors, Hibernate is a reliable and experienced choice for the job.



### Q23. Explain Spring Data?

**Answer:-** Spring Data is a part of the larger Spring Framework that aims to simplify the development of data access layer in Spring applications. 
Spring Data aims to make it easy for the developers to use relational and non-relational databases, cloud-based data services, and other data access technologies. So, basically, it makes it easy for data access and still retains the underlying data.

### Q24. What do you understand by auto-configuration in Spring Boot and how to disable the auto-configuration?

**Answer:-** Auto-configuration in Spring Boot refers to the mechanism by which Spring Boot automatically configures beans and components based on the dependencies and environment detected in your application. 

To disable auto-configuration in Spring Boot, you can use the @EnableAutoConfiguration annotation with the exclude attribute to exclude specific auto-configuration classes. For example, to exclude the DataSourceAutoConfiguration class, which configures a data source bean, you can use the following code:

```Java
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration;
import org.springframework.boot.SpringApplication;

@SpringBootApplication(exclude = DataSourceAutoConfiguration.class)
public class MyApplication {
    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }
}
```

In this example, @SpringBootApplication(exclude = DataSourceAutoConfiguration.class) disables the auto-configuration of the data source bean. You can use the exclude attribute to exclude other auto-configuration classes as needed.

Apart from this, Spring Boot also provides the facility to exclude list of auto-configuration classes by using the spring.autoconfigure.exclude property. You can go forward, and add it either in the application.properties or add multiple classes with comma-separated.

### Q25. What are the differences between @SpringBootApplication and @EnableAutoConfiguration annotation?

**Answer:-** **@SpringBootApplication** 
- It is typically used to annotate the main class of a Spring Boot application to enable various features, such as component scanning, auto-configuration, and specifying the base package for component scanning.
- It is a combination of @Configuration, @ComponentScan and @EnableAutoConfiguration annotations.

**@EnableAutoConfiguration** 
- It is used to enable Spring Boot's auto-configuration mechanism, which automatically configures the Spring application based on its classpath and the dependencies it contains.
- It is a combination of @Configuration and @ComponentScan annotations

### Q26. What is the best way to expose custom application configuration with Spring Boot?

**Answer:-** Spring Boot lets you expose custom settings for your application in two ways:

**1. Using Properties Files:**
- This is the simplest approach. You can create properties files (YAML is also supported) with key-value pairs representing your configuration settings.
- Put these files in a special folder (src/main/resources).
- Spring Boot automatically loads these properties and makes them available through the Spring Environment.
- Access these settings in your code using @Value or other methods.

**2. @ConfigurationProperties (Organized):**
- This approach provides a more structured way to define your configuration.
- Create a class annotated with @ConfigurationProperties specifying a prefix for your configuration properties.
- Inside this class, define variables for each setting you need.
- Spring Boot automatically matches these variables to settings with similar names in your property files and uses those values.

**Choosing the Best Way:**

For simple configurations with a few settings, properties files might be sufficient.
For more complex configurations with nested structures or relationships between settings, using @ConfigurationProperties offers better type safety, organization, and maintainability.


### 27.  Can we create a non-web application in Spring Boot?

**Answer:-**  Yes, you can create non-web applications in Spring Boot. While Spring Boot is often used for developing web applications, it can also be used for standalone applications, batch processing applications, command-line applications, and more.
We can create a non-web application by removing the web dependencies from the classpath along with defining the entry point of your application.


### Q28. What are the steps to connect an external database like MySQL or Oracle?


**Answer:-** To connect an external database like MySQL or Oracle to a Spring Boot application, you can follow these general steps:
1. Add the Database Driver Dependency in pom.xml file
2. Configure the Database Connection in application.properties file.    
    ```xml 
    spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase
    spring.datasource.username=myuser
    spring.datasource.password=mypassword
    spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver (Optional)
    ```
3. Enable JPA (Optional) and Defines Entities - If you plan to use JPA (Java Persistence API) for object-relational mapping, include the spring-boot-starter-data-jpa dependency and configure JPA properties like:
```spring.jpa.hibernate.ddl-auto: ```
Defines how JPA interacts with the database schema (e.g., create, update, none).

4. Run Your Application

### Q29. How is Hibernate chosen as the default implementation for JPA without any configuration?

**Answer:-** **@RequestMapping**\
The @RequestMapping annotation is used in Spring MVC to map HTTP requests to handler methods in your controller. It can be placed at the class level or the method level. When placed at the class level, it defines a base path for all the request mappings within that class.
It can be used to map requests of any HTTP method (GET, POST, PUT, DELETE, etc.) to the corresponding handler method.

**@GetMapping**  \
On the other hand, is a specialized form of @RequestMapping that is used specifically for mapping HTTP GET requests. It is a shortcut annotation that combines @RequestMapping with the method attribute set to RequestMethod.GET, making it more concise and easier to read for handling GET requests.

In summary, @RequestMapping is a general-purpose annotation for mapping any HTTP request method, while @GetMapping is a specific annotation for mapping HTTP GET requests.

### Q30. In which layer, should the boundary of a transaction start?

**Answer:-** The boundary of the transaction should start from the Service Layer since the logic for the business transaction is present in this layer itself.


### Q31. Explain how to register a custom auto-configuration.


**Answer:-** Here's how to register a custom auto-configuration in Spring Boot: \
**1. Create a Configuration Class:** Develop a class annotated with @Configuration. This class will hold the configuration logic for your custom auto-configuration feature.\
**2. Use Conditional Annotations (Optional):**
You can leverage conditional annotations like @ConditionalOnClass or @ConditionalOnMissingBean to control when your auto-configuration gets applied. \
**@ConditionalOnClass:** Activates the configuration only if a specific class is present on the classpath (indicates related functionality exists). \
**@ConditionalOnMissingBean:** Activates the configuration only if a specific bean hasn't already been defined elsewhere.

**3. Implement Your Configuration Logic:** Inside your configuration class, define beans, properties, or other configurations specific to your custom feature.

**4. Register the Configuration Class:** **@EnableAutoConfiguration Annotation**
Within this annotation, provide a list that includes the class containing your custom auto-configuration. This instructs Spring Boot to consider your custom configuration during the auto-configuration process.

By following these steps, you can create and register custom auto-configurations in your Spring Boot application, extending its functionality and providing tailored behavior based on your specific needs.


### Q32. Explain Spring Data?

**Answer:-** 
### WAR vs Embedded Containers


| Aspect         | WAR                           | Embedded Containers            |
|----------------|-------------------------------|--------------------------------|
| Packaging      | Packaged as a WAR file        | Packaged as an executable JAR |
| Deployment     | Deployed to a web server   | No separate deployment step   |
| Portability    | Portable to any servlet container | Self-contained and portable  |
| Configuration  | External configuration (e.g., server.xml) | Configuration through application properties or classes |
| Development    | Requires deployment to web server | Can be run directly from IDE |

## WAR (Web Application Archive)

- **Packaging**: WAR files contain all resources and classes needed to run a web application.
- **Deployment**: Requires deployment to a web server (e.g., Tomcat, Jetty).
- **Portability**: Portable to any servlet container that supports the Servlet API.
- **Configuration**: External configuration (e.g., server.xml) for the servlet container.
- **Development**: Requires deployment to a web server for testing.

## Embedded Containers

- **Packaging**: Packaged as an executable JAR file containing the application and embedded container.
- **Deployment**: No separate deployment step; application runs directly from the JAR file.
- **Portability**: Self-contained and portable, as the container is packaged with the application.
- **Configuration**: Configuration through application properties or classes.
- **Development**: Can be run directly from the IDE without deploying to a web server.

In summary, WAR files are traditional deployment artifacts that require deployment to a web server, while embedded containers provide a more self-contained and lightweight deployment model that is well-suited for development and testing.



### Q33. What do you think is the need for Profiles?

**Answer:-** Profiles are used to provide a way to segregate the different parts of the application configuration and make it available for various environments.

Consider you have multiple environments,

- Dev
- QA
- Stage
- Production
Now, let’s say, you want to have different application configuration in each of the environments, you can use profiles to have different application configurations for different environments.

**Example:** **Using application.properties**

In your application.properties file:
```xml
spring.profiles.active=dev 
```
 

### Q25. What are the steps to add a custom JS code with Spring Boot?

**Answer:-** To add custom JavaScript code to a Spring Boot application, you can follow these steps:

**1. Create a JavaScript file:** First, create a JavaScript file (e.g., custom.js) with your custom JavaScript code. You can place this file in the src/main/resources/static directory of your Spring Boot project.

Example custom.js:

```js
console.log("Hello, custom JavaScript!");
```

**2.Link the JavaScript file in your HTML:** If you want to include the custom JavaScript in a Thymeleaf template or a regular HTML file, you can add a <script> tag to link to your JavaScript file.

Example Thymeleaf template (index.html):
```html

<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Custom JavaScript Example</title>
</head>
<body>
    <h1>Custom JavaScript Example</h1>
    <!-- Link to custom JavaScript file -->
    <script th:src="@{/js/custom.js}"></script>
</body>
</html>
```

**3. Serve the JavaScript file:** Spring Boot automatically serves static content from the src/main/resources/static directory, so your custom.js file will be accessible at http://localhost:8080/js/custom.js (assuming your application runs on port 8080).

**4. Include the JavaScript in your web pages:** Once you've linked your JavaScript file in your HTML or Thymeleaf template, the custom JavaScript code will be executed when the page is loaded.

By following these steps, you can add custom JavaScript code to your Spring Boot application and include it in your web pages.

### Q26. How to instruct an auto-configuration to back off when a bean exists?
**Answer:-** To instruct an auto-configuration class to back off when a bean exists, you have to use the @ConditionalOnMissingBean annotation. The attributes of this annotation are as follows:

- **value:** This attribute stores the type of beans to be checked
- **name:** This attribute stores the name of beans to be checked

### Q27. Why is Spring Data REST not recommended in real-world applications?

**Answer:-** Spring Data REST is great for quick prototypes, but not ideal for complex apps because:

- Security Risk: Exposes entire entities, potentially revealing sensitive data.
- Limited Control: Offers basic CRUD, might lack customization for complex logic.
- Over/Under Exposure: Might expose too much or not enough data by default.
- Domain vs Consumer Focus: Prioritizes your model, not necessarily what consumers need.

**Alternatives to Spring Data REST:**

**Spring MVC:** Offers more control over your API design and allows you to build custom controllers with tailored functionalities.\
**Spring WebFlux:** For reactive APIs with improved performance and scalability.

### Q28. What do you understand by Spring Boot supports relaxed binding?
**Answer:-** In Spring Boot, relaxed binding refers to the ability to configure application properties in a more flexible and forgiving manner. It allows you to use different formats, case styles, and variations of property names in your configuration files without causing errors.

For example, if you have a property named server.port in your application.properties file, you can configure it using various styles:

- server.port=8080 (standard format)
- server.Port=8080 (camel case)
- SERVER_PORT=8080 (uppercase)
- SERVERPORT=8080 (no dot notation)
Spring Boot's relaxed binding automatically converts these variations to the correct property name format (server.port) behind the scenes, making configuration more user-friendly and forgiving.

### Q29. What is the name of the default H2 database configured by Spring Boot?
**Answer:-** The name of the default H2 database is testdb.  Refer below:
```
spring.datasource.name=testdb # Name of the datasource.
```
Note: Just incase if you are using H2 in-memory database, then exactly that is the name of Spring Boot which is used to setup your H2 database.


