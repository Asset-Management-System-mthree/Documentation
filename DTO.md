### LoginUserDto.java

The LoginUserDto class is a Data Transfer Object (DTO) used for encapsulating the login credentials of a user. It contains fields for the user's email and password, along with their corresponding getter and setter methods.

#### Fields

- **email**: A String representing the user's email address. This field is used for user identification during the login process.n
- **password**: A String representing the user's password. This field is used to authenticate the user during the login process.

#### Methods

- getEmail(): Returns the email of the user.
- setEmail(String email): Sets the email of the user.
- getPassword(): Returns the password of the user.
- setPassword(String password): Sets the password of the user.

---

### RegisterUserDto.java

The RegisterUserDto class is a Data Transfer Object (DTO) used to encapsulate the registration details of a new user. It includes fields for the user's email, password, and full name, along with their respective getter and setter methods.

#### Fields

- **email**: A String representing the user's email address. This field is essential for user identification and communication.
- **password**: A String representing the user's password. This field is required for user authentication.
- **fullName**: A String representing the user's full name. This field can be used for display purposes and personalization.

#### Methods

- getEmail(): Returns the email of the user.
- setEmail(String email): Sets the email of the user.
- getPassword(): Returns the password of the user.
- setPassword(String password): Sets the password of the user.
- getFullName(): Returns the full name of the user.
- setFullName(String fullName): Sets the full name of the user.
