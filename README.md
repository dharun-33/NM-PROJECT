
Here’s a **Java REST Client Integration Project** example with **full content**, including the explanation, project structure, and sample code.

---

## 🌐 **Project Title:** REST Client Integration using Java

### **Objective**

To create a Java application that consumes a RESTful web service using the `HttpClient` or `RestTemplate` library.
The project demonstrates how to perform **GET**, **POST**, **PUT**, and **DELETE** operations from a Java REST client.

---

## ⚙️ **Technologies Used**

* Java (JDK 11+)
* REST API (JSON-based)
* Maven (for dependency management)
* Spring Boot (optional)
* HttpClient / RestTemplate / HttpURLConnection
* IDE: VS Code / IntelliJ / Eclipse

---

## 🗂️ **Project Structure**

```
RestClientIntegration/
 ├── src/
 │   └── main/
 │       └── java/
 │           └── com/example/restclient/
 │               ├── RestClientApplication.java
 │               ├── model/
 │               │   └── User.java
 │               └── service/
 │                   └── RestClientService.java
 └── pom.xml
```

---

## 📘 **1. Model Class – User.java**

```java
package com.example.restclient.model;

public class User {
    private int id;
    private String name;
    private String email;

    public User() {}

    public User(int id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    public int getId() { return id; }
    public void setId(int id) { this.id = id; }

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }

    @Override
    public String toString() {
        return "User [id=" + id + ", name=" + name + ", email=" + email + "]";
    }
}
```

---

## 📘 **2. REST Client Service – RestClientService.java**

```java
package com.example.restclient.service;

import java.net.URI;
import org.springframework.http.*;
import org.springframework.web.client.RestTemplate;
import com.example.restclient.model.User;

public class RestClientService {

    private static final String BASE_URL = "https://jsonplaceholder.typicode.com/users";
    private final RestTemplate restTemplate = new RestTemplate();

    // GET Request
    public void getUserById(int id) {
        String url = BASE_URL + "/" + id;
        ResponseEntity<User> response = restTemplate.getForEntity(url, User.class);
        System.out.println("GET Response: " + response.getBody());
    }

    // POST Request
    public void createUser(User user) {
        ResponseEntity<User> response = restTemplate.postForEntity(BASE_URL, user, User.class);
        System.out.println("POST Response: " + response.getBody());
    }

    // PUT Request
    public void updateUser(int id, User user) {
        String url = BASE_URL + "/" + id;
        restTemplate.put(url, user);
        System.out.println("User updated successfully!");
    }

    // DELETE Request
    public void deleteUser(int id) {
        String url = BASE_URL + "/" + id;
        restTemplate.delete(url);
        System.out.println("User deleted successfully!");
    }
}
```

---

## 📘 **3. Main Class – RestClientApplication.java**

```java
package com.example.restclient;

import com.example.restclient.model.User;
import com.example.restclient.service.RestClientService;

public class RestClientApplication {
    public static void main(String[] args) {
        RestClientService client = new RestClientService();

        // GET Example
        client.getUserById(1);

        // POST Example
        User newUser = new User(11, "Aravinth", "aravinth@example.com");
        client.createUser(newUser);

        // PUT Example
        User updatedUser = new User(1, "Updated Name", "update@example.com");
        client.updateUser(1, updatedUser);

        // DELETE Example
        client.deleteUser(1);
    }
}
```

---

## 🧩 **4. pom.xml (if using Maven)**

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
    http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>restclient</artifactId>
    <version>1.0</version>

    <dependencies>
        <!-- Spring Web for RestTemplate -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-web</artifactId>
            <version>6.0.9</version>
        </dependency>

        <!-- JSON Processing -->
        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
            <version>2.16.0</version>
        </dependency>
    </dependencies>
</project>
```

---

## ✅ **Output Example**

```
GET Response: User [id=1, name=Leanne Graham, email=Sincere@april.biz]
POST Response: User [id=11, name=Aravinth, email=aravinth@example.com]
User updated successfully!
User deleted successfully!
```

---

## 📄 **README.md (for GitHub)**

```markdown
# Java REST Client Integration

## 📘 Overview
This project demonstrates how to integrate a Java client with a RESTful API using Spring's `RestTemplate`.  
It performs CRUD operations (GET, POST, PUT, DELETE) on JSONPlaceholder API.

## ⚙️ Features
- REST API Consumption using Java
- JSON parsing with Jackson
- Simple and clean architecture

## 🚀 How to Run
1. Clone the repo
2. Open in IntelliJ / VS Code
3. Run `RestClientApplication.java`

## 🧩 API Used
`https://jsonplaceholder.typicode.com/users`

## 🧑‍💻 Example Operations
- Fetch user details  
- Create new user  
- Update existing user  
- Delete user  
```

---

Would you like me to modify this to use **HttpClient (without Spring Boot)** instead of `RestTemplate` — for a more lightweight **pure Java** version?
