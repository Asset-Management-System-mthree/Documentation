### AuthenticationController.java

The AuthenticationController class provides RESTful endpoints for user registration and login, handling requests within the /auth route. It integrates with AuthenticationService for authentication logic and JwtService to generate JWT tokens upon successful login.

#### Key Components

- **JwtService**: Manages JWT token generation.
- **AuthenticationService**: Handles user registration and authentication logic.

#### Endpoints

- **POST /auth/signup**:
  - Registers a new user.
  - Accepts a RegisterUserDto object containing registration details.
  - Calls authenticationService.signup() to create the user.
  - Returns the registered User object.

- **POST /auth/login**:
  - Authenticates an existing user.
  - Accepts a LoginUserDto object containing login credentials.
  - Calls authenticationService.authenticate() for verification.
  - Generates a JWT token using JwtService.generateToken() if authentication is successful.
  - Returns a LoginResponse with the JWT token and expiration time.

---

### BitcoinDataController.java

The BitcoinDataController class provides an endpoint to fetch and store current Bitcoin data. It relies on the BitcoinDataService for data handling, which retrieves and saves Bitcoin information.

#### Key Component

- **BitcoinDataService**: Handles logic for fetching and storing Bitcoin data.

#### Endpoint

- **GET /api/fetch-bitcoin-data**:
  - Triggers the retrieval and storage of the current Bitcoin data.
  - Calls bitcoinDataService.fetchAndStoreBitcoinData() to perform data operations.
  - Returns a success message confirming that the Bitcoin data has been successfully fetched and saved.
---

### GoldDataController.java

The GoldDataController class provides an endpoint to fetch and store current gold data. It utilizes the GoldDataService to handle the logic for retrieving and saving gold information.

#### Key Component

- **GoldDataService**: A service class responsible for the operations related to fetching and storing gold data.

#### Endpoint

- **GET /api/gold/fetch**:
  - Invokes the retrieval and storage of current gold data.
  - Calls goldDataService.fetchAndStoreGoldData() to perform the data fetching and storage process.
  - Returns a confirmation message indicating that the gold data has been successfully fetched and stored.

---

### StockController.java

The StockController class provides an endpoint to retrieve predicted stock prices based on user input. It communicates with the `StockService` to fetch predictions from an external source, such as a Flask API.

#### Key Component

- **StockService**: A service class that contains the logic for retrieving predicted stock prices.

#### Endpoint

- **GET /stock/predict**:
  - Accepts a query parameter ticker that represents the stock ticker symbol for which the prediction is requested.
  - Calls stockService.getPredictedStockPrice(ticker) to retrieve the predicted stock price.
  - Returns the predicted stock price as a string response.

---
### StockDataController.java

The StockDataController class provides endpoints for fetching stock data and analyzing stock price changes. It interacts with the StockDAtaYahooFetch service to retrieve stock information and the StockDataAnalysisService for analyzing percentage changes.

#### Key Components

- **StockDAtaYahooFetch**: A service responsible for fetching and storing stock data from Yahoo Finance.
- **StockDataAnalysisService**: A service that analyzes stock data, particularly focusing on percentage changes in stock prices.

#### Endpoints

- **POST /api/stocks/fetch**:
  - Triggers the fetching and storing of stock data for a predefined list of top NASDAQ stock symbols.
  - Retrieves stock data for the specified symbols using stockDAtaYahooFetch.fetchAndStoreStockData(stockSymbols).

- **GET /api/stocks/{symbol}/percentage-changes**:
  - Accepts a path variable symbol representing the stock ticker symbol.
  - Calls stockDataAnalysisService.getPercentageIncrease(symbol) to retrieve a map of percentage changes for the specified stock.
  - Returns the percentage changes as a ResponseEntity<Map<String, BigDecimal>>.



### UserController.java

The UserController class provides endpoints for retrieving information about authenticated users and all registered users in the system. It utilizes the UserService to interact with user data.

#### Key Component

- **UserService**: A service class responsible for user-related operations, including fetching user details.

#### Endpoints

- **GET /users/me**:
  - Retrieves the currently authenticated user's information.
  - Uses SecurityContextHolder to access the authentication details of the current user.
  - Returns the User object representing the authenticated user as a ResponseEntity.

- **GET /users/**:
  - Retrieves a list of all registered users in the system.
  - Calls userService.allUsers() to fetch the user data.
  - Returns a list of User objects as a ResponseEntity.

