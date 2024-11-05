### ApplicationConfiguration.java

The ApplicationConfiguration class configures the security settings and authentication mechanisms needed for managing user access within the application. It enables Spring Security to handle user authentication by integrating with a custom UserRepository for user data retrieval and implementing password encryption.

#### Key Components

- **UserRepository**: Injected to fetch user data for authentication based on email.

#### Beans

- **UserDetailsService**:
  - Retrieves user details by email.
  - Throws a UsernameNotFoundException if the user is not found.
  - Used by Spring Security for authentication.

- **BCryptPasswordEncoder**:
  - Provides password encoding using BCrypt, a secure hashing algorithm.
  - Ensures that user passwords are stored in an encoded format to enhance security.

- **AuthenticationManager**:
  - Configures and retrieves an AuthenticationManager instance.
  - Responsible for authenticating user credentials.

- **AuthenticationProvider**:
  - Configures a DaoAuthenticationProvider with the UserDetailsService and BCryptPasswordEncoder.
  - Defines how authentication is managed, including credential validation and password encoding.

### JwtAuthenticationFilter.java

The JwtAuthenticationFilter class is a custom filter used to handle JSON Web Token (JWT) authentication for the application. It extends OncePerRequestFilter to ensure that each request is processed only once within the filter chain. This filter intercepts HTTP requests, extracts and validates JWT tokens, and sets the security context if the token is valid.

#### Key Components

- **JwtService**: Provides methods for extracting and validating the JWT and retrieving the username from it.
- **UserDetailsService**: Service used to load user details by username.
- **HandlerExceptionResolver**: Handles exceptions that may arise during authentication.

#### Methods

- **doFilterInternal**:
  - Intercepts each HTTP request.
  - Checks if an Authorization header is present and starts with Bearer, indicating a JWT.
  - Extracts the token and uses JwtService to get the username from it.
  - Loads the user's details if the username is found and checks if the token is valid.
  - If valid, creates a UsernamePasswordAuthenticationToken, sets it in the security context, and marks the user as authenticated.
  - Uses HandlerExceptionResolver to manage exceptions.

#### Workflow

- **Authorization Header Check**: Ensures only requests with a valid Bearer token are processed.
- **Token Validation**: Verifies the JWT's authenticity.
- **Security Context Update**: Sets the authenticated user in SecurityContextHolder if authentication is successful.

---

### RestTemplateConfig.java

The RestTemplateConfig class configures a RestTemplate bean, which is used to make RESTful HTTP requests within the application. It enables easy and synchronous communication with external APIs or other microservices.

#### Key Component

- **RestTemplate**: A Spring utility for performing HTTP requests and receiving responses synchronously.

#### Bean

- **restTemplate**:
  - Creates and configures a singleton RestTemplate instance.
  - Allows HTTP requests throughout the application by injecting this bean.

---

### SecurityConfiguration.java

The SecurityConfiguration class configures Spring Security settings for authentication, authorization, and Cross-Origin Resource Sharing (CORS) policies.

#### Key Components

- **AuthenticationProvider**: Handles authentication using a custom provider.
- **JwtAuthenticationFilter**: A custom filter for validating JWT tokens per request.

#### Beans

- **securityFilterChain**:
  - Configures HTTP security settings including CORS, CSRF, session management, and authorization.
  - **CORS**: Enables Cross-Origin Resource Sharing with specific origins, headers, and methods.
  - **CSRF**: Disabled as JWT is used, making CSRF protection unnecessary.
  - **Authorization**: Permits /auth/** endpoints for authentication and requires authentication for others.
  - **Session Management**: Sets to STATELESS as JWTs are used for authentication.

- **corsConfigurationSource**:
  - Configures CORS settings with allowed origins, methods, headers, exposed headers, and credential sharing options.


