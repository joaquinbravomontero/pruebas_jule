# Spring Boot Demo Application

This is a simple Spring Boot application built with Java 21 and Maven.

## Features

- Responds with "Hello World" at the `/hello` endpoint.

## Prerequisites

- Java Development Kit (JDK) 21 or later.
- Maven (or use the provided Maven wrapper `mvnw`).

## Building and Running the Application

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

## Accessing the Endpoint

Once the application is running, you can access the "Hello World" endpoint by opening your web browser or using a tool like `curl`:

```
http://localhost:8080/hello
```

You should see the response:
```
Hello World
```
