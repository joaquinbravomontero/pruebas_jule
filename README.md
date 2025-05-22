# Spring Boot Demo Application

This is a simple Spring Boot application built with Java 21 and Maven.

## Features

- Responds with "Hello World" at the `/hello` endpoint.

## Prerequisites

- Java Development Kit (JDK) 21 or later.
- Maven (or use the provided Maven wrapper `mvnw`).
- Docker (for Docker instructions).

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
