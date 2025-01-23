# Java Application with Docker

This repository contains a Java application packaged in a Docker container.

## Prerequisites
- Docker
- Maven (if you want to build locally)
- Java (version 11 or later)

## Steps to Deploy

### 1. **Check Java & Maven Versions**
   - Make sure you have the correct versions of Java and Maven installed on your system:
     - Check Java version:  
       ```bash
       java -version
       ```
     - Check Maven version:  
       ```bash
       mvn -v
       ```
   - If your project uses specific versions, make sure you align your local environment with those versions to avoid build issues.

### 2. **Build the JAR/WAR File with Maven**
   - Navigate to the project directory and run:
     ```bash
     mvn clean install
     ```
   - This will create a `.jar` file (in the `target/` folder) if it's a JAR project. For a WAR file, it will also be in the `target/` folder.

### 3. **Write the Dockerfile**

   Depending on your deployment (JAR or WAR), you will use a different base image.

   **For a `.jar` application**:
   ```dockerfile
   FROM openjdk:11-jre-slim
   COPY target/your-app.jar /app/your-app.jar
   CMD ["java", "-jar", "/app/your-app.jar"]
   EXPOSE 8080
