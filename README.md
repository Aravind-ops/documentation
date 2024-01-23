ADVANCED QUESTIONS

1)webclient with https , flux
2)Reusable services to be used by multiple business groups / springboot library creation
3)Distributed database transaction
4)Hibernate bidirectional mapping



JAVA


SPringboot microservices

1)Integration with core banking application - application refresh

2)Cloud strategy for a banking group

3)How much time spent on integration issues between teams

4)https certificate configuration - webclient with SSL  /write https client code with webclient

5)Starter package / library creation in springboot





6)Q: What is difference between Spring Security's @PreAuthorize and HttpSecurity?
Ans:
The first distinction is small, but it is important to note. Before controller mapping occurs, the HttpSecurity function rejects the request in a web request filter. The @PreAuthorize assessment, on the other hand, occurs later, directly before the controller method is executed. This means that HttpSecurity configuration is done before @PreAuthorize.
Second, HttpSecurity is associated with URL endpoints, whereas @PreAuthorize is associated with controller methods and is located within the code next to the controller definitions.
The use of SpEL (Spring Expression Language ) is another advantage that @PreAuthorize has over HttpSecurity.



7)CORS configuration springboot 


If we use Spring Security in our project, we must take an extra step to make sure it plays well with CORS. That’s because CORS needs to be processed first. Otherwise, Spring Security will reject the request before it reaches Spring MVC.

Luckily, Spring Security provides an out-of-the-box solution:

@EnableWebSecurity
public class WebSecurityConfig {

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http.cors().and()...
    }
}


For that, we need to add a CorsConfigurationSource bean that takes care of the CORS configuration using a CorsConfiguration instance. The http.cors() method uses CorsFilter if a corsFilter bean is added, else it uses CorsConfigurationSource. If neither is configured, then it uses the Spring MVC pattern inspector handler.


8)Performance tuning in Relational databse
When should indexes be avoided?
Although indexes are intended to enhance a database's performance, there are times when they should be avoided.

The following guidelines indicate when the use of an index should be reconsidered.

Indexes should not be used on small tables.

They should not be used on tables that have frequent, large batch updates or insert operations.

Indexes should not be used on columns that contain a high number of NULL values.

Columns that are frequently manipulated should not be indexed.




9)SAGA pattern is a design pattern that is a long-lived sequence of smaller transactions. This pattern is used to manage and maintain data consistency across multiple microservices.

It helps to maintain data consistency by providing an alternative approach to the traditional ACID transactions model that may not be feasible in a distributed environment.

Since each service can have its database and be in a different environment



with the database per service, we’re able to use polyglot persistence. It means that we can use different database technologies for different microservices. So one service may use an SQL database and another one a NoSQL database. 



Shared Database
A shared database is considered an anti-pattern. Although, it’s debatable. The point is that when using a shared database, the microservices lose their core properties: scalability, resilience, and independence. Therefore, a shared database is rarely used with microservices.

CQRS (Command Query Responsibility Segregation) helps with another important feature: querying related data from multiple data states.




Generally, NoSQL databases are designed for horizontal scalability and high availability, so they are not focused on offering ACID transactions. At times the data will not be consistent, which means they are not well-suited for transactions that require immediate integrity, such as banking and ATM transactions.
# documentation
