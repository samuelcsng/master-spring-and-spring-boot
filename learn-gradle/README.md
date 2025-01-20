# 226 

# 227 Step 01
- Gradle
  - to build, automate and deliver better software, faster
  - build anything
    - Cross-Platform Tool
      - Java, C/C++, JavaScript, Python, ...
  - Automate Everything
    - completely programmable
      - commplete flexibility
      - DSL Domain Specific Language
        - Groovy and Kotlin
  - fast builds
    - compile avoidance to advanced caching
    - 90% faster than Maven
      - incrementality
        - Gradle runs only what is necessary
          - eg. compiles only changed files
      - build cache
        - reuse the build outputs of other Gradle builds with same inputs
  - same project layout as Maven
  - BUT lack IDE support
- *** maven
  - platform specific Tool
  - depends on Java
  - xml

# 228 Step 02
- Creating Spring Boot Project with Gradle
- start.spring.io
  - Gradle Groovy
  - Java 17
  - dependency - web
  - Eclipse - import
- build.gradle
- settings.gradle
- ./gradlew bootRun

# 229 Step 03
- build.gradle and settings.gradle
- build.gradle
  - dependencies
    - implementation '...'
  - plugins
    - id '...'
  - group = '...'
  - repositories
  - JUnit
- settings.gradle
  - rootProject.name = '...'
  - pluginManagement {}

# 230 Step 04
- Gradle Plugins for Java and Spring Boot
  - Java Plugin
    - Java compilation + testing + bundling capabilities
    - Default Layout(folder structure)
      - src/main/java
      - src/main/resources
      - src/test/java
      - src/test/resources
    - Key Task
      - build
  - Dependency Management
    - Maven-like
    - implementation group:'...', name:'...', version:'...'
    - implementation '...:...:...'
  - Spring Boot Gradle Plugin
    - Spring Boot support in Gradle
      - bootJar, bootBuildImage
      - no need to specify dependency version

# 231 Step 05
- Maven or Gradle
  - Spring Framework v3.2.0 - use Gradle at 2012
  - Spring Boot v2.3.0 - use Gradle at 2020
  - Spring Cloud - continues to use Maven
  - Maven
    - Familiar, Simple, Restrictive
  - Gradle
    - Faster build times, less verbose
    - flexible
    - Groovy script