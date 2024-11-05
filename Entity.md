## BitCoinData.java

This class represents the entity for Bitcoin data in the application, mapped to the bitcoin_data table in the database. It contains various attributes that correspond to the fields in the table.

### Annotations
- @Entity: Specifies that this class is an entity and is mapped to a database table.
- @Table(name = "bitcoin_data"): Defines the name of the table in the database to which this entity is mapped.
- @Id: Specifies the primary key of the entity.
- @GeneratedValue(strategy = GenerationType.IDENTITY): Indicates that the primary key should be generated automatically by the database.
- @Column: Specifies the details of the column to which a field is mapped.

### Fields
- private Long id: The unique identifier for the Bitcoin data entry.
- private String symbol: The symbol representing the Bitcoin data (e.g., "BTC").
- private LocalDate date: The date of the Bitcoin data entry.
- private BigDecimal open: The opening price of Bitcoin on the given date.
- private BigDecimal high: The highest price of Bitcoin on the given date.
- private BigDecimal low: The lowest price of Bitcoin on the given date.
- private BigDecimal close: The closing price of Bitcoin on the given date.
- private Long volume: The trading volume of Bitcoin on the given date.

### Getters and Setters
The class includes standard getter and setter methods for each field to access and modify the values. These methods are essential for the Java Persistence API (JPA) to interact with the database.

### Example Usage
This entity is typically used in conjunction with a repository to perform CRUD (Create, Read, Update, Delete) operations on the Bitcoin data in the database.

---


## GoldData.java

This class represents the entity for gold market data in the application, mapped to the `gold_data` table in the database. It includes attributes that correspond to the fields in the table, capturing essential information about gold prices over time.

### Annotations
- @Entity: Specifies that this class is an entity and is mapped to a database table.
- @Table(name = "gold_data"): Defines the name of the table in the database to which this entity is mapped.
- @Id: Specifies the primary key of the entity.
- @GeneratedValue(strategy = GenerationType.IDENTITY): Indicates that the primary key should be generated automatically by the database.
- @Column: Specifies the details of the column to which a field is mapped.

### Fields
- private Long id: The unique identifier for the gold data entry.
- private String symbol: The symbol representing the gold data (e.g., "XAU").
- private LocalDate date: The date of the gold data entry.
- private BigDecimal open: The opening price of gold on the given date.
- private BigDecimal high: The highest price of gold on the given date.
- private BigDecimal low: The lowest price of gold on the given date.
- private BigDecimal close: The closing price of gold on the given date.
- private Long volume: The trading volume of gold on the given date.

### Getters and Setters
The class includes standard getter and setter methods for each field to access and modify the values. These methods are essential for the Java Persistence API (JPA) to interact with the database.

### Example Usage
This entity is typically used in conjunction with a repository to perform CRUD (Create, Read, Update, Delete) operations on the gold data in the database.

---

## StockData.java

This class represents the entity for stock market data in the application, mapped to the stock_data table in the database. It includes attributes that correspond to the fields in the table, capturing essential information about stock prices over time.

### Annotations
- @Entity: Specifies that this class is an entity and is mapped to a database table.
- @Table(name = "stock_data", uniqueConstraints = {@UniqueConstraint(columnNames = {"stock_symbol", "date"})}): Defines the name of the table in the database and enforces a unique constraint on the combination of `stock_symbol` and `date` to prevent duplicate entries.
- @Id: Specifies the primary key of the entity.
- @GeneratedValue(strategy = GenerationType.IDENTITY): Indicates that the primary key should be generated automatically by the database.
- @Column: Specifies the details of the column to which a field is mapped.

### Fields
- private Long id: The unique identifier for the stock data entry.
- private String stockSymbol: The symbol representing the stock (e.g., "AAPL" for Apple Inc.).
- private LocalDate date: The date of the stock data entry.
- private BigDecimal open: The opening price of the stock on the given date.
- private BigDecimal high: The highest price of the stock on the given date.
- private BigDecimal low: The lowest price of the stock on the given date.
- private BigDecimal close: The closing price of the stock on the given date.
- private Long volume: The trading volume of the stock on the given date.

### Getters and Setters
The class includes standard getter and setter methods for each field to access and modify the values. These methods are essential for the Java Persistence API (JPA) to interact with the database.

### Example Usage
This entity is typically used in conjunction with a repository to perform CRUD (Create, Read, Update, Delete) operations on the stock data in the database.

---
## User.java

This class represents the user entity in the application, mapped to the `users` table in the database. It implements the `UserDetails` interface from Spring Security, enabling it to provide user authentication and authorization information.

### Annotations
- @Entity: Indicates that this class is an entity and is mapped to a database table.
- @Table(name = "users"): Specifies the name of the table in the database.
- @Id: Marks the primary key of the entity.
- @GeneratedValue(strategy = GenerationType.AUTO): Indicates that the primary key should be generated automatically.
- @Column: Specifies the details of the column to which a field is mapped.
- @CreationTimestamp: Automatically sets the creation timestamp of the user record.
- @UpdateTimestamp: Automatically sets the update timestamp of the user record.

### Fields
- private Integer id: The unique identifier for the user.
- private String fullName: The full name of the user.
- private String email: The unique email address of the user (used as the username).
- private String password: The hashed password of the user.
- private Date createdAt: The timestamp when the user account was created.
- private Date updatedAt: The timestamp when the user account was last updated.

### Implemented Methods from UserDetails
- getAuthorities(): Returns the authorities granted to the user. This implementation currently returns an empty list.
- getPassword(): Returns the user's password.
- getUsername(): Returns the user's email as the username.
- isAccountNonExpired(): Indicates if the user's account is non-expired (always returns true).
- isAccountNonLocked(): Indicates if the user's account is non-locked (always returns true).
- isCredentialsNonExpired(): Indicates if the user's credentials are non-expired (always returns true).
- isEnabled(): Indicates if the user's account is enabled (always returns true).

### Getters and Setters
The class includes standard getter and setter methods for each field to access and modify the values. This is essential for JPA to interact with the database and for the application to manage user details effectively.

### Example Usage
This entity is used for user management within the application, allowing for user registration, authentication, and profile management. It integrates with Spring Security for handling authentication processes.
