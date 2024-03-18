# Spring Data JPA Interview Question

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

### Q05. f
