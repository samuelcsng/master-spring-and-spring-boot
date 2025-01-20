# 232

# 233
- docker command list

# 234 Step 01
- Docker
- Manual Deployment
  1. Setup Hardware
  2. Setup OS(Linux, Windows, Mac,...)
  3. Install Software(Java,Python,NodeJs,...)
  4. Setup Application Dependencies
  5. Install Application
- docker --version
- docker container run -d -p 5000:5000 in28min/hello-world-python:0.0.1.RELEASE

# 235 Step 02
- Docker Fundamentals
- OS, Programming Language, Hardware not matter
1. Developer create Docker image
2. Operations run the Docker image
   - run same docker command for any images
- docker container ls
- docker container stop container_ID
- docker container run -d -p 5000:5000 in28min/hello-world-java:0.0.1.RELEASE
- docker container run -d -p 5000:5000 in28min/hello-world-nodejs:0.0.1.RELEASE
- Docker image includes:
  - OS
  - Application Runtime(JDK or Python or NodeJS)
  - Application code and dependencies
- run Docker container the same way everywhere:
  - local machine
  - corporate data center
  - cloud

# 236 Setp 03
- how Docker works
- standardized application packaging
- multi platform support
- isolation
- docker container run -d -p 5000:5000 in28min/hello-world-nodejs:0.0.1.RELEASE
  - Docker Registry(Default: Docker Hub)
  - Image
  - Container
    - docker image ls
  - Repository Name
  - Tag(or version)
  - -p hostPort:containerPort
    - Docker internal network: bridge network
    - host port
    - docker container ls
    - docker container stop containerID
  - -d
    - Detached Mode (no tie up with the terminal)

# 237 Step 04
- Docker Terminology
  - Docker Image
    - OS, software, code, dependencies
  - Docker Registry
  - Docker Hub
  - Docker Repository
    - same repository have different images(same image name)
    - different Docker images for the same repository is differentiated by different tags
  - Docker Container
    - Runtime instance of a docker image
  - Dockerfile
    - instructions to create Docker image

# 238 Step

# 239 Step 05
- Dockerfile
  - FROM base_image
  - COPY target/*.jar app.jar
  - EXPOSE 5000
  - ENTRYPOINT ["java", "-jar", "/app.jar"]
```dockerfile
FROM openjdk:21-jdk-slim
COPY target/*.jar app.jar
EXPOSE 5000
ENTRYPOINT ["java","-jar","/app.jar"]
```
- mvn clean install -> ./target/*.jar
- docker --version
- docker build -t in28min/hello-world-docker:v1 .
- docker image list
- docker run -d -p 5000:5000 in28min/hello-world-docker:v1
- docker container ls

# 240 Step 06
- Dockerfile - 2
  - Build Jar File - Multi Stage
  - build the jar file as part of creation of Docker Image
  - run the jar file in the image
- docker build -t in28min/hello-world-docker:v2 .
- NOT make use of anything built on local machine, jar file build on image
```dockerfile
FROM maven:3.9.6-amazoncorretto-21-al2023 AS build
WORKDIR /home/app
COPY . /home/app
RUN mvn -f /home/app/pom.xml clean package

FROM openjdk:21-jdk-slim
EXPOSE 5000
COPY --from=build /home/app/target/*.jar app.jar
ENTRYPOINT [ "sh", "-c", "java -jar /app.jar" ]
```

# 241 Step 07
- Dockerfile - 3
- Improve Layer Caching
- improve build time of docker image
- layering
- Docker caches every layer and tries to reuse
```dockerfile
FROM maven:3.9.6-amazoncorretto-21-al2023 AS build
WORKDIR /home/app

COPY ./pom.xml /home/app/pom.xml
COPY ./src/main/java/com/in28minutes/rest/webservices/restfulwebservices/RestfulWebServicesApplication.java	/home/app/src/main/java/com/in28minutes/rest/webservices/restfulwebservices/RestfulWebServicesApplication.java

RUN mvn -f /home/app/pom.xml clean package

COPY . /home/app
RUN mvn -f /home/app/pom.xml clean package

FROM openjdk:21-jdk-slim
EXPOSE 5000
COPY --from=build /home/app/target/*.jar app.jar
ENTRYPOINT [ "sh", "-c", "java -jar /app.jar" ]
```
- docker build -t in28min/hello-world-docker:v3 .

# 242 Step 08
- Spring Boot Maven Plugin - Create Docker Image
- Spring Boot support in Apache Maven
  - create executable jar package
  - run Spring Boot application
  - create Container Image
```xml
  <build>
      <plugins>
          <plugin>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-maven-plugin</artifactId>
          </plugin>
      </plugins>
  </build>
```
- commands:
  - mvn spring-boot:repackage
  - mvn spring-boot:run
  - mvn spring-boot:start
  - mvn spring-boot:stop
  - mvn spring-boot:build-image
    - build OCI image (Open Container Initiative Compatible Image)
    - Docker is compatible with OCI image format and can use the image
    - can build efficient image (smaller in size, build time much shorter)
    - request java version at least 17
    - no need to create Dockerfile 

# 243 Stop 09
- Docker with Spring Boot Review
  - Docker file
  - multi-stage - nothing build in local machine
  - layer caching - reuse duplicated processes
  - Spring Boot Mavn Plugin - no Dockerfile created
    - mvn spring-boot:build-i