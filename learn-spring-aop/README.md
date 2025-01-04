# 214

# 215 Step 01
- Spring AOP(Aspect Oriented Programming)
- Pointcut
- Aspect
- Advice
- Annotations
- @Before
- @After
- @Around

# 216 Step 02
- Aspect Oriented Programming(AOP)
  - Web Layer
    - View Logic for web apps OR JSON conversion for REST API
  - Business Layer
    - Business Logic
  - Data Layer
    - Persistence Logic
  - common aspects:
    - Security
    - Performance
    - Logging
  - Cross Cutting Concerns
    - AOP implements Cross Cutting Concerns
      - implement the cross cutting concern an aspect
      - define point cuts
  - AOP Frameworks
    - Spring AOP (works with Spring Beans)
    - AspectJ (works on any Java class)

# 217 Step 03
- Spring Initializr
  - Gradle Project
    - build.gradle
    - settings.gradle
```commandline
./gradlew.bat bootRun
```


# 218 Step 04
- Spring Components for AOP
- CommandLineRunner interface
```java
@Override
public void run(String... args) throws Exception {
  ...
}
```
- Logger, LoggerFactory.getLogger()
  - logger.info()
- @Component, @Service
- @Repository
- 