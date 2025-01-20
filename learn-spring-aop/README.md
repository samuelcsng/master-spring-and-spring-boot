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

# 219 Step 05
- AOP Logging Aspect and Pointcut
- @Configuration
- @Aspect
- Logger, LoggerFactory.getLogger()
- @Pointcut(), @Before()
- JoinPoint
- @Before

# 220 Step 06
- AOP Terminology
- Compile Time
  - Advice
  - Pointcut
  - Aspect (combination of)
    - Advice
    - Pointcut
  - Weaver
    - AspectJ or Spring AOP
- Runtime
  - Join Point

# 221 Step 07
- @After(pointcut)
- @AfterReturning(pointcut, returning)
- @AfterThrowing(pointcut, throwing)

# 222 Step 08
- @Around(pointcut)
- ProceedingJoinPoint, ProceedingJoinPoint.proceed()
- Thread.sleep()
- Logger.info()

# 223 Step 09
- AOP Best Practice
- @Pointcut("execution(...)")
- @Pointcut("bean(...)")

# 224 Step 10
- self-build custom Annotation
  ```java
  @Target(ElementType.METHOD)
  @Retention(RetentionPolicy.RUNTIME)
  public @interface TrackTime {
  }
  ```
- @Pointcut("@annotation(...)")
- @Around("...")
- @TrackTime

# 225 Step 11