# 167 Step 01
- spring-boot-starter-web
  - spring-webmvc 
  - spring-web
  - spring-boot-starter-tomcat
  - spring-boot-starter-json
- spring-starter-data-jpa
- spring-boot-devtools
- h2

# 168 Step 02
- @RestController
- @RequestMapping
- @GetMapping

# 167 Step 03
- JSON response
- @Override toString()

# 170 Step 04
- logging.level
- DispatcherServlet - Front Controller Pattern
- Starter Project
- Auto Configuration
- to JSON
  - @ResponseBody + JacksonHttpMessageConverters
- error mapping

# 171 Step 05
- Path Parameter
- @PathVariable

# 172 Step 06
- GET
- POST
- PUT
- PATCH
- DELETE

# 173 Step 07
- DAO Data Access Object
- JPA/Hibernate > Database

# 175 Step 08
- @Component + @Autowired
- Optional.get() vs Optional.orElseThrow()

# 176 Step 09
- @PostMapping + @RequestBody

# 177 Step 10
- response status
- HTTP Status Code
- @ResponseEntity.method()
- URI
- ServletUriComponentsBuilder

# 178 Step 11
- Exception Handling - 404 Resource Not Found
- @ResponseStatus(code = HttpStatus.NOT_FOUND)
- Spring Boot DevTools is disabled when running a Java .jar file

# 180 Step 12
- Generic Exception Handling
- @ControllerAdvice
- extends ResponseEntityExceptionHandler
- @ExceptionHandler()
- ResponseEntity<>

# 181 Step 13
- @DeleteMapping()

# 182 Step 14
- Validations
- spring-boot-starter-validation
- @Valid
- @Size(min = ..., message ="...")
- @Past(message = "...")
- handleMethodArgumentNotValid

# 183 Step 15
- Documentation
- Content Negotiation
- Internationalization - i18n
- Versioning
- HATEOAS
- Static Filtering
- Dynamic Filtering
- Monitoring

# 184

# 185 Step 16
- Swagger(2011)
- Open API(2016)
- Swagger UI

# 186 

# 187 Step 17
- springdoc openapi
- springdoc-openapi-starter-webmvc-ui

# 188 Step 18
- Content Negotiation
- format: JSON, XML
- language: English, ...
- Accept Header(MIME types)
  - application/json
  - application/xml
- Accept-Language Header(en, nl, fr, ...)
```java
<groupId>com.fasterxml.jackson.dataformat</groupId>
<artifactId>jackson-dataformat-xml</artifactId>
```

# 189 Step 19
- Internationalization - i18n
- HTTP Request Header
  - Accept-Language
- MessageSource.class
- LocaleContextHolder.getLocale()

# 190

# 191 Step 20
- Versioning REST API
  - URI Versioning - Twitter
- URL
- Request Parameter
- Header
- Media Type

# 192 Step 21
- Request Parameter versioning - Amazon
- (Custom) Headers versioning - Microsoft
- Media Type versioning (content negotiation or accept header) - GitHub

# 193 Step 22
- HATEOAS
  - Hypermedia as the Engine of Application State
  - HAL
    - JSON Hypertext Application Language
    ```
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-hateoas</artifactId>
    ```
    - EntityModel<...>
    - WebMvcLinkBuilder

# 194 Step 23
- Static Filtering for REST API
- Serialization (Java object -> JSON stream), Jackson framework
  - Customize field names in response
    - @JSONProperty
  - Return only selected fields
    - Filtering
      - Static Filtering
        - @JsonIgnore
        - @JsonIgnoreProperties(...)
      - Dynamic Filtering

# 195 Step 24
- Dynamic Filtering for REST API
  - MappingJacksonValue
  - FilterProvider
  - SimpleFilterProvider
  - SimpleBeanPropertyFilter
  - @JsonFilter(...)

# 196 Step 25
- Spring Boot Actuator
  - Monitor and manage
```java
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-actuator</artifactId>
```
  - endpoints:
    - beans
    - health
    - metrics
    - mappings
    - env
  - ```management.endpoints.web.exposure.include=*```

# 197 Step 26
- Spring Boot HAL Explorer
  - HAL (JSON Hypertext Application Language)
  - HAL Explorer
```java
<groupId>org.springframework.data</groupId>
<artifactId>spring-data-rest-hal-explorer</artifactId>
```

# 198 Step 27
- H2 w/ JPA + Hibernate

# 199

# 200 Step 28
- @Entity()
- @Id
- @GeneratedValue
```java
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
spring.jpa.defer-datasource-initialization=true
```

# 201 Step 29
- H2 + JPA + Hibernate
- JpaRepository<>
- repository.findById() -> Optional<>

# 202 Step 30
- Entity with Many-to-One relationship
- @OneToMany
- @ManyToOne(fetch = FetchType.LAZY)
- @JsonIgnore
- spring.jpa.show-sql=true

# 203 Step 31
- GET API

# 204 Step 32
- POST API
- @Size()
- ResponseEntity<>
- Optional<>.get()
- ServletUriComponentsBuilder

# 205 Step 33
- JPA and Hibernate Queries for REST API
- spring.jpa.show-sql=true

# 206 Step 34
- MySQL

# 207 Step 34z
- Docker MySQL

# 208

# 209

# 210 Step 35
- REST API to MySQL
```java
spring.datasource.url=jdbc:mysql://localhost:3306/udemy
spring.datasource.username=root
spring.datasource.password=admin1234

spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
```
```java
<groupId>com.mysql</groupId>
<artifactId>mysql-connector-j</artifactId>
```
- mysqlsh (MySQL Shell)

# 211 Step 36
- Basic Authentication Spring Security
```java
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-starter-security</artifactId>
```
```java
spring.security.user.name=username
spring.security.user.password=password
```

# 212 Step 37
- Enhanced Spring Security Configuration for Basic Authentication
- Filter Chains
  1. All requests should be authenticated
  2. If a request is not authenticated, a web page is shown
  3. CSRF -> POST, PUT
```java
@Configuration
public class SpringSecurityConfiguration {

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {

        http.authorizeHttpRequests(
                auth -> auth.anyRequest().authenticated()
        );

        http.httpBasic(withDefaults());

        http.csrf().disable();

        return http.build();
    }
}
```
- Configuration
  - Bean FilterChain
  - @Configuration
  - @Bean
  - SecurityFilterChain()
  - HttpSecurity

# 213



