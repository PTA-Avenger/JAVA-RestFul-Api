Secure Guestbook API
This project is an enterprise-grade REST API built with Java and Spring Boot. It features a secure guestbook system where users can register, authenticate via JWT (JSON Web Tokens), and sign a digital guestbook.


### Tech Stack

Language: Java 17+ 


Framework: Spring Boot 3+ 


Security: Spring Security & JWT 


Persistence: Spring Data JPA with H2 Database (In-memory) 


Utilities: Lombok 

### Features

User Authentication: Secure registration and login using BCryptPasswordEncoder for password hashing.



JWT Security: Stateless authentication using signed tokens for protected resources.


Guestbook Management:


Public: View all guestbook signatures.


Private: Sign the guestbook (requires a valid JWT).

API Security Rules:


Permit All: /api/register, /api/login, and /api/signatures.


Authenticated Only: Any other request, including /api/sign, requires a Bearer token.

### Getting Started
1. Prerequisites
Java 17 or higher installed.

Maven (or use the provided mvnw wrapper).

2. Configuration & Dependencies
The project requires the following key dependencies in your pom.xml:


spring-boot-starter-security 


jjwt-api, jjwt-impl, and jjwt-jackson (v0.11.5) 

3. Installation & Running
Clone the repository.

Run the application using the Maven wrapper:

Bash
./mvnw clean spring-boot:run


### API Endpoints
Method	Endpoint	Description	Auth Required
POST	/api/register	
Register a new user account 

No
POST	/api/login	
Authenticate and receive a JWT 

No
GET	/api/signatures	
View all guestbook entries 

No
POST	/api/sign	
Add a message to the guestbook 

Yes (Bearer Token)
Testing with Token
To access protected endpoints, include the token in the request header:


Authorization: Bearer <your_jwt_token> 

### Project Structure

JwtService: Handles token generation, extraction, and validation.
+1


JwtAuthenticationFilter: Intercepts requests to validate the "Bearer" token in the header.
+1


SecurityConfig: Defines the security filter chain, stateless session policy, and endpoint permissions.
+1


ApplicationConfig: Configures the UserDetailsService, AuthenticationProvider, and PasswordEncoder.
+1
