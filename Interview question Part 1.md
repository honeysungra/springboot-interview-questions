
# Spring Boot Interview Question


#### Q1. What is Spring Boot and mention the need for it?

Answer:- Spring boot is an open source spring module that aims to simplify the use of the Spring framework. It is used to create standalone Spring-based applications with minimal setup and configuration that you can just run.
It basically removes a lot of configurations and dependencies, allowing developers to focus more on writing the application logic rather than dealing with infrastructure setup.

#### Q2. What is the need for spring boot application?

Answer:-  The need for Spring Boot arises from the complexity involved in setting up a Spring application. 
Traditionally, developers had to configure various components such as data sources, application servers, and logging frameworks manually, which could be time-consuming and error-prone.
Spring Boot streamlines this process by providing defaults for these configurations, making it easier to get started with Spring-based projects. 
It also offers a range of features such as embedded servers, auto-configuration, and starter dependencies, which further simplify and accelerate the development process.

#### Q3. Key features of Spring boot.

Answer:- Few important features of Spring Boot are as follows:

#### 1.  Auto-configuration: Spring Boot automatically configures your application based on its dependencies, reducing the need for manual configuration.

#### 2. Spring Boot CLI - The Spring Boot Command Line Interface (CLI) allows you to quickly create, test, and run Spring Boot applications using a command-line interface.

#### 3. Starter dependencies -  Spring Boot offers a set of "starter" dependencies that simplify the inclusion of libraries for common tasks such as web development, data access, and security and eventually improves productivity.

#### 4. Spring Initializer - This is basically a web application, which can create an internal project structure for you. So, you do not have to manually set up the structure of the project, instead, you can use this feature.

#### 5. Spring Actuator - Spring Boot Actuator provides a set of production-ready features to help you monitor and manage your application, including health checks, metrics, and more.

#### 6. Logging and Security – The logging and security feature of Spring Boot, ensures that all the applications made using Spring Boot are properly secured without any hassle.

#### 7. Spring Boot DevTools: DevTools provides development-time features like automatic restarts, LiveReload support, and remote debugging to enhance the developer experience.

#### 8. Embedded servlet container support: Spring Boot provides out-of-the-box support for embedded servlet containers like Tomcat, Jetty, and Undertow, making it easy to run web applications.

#### Q4. Mention the advantages of Spring Boot?

Spring Boot offers several advantages that make it a popular choice for developing Java applications:

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


#### Q5. How Spring Boot internally works or explain run() method in Spring Boot?

Answer:- The run() method in Spring Boot is the entry point for your application. It is typically used to bootstrap and start the Spring application.
It's a static method provided by the SpringApplication class that you call from your application's main method.

@SpringBootApplication
public class MyApplication {

    public static void main(String[] args) {
        SpringApplication.run(MyApplication.class, args);
    }

In this example, the 'run()' method is called with the MyApplication class and the command-line arguments ('args') passed to the application. SpringApplication.run() is a static method that bootstraps and launches the Spring application.
The run() method handles all the complex tasks of setting up the application context, loads beans, and starting the server, so you can focus on writing the business logic of your application.

#### Q6. Explain how to create a Spring Boot application using Maven.

Answer:- There are various approaches to create a Spring Boot application using maven, but if I have to name a few, then following are the ways to create a Spring Boot project/ application using maven:

Spring Boot CLI
Spring Starter Project Wizard
Spring Initializr
Spring Maven Project

#### Q7. What does the @SpringBootApplication annotation do internally?

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

#### Q8. What is the starter dependency of the Spring boot module?

Answer:- In Spring Boot, starter dependencies are a set of convenient dependency descriptors that you can include in your application to get a specific set of dependencies. Starter dependencies help you quickly set up and use common frameworks and libraries in your Spring Boot application.
Here are some of the commonly used Spring Boot Starter dependencies:

1. spring-boot-starter-web: It is used for building web, including RESTful, applications using Spring MVC. It uses Tomcat as the default embedded container.
2. spring-boot-starter-data-jpa: It simplifies the development of Spring applications that use data access technologies, relational databases, and distributed databases providing powerful capabilities such as Spring Data JPA, Hibernate, DataSource setup, and others.
3. spring-boot-starter-security: It is used for Spring Security. It is a powerful and customizable authentication and access-control framework.
4. spring-boot-starter-test: It is used for testing Spring Boot applications with libraries including JUnit, Hamcrest and Mockito.

#### Q9. What is spring boot starter parent?

Answer:- It's used to manage the versions of dependencies and plugins in your project, ensuring that they are all compatible with each other and with the Spring Boot version you are using.
When you use spring-boot-starter-parent as the parent POM  (Project Object Model) for your project, you inherit its configuration, including the dependency management section. This means that you don't need to specify versions for most dependencies in your pom.xml file, as they are already managed by the parent POM.

Additionally, spring-boot-starter-parent provides some useful plugins and configurations for building and packaging your Spring Boot application, such as the Spring Boot Maven plugin for running your application and creating executable JAR files.

#### Q10. Explain types of Embedded Servers in Spring boot?
Answer-: The types of embedded servers supported by Spring Boot include:
  1. Tomcat: Tomcat is a widely used embedded server for Java web applications. It is the default embedded server in Spring Boot and is well-suited for running servlet-based applications.

  2. Jetty: Jetty is another popular embedded server option in Spring Boot. It is known for its lightweight and fast startup time, making it suitable for both development and production environments.

  3. Undertow: Undertow is a high-performance web server that is included as an embedded server option in Spring Boot. It is known for its scalability and low resource usage.

To use a specific embedded server in your Spring Boot application, you can include the corresponding starter dependency in your pom.xml (for Maven). For example, to use Tomcat as the embedded server, you would include the spring-boot-starter-tomcat dependency.

#### Q11. How to remove embedded tomcat server and enable jetty server/ undertow server?
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
