# REST API and RestAssured Interview Questions and Answers for 3 Years SDET Experience in Banking Domain

## 1. What is a REST API?
### Answer:
A REST API (Representational State Transfer Application Programming Interface) is a set of rules that allows programs to communicate with each other over the web. It uses standard HTTP methods (GET, POST, PUT, DELETE) and typically returns data in JSON format.

## 2. What are the main principles of REST?
### Answer:
The main principles of REST include:
- **Statelessness**: Each request from the client must contain all the information needed for the server to fulfill that request.
- **Client-Server Architecture**: The client and server operate independently of each other.
- **Cacheability**: Responses must define themselves as cacheable or not for better performance.
- **Layered System**: A client should not typically be able to tell whether it is connected directly to the end server or an intermediary.
- **Uniform Interface**: Resources are identified through URIs, and standard HTTP methods are used to interact with them.

## 3. What is RestAssured?
### Answer:
RestAssured is a Java DSL (Domain Specific Language) for testing REST services in a simple way. It provides a set of constraints that let us validate the behavior of REST APIs effectively.

## 4. How do you send a GET request in RestAssured?
### Answer:
```java
import io.restassured.RestAssured;
import static io.restassured.RestAssured.*;

public class GetRequestExample {
    public static void main(String[] args) {
        RestAssured.given()
            .when()
            .get("https://api.example.com/users")
            .then()
            .statusCode(200);
    }
}
```

## 5. How do you authenticate a REST API in RestAssured?
### Answer:
You can authenticate using Basic Authentication as follows:
```java
import io.restassured.RestAssured;
import static io.restassured.RestAssured.*;

public class AuthExample {
    public static void main(String[] args) {
        RestAssured.given()
            .auth().preemptive().basic("username", "password")
            .when()
            .get("https://api.example.com/login")
            .then()
            .statusCode(200);
    }
}
```

## 6. What are some common HTTP status codes?
### Answer:
- **200 OK**: The request has succeeded.
- **201 Created**: The request has succeeded and a new resource has been created.
- **400 Bad Request**: The server could not understand the request due to invalid syntax.
- **401 Unauthorized**: Authentication is required and has failed or has not yet been provided.
- **404 Not Found**: The server cannot find the requested resource.
- **500 Internal Server Error**: The server has encountered a situation it doesn’t know how to handle.

## 7. Can you explain the importance of JSON Schema?
### Answer:
JSON Schema is used to validate the structure of JSON data. It ensures that the API responses match the expected set of rules for data types, required fields, and other constraints, enhancing data quality and consistency.

## 8. How can you use parameterization in RestAssured?
### Answer:
You can use parameterization to send dynamic data in your requests. Example:
```java
public void addUser(String name, int age) {
    given()
        .contentType("application/json")
        .body("{\"name\": \"" + name + "\", \"age\": " + age + "}")
        .when()
        .post("https://api.example.com/users")
        .then()
        .statusCode(201);
}
```

## 9. What are some best practices for testing REST APIs?
### Answer:
- Validate the response time of the API.
- Check for different status codes for various scenarios.
- Ensure the API handles input validation correctly.
- Test edge cases and boundary conditions.
- Use assertions to validate the response body and headers.

## 10. Describe the role of logging in API testing.
### Answer:
Logging is crucial for troubleshooting and understanding the flow of API requests and responses. It helps in identifying issues, especially when tests fail, by providing context around what happened during the request lifecycle.

---