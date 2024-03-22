![image](https://github.com/honeysungra/springboot-interview-questions/assets/79264165/71c5b21e-5022-467d-80d2-1959752f0697)# Spring Data JPA Interview Question

### Q01. How is Hibernate chosen as the default implementation for JPA without any configuration?

**Answer:-** Spring Data JPA builds on the standard JPA specification and provides additional features to reduce the amount of boilerplate code neededd for CRUD operations. It offers repository interfaces that can be easily extended to define custom queries, and it provides support for pagination, auditing, and dynamic query generation.
It uses JPA (Java Persistence API) to interact with databases, allowing developers to focus on writing queries and business logic rather than handling low-level database operations.

### Q02.  Basic Flow of Spring Data JPA?
![Flow of Spring data JPA](https://github.com/honeysungra/springboot-interview-questions/assets/79264165/30af0c53-0c5c-4e40-a65f-12bd1e647a27)

### Q03. Explain various properties of Hibernate

**Answer:-** To configure Spring Data JPA in your Spring Boot application, you can use the following properties in your `application.properties` or `application.yml` file:

1. **spring.datasource.url**: The JDBC URL of the database.
   - Example: `spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase`

2. **spring.datasource.username**: The username to use when connecting to the database.
   - Example: `spring.datasource.username=root`

3. **spring.datasource.password**: The password to use when connecting to the database.
   - Example: `spring.datasource.password=password`

4. **spring.datasource.driver-class-name**: The fully qualified name of the JDBC driver class.
   - Example: `spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver`

5. **spring.jpa.show-sql**: Whether to enable logging of SQL statements.
   - Example: `spring.jpa.show-sql=true`

6. **spring.jpa.hibernate.ddl-auto**: Specifies how Hibernate should update the database schema.
   - Example: `spring.jpa.hibernate.ddl-auto=update`
     

7. **spring.jpa.properties.hibernate.dialect**: The Hibernate dialect for the database.
   - Example: `spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect`

8. **spring.data.jpa.repositories.enabled**: Whether Spring Data JPA repositories should be enabled.
   - Example: `spring.data.jpa.repositories.enabled=true`

You can customize these properties based on your specific application and database setup.

### Q04. Explain spring.jpa.hibernate.ddl-auto and spring.jpa.properties.hibernate.dialect in brief.
**Answer:-** **spring.jpa.hibernate.ddl-auto:** This property controls how Hibernate will update the database schema. It has several options:

- validate: Hibernate only validates that the schema matches the entities. It does not make any changes to the database schema.
- update: Hibernate updates the database schema based on the entity mappings. It adds missing tables and columns, but it does not drop any existing schema objects or data.
- create: Hibernate creates the database schema from scratch, dropping any existing schema objects and data. This is useful for development but should be used with caution in production.
- create-drop: Similar to create, but the database schema is dropped when the SessionFactory is closed, typically at the end of the application's lifecycle. This is also useful for development but not recommended for production.
  
**spring.jpa.properties.hibernate.dialect:** This property sets the Hibernate dialect for the database you are using. The dialect determines the SQL syntax and database-specific features that Hibernate will use. For example, for MySQL, you would use org.hibernate.dialect.MySQLDialect, and for PostgreSQL, you would use org.hibernate.dialect.PostgreSQLDialect. Using the correct dialect ensures that Hibernate generates valid SQL queries for your database.

### Q05. Important spring data JPA annotation.
**Answer:-** Here is a list of some common annotations used in Spring Data JPA along with their descriptions and examples:\
**1. @Entity:**
- Description: Marks a class as an entity, which means it will be mapped to a database table.
- Example:
``` java
@Entity
public class User {
    // fields, getters, setters
}
```
**2. @Table:**
- Description: Specifies the details of the database table to which an entity is mapped.
- Example:
``` java
@Entity
@Table(name = "users")
public class User {
    // fields, getters, setters
}
```
- Attributes:
     - name: (String) The name of the table in the database. Default is the entity name.\

**3. @Id:**
- Description: Specifies the primary key of an entity.
- Example:
``` java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```
**4. @GeneratedValue:**
- Description: Specifies the strategy used for generating primary key values.
- Example:
``` java
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```
- Attributes:
     - strategy: (GenerationType) The generation strategy for the primary key.\
       
**5. @Column:**
- Description: Specifies the details of a column in a database table.
- Example:
``` java
@Column(name = "username", nullable = false, unique = true)
private String username;
```
- Attributes:
   - name: (String) The name of the column in the database.
   - nullable: (boolean) Whether the column allows NULL values. Default is true.
   - unique: (boolean) Whether the column values must be unique. Default is false.
   - Many more attributes for column definition like length, precision, scale, etc.
     
**6. @OneToMany:**
- Description: Establishes a one-to-many relationship between two entities.
- Example:
``` java
@Entity
public class Department {
    @OneToMany(mappedBy = "department")
    private List<Employee> employees;
    // other fields, getters, setters
}
```
- Attributes:
   - mappedBy: (String) The field in the target entity that owns the relationship.\
     
**7. @ManyToOne:**
- Description: Specifies a many-to-one relationship between two entities.
- Example:
``` java
@Entity
public class Employee {
    @ManyToOne
    @JoinColumn(name = "department_id", nullable = false)
    private Department department;
    // other fields, getters, setters
}
```
- Attributes:
   - optional: (boolean) Whether the association is optional. Default is true.
   - fetch: (FetchType) The fetching strategy for the association. Default is FetchType.EAGER.
   - cascade: (CascadeType[]) The cascade operations to be applied to the association.\


**8. @Repository:**
- Description: Indicates that an interface or class provides access to the database.
- Example:
``` java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    // methods for accessing user data
}
```
- Attributes:
   - mappedBy: (String) The field in the target entity that owns the relationship.\


**9. @Query:**
- Description: Specifies a JPQL or native SQL query to be executed.
- Example:
``` java
@Query("SELECT u FROM User u WHERE u.username = ?1")
User findByUsername(String username);
```
- Attributes:
   - mappedBy: (String) The field in the target entity that owns the relationship.\

**10. @Transactional:**
- Description: Defines the scope of a single database transaction.
- Example:
``` java
@Transactional
public void updateUser(User user) {
    userRepository.save(user);
}
```
- Attributes:
   - name: (String) The name of the column in the database.
   - nullable: (boolean) Whether the column allows NULL values. Default is true.
   - referencedColumnName: (String) The name of the column in the referenced table.

### Q6. What are the primary key generation strategies?
**Answer:-** The _@GeneratedValue_ annotation works in conjunction with _@Id_ to specify how primary key values should be generated. These strategies are specified using the `@GeneratedValue` annotation's `strategy` attribute. Here are the primary key generation strategies supported by JPA:

**1. GenerationType.IDENTITY -> Database-Generated Auto-Increment:**
 - This strategy is suitable for databases like MySQL and PostgreSQL that support  **auto-incrementing**  columns. The database automatically assigns a unique value to the id field for each new record.
 - Example : 
	```java
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;
	```
**2. GenerationType.SEQUENCE -> Database-Generated Sequence:**
 - A separate database sequence is used to generate unique primary key values. The sequence is usually pre-defined in the database.
 - This strategy is useful for databases like Oracle that have sequence objects.
 - Example: 
	```java
	@GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "user_seq")
	@SequenceGenerator(name = "user_seq", sequenceName = "user_sequence", allocationSize = 1)
	private Long id;
	```
**3. GenerationType.TABLE -> Table-Generated Sequence:**
 - A special table is used to generate unique primary key values. Each row in the table represents a unique key value.
 - The _GenerationType.TABLE_ gets only rarely used nowadays.
 - Prefer the _GenerationType.SEQUENCE_, if your database supports sequences, which most popular databases do.
 - Example:
	 ```java
	    @GeneratedValue(strategy = GenerationType.TABLE, generator = "user_gen")
	    @TableGenerator(name = "user_gen", table = "id_generator", pkColumnName = "gen_name", valueColumnName = "gen_val", pkColumnValue = "user_gen", allocationSize = 1)
	    private Long id;
	```

** 4. GenerationType.AUTO -> Provider-Defined Strategy:**
- This strategy allows the JPA provider to choose the most appropriate strategy based on the underlying database and configuration.
- Example: 
	 ```java
	 @GeneratedValue(strategy = GenerationType.AUTO)
	private Long id;
	```
**5. GenerationType.UUID -> Developer-Defined Strategy:**
- The latest release of the JPA 3.1.0 specification provides developers with a new  _GenerationType.UUID_  we can use in the  _@GeneratedValue_  annotation:
- GenerationType instructs that a UUID for the entity should be generated automatically for us by the persistence provider.
- Example 
	```java
	 @GeneratedValue(strategy = GenerationType.UUID)
	private Long id;
	```
### Q7. Define hibernate annotations- @CreationTimestamp and @UpdateTimestamp
**Answer:-** The `@CreationTimestamp` and `@UpdateTimestamp` annotations are used in Hibernate to automatically populate the creation and last update timestamps of entities. Here's a brief description of each annotation:
**1. @CreationTimestamp:** Marks a field to be automatically populated with the timestamp of when the entity was created.
```java
@CreationTimestamp
@Column(name = "created_at", nullable = false, updatable = false)
private LocalDateTime createdAt;
```
In this example, the `createdAt` field will be automatically set to the current timestamp when a new entity is persisted.

**2 @UpdateTimestamp**: Marks a field to be automatically updated with the timestamp of when the entity was last updated.
```java
@UpdateTimestamp
@Column(name = "updated_at")
private LocalDateTime updatedAt;
```
In this example, the `updatedAt` field will be automatically updated with the current timestamp whenever the entity is updated and persisted.
### Q8. What is Lombok, its uses and their annotations?

**Answer:-** Lombok is a Java library that helps reduce boilerplate code in Java classes. It provides a set of annotations that, when used, automatically generate common code such as getters, setters, constructors, and more. This can lead to more concise and readable code. Some of the key annotations provided by Lombok are:

1. **@Getter** and **@Setter**: Generates getter and setter methods for class fields.

2. **@ToString**: Generates a `toString()` method that includes the class name and all fields.

3. **@EqualsAndHashCode**: Generates `equals()` and `hashCode()` methods based on the class fields.

4. **@NoArgsConstructor**, **@RequiredArgsConstructor**, and **@AllArgsConstructor**: Generates constructors with no arguments, with required arguments, and with all arguments respectively.

5. **@Data**: Combines `@ToString`, `@EqualsAndHashCode`, `@Getter`, `@Setter`, and `@RequiredArgsConstructor` annotations.

6. **@Builder**: Implements the builder pattern for easy object creation with chained method calls.

7. **@Slf4j** and **@Log**: Generates a logger field using the SLF4J or java.util.logging API.

### Q9. Spring data JPA Repository Interfaces and it's Hierarchy.
**Answer:-** ![image](https://github.com/honeysungra/springboot-interview-questions/assets/79264165/a5a12b62-c700-4933-adef-8ac0c24c8e91)
![image](https://github.com/honeysungra/springboot-interview-questions/assets/79264165/fcae5d34-2e9e-4fbc-a5d9-0b7e4c745439)

### Q10. Spring data JPA methods with example
**Answer:-** 
## Spring Data JPA Methods with Examples

Spring Data JPA provides a wide range of methods that you can use to interact with your database without writing custom queries. Here are some common methods along with examples:

1. **Save an Entity**:
   - Save a new entity or update an existing one.
     ```java
     // Save a new entity
     userRepository.save(new User("John Doe", 30));
     
     // Update an existing entity
     User user = userRepository.findById(1L).orElseThrow();
     user.setName("Jane Doe");
     userRepository.save(user);
     ```

2. **Find by ID**:
   - Find an entity by its primary key.
     ```java
     Optional<User> userOptional = userRepository.findById(1L);
     ```

3. **Find All**:
   - Retrieve all entities of a certain type.
     ```java
     Iterable<User> users = userRepository.findAll();
     ```

4. **Delete by ID**:
   - Delete an entity by its primary key.
     ```java
     userRepository.deleteById(1L);
     ```

5. **Count**:
   - Count the number of entities in a repository.
     ```java
     long count = userRepository.count();
     ```

6. **Exists by ID**:
   - Check if an entity with a given ID exists.
     ```java
     boolean exists = userRepository.existsById(1L);
     ```

7. **Find by Property**:
   - Find entities by a specific property value.
     ```java
     List<User> users = userRepository.findByAge(25);
     ```

8. **Find by Multiple Properties**:
   - Find entities by multiple property values.
     ```java
     List<User> users = userRepository.findByNameAndAge("John Doe", 30);
     ```

9. **Query Methods**:
   - Use query methods to define custom queries.
     ```java
     List<User> users = userRepository.findByAgeGreaterThan(25);
     ```

10. **Sorting**:
    - Sort the results of a query.
      ```java
      List<User> users = userRepository.findByAgeGreaterThanOrderByAgeDesc(25);
      ```

11. **Paging**:
    - Retrieve results in a paginated manner.
      ```java
      Page<User> page = userRepository.findAll(PageRequest.of(0, 10));
      ```

12. **Custom Query**:
    - Define a custom query using `@Query` annotation.
      ```java
      @Query("SELECT u FROM User u WHERE u.age > :age")
      List<User> findByAgeGreaterThan(@Param("age") int age);
      ```
These are just a few examples of the methods provided by Spring Data JPA. You can combine these methods and use them according to your application's needs to interact with your database easily and efficiently.
