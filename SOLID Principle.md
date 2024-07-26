  

# SOLID Principle
https://www.inspirontechnologies.co.in/solid-principles-interview-questions
## 1. Why we need solid Principle?
The broad goal of the SOLID principles is to reduce dependencies so that engineers change one area of software without impacting others. Additionally, they’re intended to make designs easier to understand, maintain, and extend. Ultimately, using these design principles makes it easier for software engineers to avoid issues and to build adaptive, effective, and agile software, they lead to better code for readability, maintainability, design patterns, and testability.

## 2. Benefits of using SOLID principles

When you use all the principles of S.O.L.I.D in a combined manner, it becomes easier for you to develop software that can be managed easily.

 **Clean**: SOLID principles make code clean and standard code.

**Maintainable**: with the help of SOLID principles our code becomes more manageable and easy to maintain.

 **Scalable**: Easy to refactor or change code.

**Redundancy**: SOLID principles avoid redundant code.

**Testable**: can be easily unit tested.

**Readable**: SOLID principles make the code easy and readable.

**Independent**: code becomes independent by reducing dependencies.

**Reusable**: code becomes reusable.

## 3. What is Single Responsibility Principle in solid principles?

This principle states that “A class should have only one reason to change” which means every class should have a single responsibility or single job or single purpose. In other words, a class should have only one job or purpose within the software system.
  
**Why is Single Responsibility Principle important?**

* In Real world, Requirement changes and so does your code implementation to cater the changing requirement.

* The more responsibilities your class has, the more often you need to change it. To prevent frequent changes to same class,

* Testing is easier - With a single responsibility, the class will have fewer test cases

* Easier to Understand

* Less functionality also means fewer dependencies to other classes.

* So best practice says : Use layers in your application and break God classes into smaller classes or modules

**Example**
```java
// Bad Example: A class with multiple responsibilities

public class UserService {
	public void createUser(String name) {
	// Code to create user
	}

	public void sendWelcomeEmail(String email) {
	// Code to send welcome email
	}

	public void saveToDatabase(User user) {
	// Code to save user to database
	}
}

// Good Example: Separate classes for each responsibility

public class UserCreationService {
	public void createUser(String name) {
	// Code to create user
	}
}

public class EmailService {
	public void sendWelcomeEmail(String email) {
	// Code to send welcome email
	}
}

public class UserRepository {
	public void saveToDatabase(User user) {
	// Code to save user to database
	}
}
```
**Use Case**: When developing a user management system, keeping user creation, email sending, and database operations separate helps in maintaining and testing the code.
  
## 4. What is Open/Closed Principle in solid principles?

- It states that “Software components should be open for extension, but closed for modification”. which means you should be able to extend a class behavior, without modifying it.
 - The term “Open for extension” means that we can extend and include extra functionalities in our code without altering or affecting our existing implementation. 
- The term “Closed for modification” means that after we add the extra functionality, we should not modify the existing implementation. 
 - In real world, You must have noticed that you change something to cater a new requirement and some other functionality breaks because of your change. To prevent that we have this principle in hand. It is one of the most important concept in in solid principles
  
**Why is Single Responsibility Principle important?**

This principle encourages the extension of existing code without modifying it, reducing the risk of introducing bugs in the existing functionality. It also promotes the use of abstraction, leading to more flexible and scalable systems.
**How to implement Open/Closed Principle in solid principles?**

The application classes should be designed in such a way that whenever fellow developers want to change the flow of control in specific conditions in application, all they need to extend the class and override some functions and that’s it.

**Example-** Imagine you have a class called `PaymentProcessor` that processes payments for an online store. Initially, the `PaymentProcessor` class only supports processing payments using credit cards. However, you want to extend its functionality to also support processing payments using PayPal.

Instead of modifying the existing `PaymentProcessor` class to add PayPal support, you can create a new class called `PayPalPaymentProcessor` that extends the `PaymentProcessor` class. This way, the `PaymentProcessor` class remains closed for modification but open for extension, adhering to the Open-Closed Principle

## 5. What is Liskov’s Substitution Principle
LSP states that the software should not alter the desirable result when we replace a parent type with any of the subtypes.
****Derived or child classes must be substitutable for their base or parent classes****. 
This principle ensures that any class that is the child of a parent class should be usable in place of its parent without any unexpected behavior.

**Example** 
```java
class  Bird {  
	public  void  Eat() {  
	System.out.println("This bird can eat.");  
	}  
	  
	public  void  fly() {  
	System.out.println("This bird can fly.");  
	}  
}  
class  Parrot  extends  Bird {  
}  
  
class  Penguin  extends  Bird {  
	@Override  
	public  void  fly() {  
	throw  new  FlyException("Penguins cannot fly");  
	}  
}
```
The Penguin class overrides the fly() method from the base class, but the behavior is fundamentally different from what’s expected by the base class. This is an LSP violation because when we try to substitute an instance of Penguin for a generic Bird, it will not behave as a typical bird in terms of flying. This could lead to unexpected behavior in the code.

To resolve this LSP violation, you should restructure the class hierarchy and ensure that derived classes confirm to the contract of the base class. One way to fix this issue is to use composition or interfaces to handle behaviors that don’t fit the base class’s contract.

```java
class  Bird{  
	public  void  Eat() {  
	System.out.println("This bird can eat.");  
	}  
}  
class  FlyingBird  extends  Bird{  
	public  void  fly() {  
	System.out.println("This bird can fly.");  
	}  
}  
  
class  Parrot  extends  FlyingBird {  
}  
  
class  Penguin  extends  Bird{  
}
```
**Why is Liskov’s Substitution Principle important?**
This avoid misusing of inheritance . It assists us in adhering to the “is-a” relationship.
It makes the code more robust and reliable. Violations of LSP can lead to unexpected behavior and bugs.

## 6. What is Interface Segregation Principle?
This principle is the first principle that applies to Interfaces instead of classes in SOLID and it is similar to the single responsibility principle. 
It states that “****do not force any client to implement an interface which is irrelevant to them****“. 
Here your main goal is to focus on avoiding fat interface and give preference to many small client-specific interfaces. 
You should prefer many client interfaces rather than one general interface and each interface should have a specific responsibility.

```java
// Bad Example: Interface with too many methods
public interface Worker {
    void work();
    void eat();
}

public class Developer implements Worker {
    @Override
    public void work() {
        // Coding
    }

    @Override
    public void eat() {
        // Eating
    }
}

public class Robot implements Worker {
    @Override
    public void work() {
        // Assembling
    }

    @Override
    public void eat() {
        // Robots don't eat
    }
}

// Good Example: Separate interfaces for each responsibility
public interface Workable {
    void work();
}

public interface Eatable {
    void eat();
}

public class Developer implements Workable, Eatable {
    @Override
    public void work() {
        // Coding
    }

    @Override
    public void eat() {
        // Eating
    }
}

public class Robot implements Workable {
    @Override
    public void work() {
        // Assembling
    }
}
```
**Why is Interface Segregation Principle important?**

By splitting large interfaces into smaller, more specific ones, we ensure that implementing classes only need to be concerned with the methods that are relevant to them. This leads to cleaner, more maintainable code and reduces the implementation burden on classes.

## 7. What is Dependency Inversion Principle?
The principle states that we must use abstraction (abstract classes and interfaces) instead of concrete implementations.

-   High-level modules should not depend on low-level modules. Both should depend on abstractions.
-   Abstractions should not depend on details. Details should depend on abstractions.
-   In simpler terms, the principle encourages you to rely on interfaces or abstract classes to decouple your code and make it easier to extend, maintain, and test.
```java
// Bad Example: High-level module depends on low-level module
public class LightBulb {
    public void turnOn() {
        // Turn on the light bulb
    }

    public void turnOff() {
        // Turn off the light bulb
    }
}

public class Switch {
    private LightBulb lightBulb;

    public Switch() {
        this.lightBulb = new LightBulb();
    }

    public void operate() {
        lightBulb.turnOn();
    }
}

// Good Example: High-level module depends on abstraction
public interface Switchable {
    void turnOn();
    void turnOff();
}

public class LightBulb implements Switchable {
    @Override
    public void turnOn() {
        // Turn on the light bulb
    }

    @Override
    public void turnOff() {
        // Turn off the light bulb
    }
}

public class Switch {
    private Switchable device;

    public Switch(Switchable device) {
        this.device = device;
    }

    public void operate() {
        device.turnOn();
    }
}

```
**Use Case:** When designing an electrical switch system, depending on the `Switchable` interface rather than the specific `LightBulb` class allows the switch to control different devices without modification.
