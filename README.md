# Spring Boot Demo Application

This is a simple Spring Boot application built with Java 21 and Maven.

## Features

- Responds with "Hello World" at the `/hello` endpoint.

## Prerequisites

- Java Development Kit (JDK) 21 or later.
- Maven (or use the provided Maven wrapper `mvnw`).
- Docker (for Docker instructions).
- Jenkins (for CI/CD pipeline).

## Building and Running the Application (Using Maven)

1.  **Clone the repository (if you haven't already):**
    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

2.  **Build the project using Maven:**
    ```bash
    ./mvnw clean package
    ```
    This command compiles the code and packages it into a JAR file in the `target` directory.

3.  **Run the application:**
    There are a couple of ways to run the application:

    *   **Using the Spring Boot Maven plugin (recommended for development):**
        ```bash
        ./mvnw spring-boot:run
        ```

    *   **Running the executable JAR file:**
        ```bash
        java -jar target/demo-0.0.1-SNAPSHOT.jar
        ```
        (Replace `demo-0.0.1-SNAPSHOT.jar` with the actual JAR file name if it differs).

## Building and Running the Application (Using Docker)

1.  **Build the Docker image:**
    Make sure you are in the root directory of the project where the `Dockerfile` is located.
    ```bash
    docker build -t spring-boot-demo .
    ```
    This command builds a Docker image tagged as `spring-boot-demo`.

2.  **Run the Docker container:**
    ```bash
    docker run -p 8080:8080 spring-boot-demo
    ```
    This command runs the Docker container and maps port 8080 of the container to port 8080 on your host machine.

## Accessing the Endpoint

Once the application is running (either via Maven or Docker), you can access the "Hello World" endpoint by opening your web browser or using a tool like `curl`:

```
http://localhost:8080/hello
```

You should see the response:
```
Hello World
```

## CI/CD Pipeline with Jenkins

This project includes a `Jenkinsfile` which defines a CI/CD (Continuous Integration/Continuous Delivery) pipeline for automating the build, test, and deployment processes.

The `Jenkinsfile` provides a basic structure for a declarative pipeline and includes the following stages:

1.  **Checkout**: Checks out the source code from the version control system.
2.  **Build**: Compiles the application and packages it using Maven (`./mvnw clean package -DskipTests`).
3.  **Test**: Runs the unit tests using Maven (`./mvnw test`).
4.  **Code Quality**: A placeholder stage for integrating code quality analysis tools like SonarQube. (Requires further Jenkins and SonarQube configuration).
5.  **Build Docker Image**: Builds a Docker image of the application using the provided `Dockerfile`.
6.  **Publish Docker Image**: A placeholder stage for publishing the Docker image to a container registry (e.g., Docker Hub, ECR, GCR). (Requires further Jenkins configuration with Docker registry credentials).

**Note:** Some steps in the `Jenkinsfile`, such as code quality analysis and publishing the Docker image, are placeholders. They require additional configuration in your Jenkins environment (e.g., SonarQube server integration, Docker registry credentials) to be fully functional. The pipeline is designed to be run in a Jenkins environment where Docker and Maven are accessible.
