# Day 3: Three French Hens (Adding User Authentication)

Welcome back to Day 3 of our "12 Days of Code-mas" adventure! Having set up a beautiful homepage, it's time to add a layer of security and personalization to our Holiday Countdown App through user authentication. Today, we'll integrate a secure login and registration system using Spring Boot and Angular.

## Understanding User Authentication

User authentication is a security process that verifies who a user is. It's crucial in personalizing and securing user data. We'll use Spring Security, a powerful and customizable authentication and access-control framework, and JSON Web Tokens (JWT) for secure credential transmission.

## Setting Up Spring Boot for Authentication

### Dependencies and Configuration

First, add the necessary dependencies to your Spring Boot project's `pom.xml`:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt</artifactId>
    <version>0.9.1</version>
</dependency>
```

Create a security configuration class that extends `WebSecurityConfigurerAdapter`:

```java
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@Configuration
@EnableWebSecurity
public class SecurityConfiguration extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .authorizeRequests()
            .antMatchers("/register", "/login").permitAll()
            .anyRequest().authenticated();
    }
}
```

### Creating the User Model

Define a `User` entity:

```java
@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;
    
    private String username;
    private String password;

    // Getters and setters omitted for brevity
}
```

### Building the Authentication API

#### User Registration

Create a `UserController` with a registration endpoint:

```java
@RestController
@RequestMapping("/api")
public class UserController {

    @PostMapping("/register")
    public ResponseEntity<?> registerUser(@RequestBody User user) {
        // Implement user registration logic
        return ResponseEntity.ok("User registered successfully");
    }
}
```

Implement password hashing using `PasswordEncoder` in your service layer.

#### User Login

For the login, you'll handle user authentication and return a JWT:

```java
@PostMapping("/login")
public ResponseEntity<?> loginUser(@RequestBody User user) {
    // Authenticate user and issue JWT
    return ResponseEntity.ok("User logged in successfully");
}
```

## Integrating Authentication with Angular

### Building the Registration and Login Forms

In your Angular app, create forms for registration and login:

```typescript
// registration.component.ts
export class RegistrationComponent {
    // Registration form logic
}

// login.component.ts
export class LoginComponent {
    // Login form logic
}
```

Use Angular's `HttpClient` to send POST requests to your Spring Boot backend.

### Handling JWT in Angular

Store the JWT in the browser's local storage and include it in subsequent HTTP requests:

```typescript
localStorage.setItem('token', jwtToken);
```

## Testing the Authentication Flow

Use tools like Postman to test your API endpoints. Ensure that registration stores user data and login returns a JWT.

## Frontend Feedback and Error Handling

Provide feedback to the user upon registration or login:

```html
<!-- Display error messages -->
<p *ngIf="errorMessage">{{ errorMessage }}</p>
```

## Security Best Practices

Remember to implement HTTPS in production and never store plain-text passwords.

## Conclusion and Preview of Day 4

With user authentication in place, our app is now more secure and personalized! On Day 4, we'll delve into database integration, storing user information securely. Stay tuned for "Four Calling Birds (Database Integration)" where we'll enhance our app's backend capabilities.

This chapter not only adds crucial functionality to our app but also introduces fundamental security practices in web development. Keep coding, and enjoy the festive spirit of learning and building! 🎄🔒💻