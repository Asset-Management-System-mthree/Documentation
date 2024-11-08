## LoginResponse.java

This class represents the response sent back to the client after a successful login attempt. It contains information necessary for the client to manage user sessions and authenticate future requests.

### Fields
 
- private String token:
  - The authentication token generated upon successful login. This token is used for subsequent requests to authenticate the user.

- private long expiresIn:
  - The duration (in seconds) for which the authentication token is valid. This helps the client know when to refresh or reauthenticate.

### Getters and Setters

1. **getToken**:
   - **Returns**: The authentication token.
   - **Usage**: String token = loginResponse.getToken();

2. **setToken**:
   - **Parameters**: 
     - String token: The authentication token to set.
   - **Returns**: The current instance of LoginResponse, allowing for method chaining.
   - **Usage**: loginResponse.setToken("your_token");

3. **getExpiresIn**:
   - **Returns**: The time in seconds until the token expires.
   - **Usage**: long expiresIn = loginResponse.getExpiresIn();

4. **setExpiresIn**:
   - **Parameters**: 
     - long expiresIn: The duration until token expiration.
   - **Returns**: The current instance of LoginResponse, allowing for method chaining.
   - **Usage**: loginResponse.setExpiresIn(3600);

### Example Usage
An instance of LoginResponse might be created and populated in the authentication service after a successful login, then returned to the client as part of the response body.

```java
LoginResponse response = new LoginResponse()
    .setToken("generated_token")
    .setExpiresIn(3600);


---


## YahooFinanceResponse.java

This class represents the structure of the response received from the Yahoo Finance API. It encapsulates the data related to financial charts and provides methods to access the nested information.

### Fields

- private Chart chart:
  - An instance of the Chart class, representing the financial chart data returned by the Yahoo Finance API.

### Getters and Setters

1. **getChart**:
   - **Returns**: The Chart object containing chart data.
   - **Usage**: Chart chart = yahooFinanceResponse.getChart();

2. **setChart**:
   - **Parameters**: 
     - Chart chart: The Chart object to set.
   - **Usage**: yahooFinanceResponse.setChart(chart);

### Nested Classes

#### Chart

- **Fields**:
  - private Result[] result:
    - An array of Result objects containing detailed financial data.

- **Getters and Setters**:
  - **getResult**: Returns the array of Result objects.
  - **setResult**: Sets the array of Result objects.

#### Result

- **Fields**:
  - private long[] timestamp:
    - An array of timestamps for the financial data points.
  - private Indicators indicators:
    - An instance of the `Indicators` class containing quote data.

- **Getters and Setters**:
  - **getTimestamp**: Returns the array of timestamps.
  - **setTimestamp**: Sets the array of timestamps.
  - **getIndicators**: Returns the Indicators object.
  - **setIndicators**: Sets the Indicators object.

#### Indicators

- **Fields**:
  - private Quote[] quote:
    - An array of Quote objects containing market data such as open, high, low, close prices, and volume.

- **Getters and Setters**:
  - **getQuote**: Returns the array of Quote objects.
  - **setQuote**: Sets the array of Quote objects.

#### Quote

- **Fields**:
  - private Double[] open:
    - An array of opening prices.
  - private Double[] high:
    - An array of highest prices.
  - private Double[] low:
    - An array of lowest prices.
  - private Double[] close:
    - An array of closing prices.
  - private Long[] volume:
    - An array of trading volumes.

- **Getters and Setters**:
  - **getOpen**: Returns the array of opening prices.
  - **setOpen**: Sets the array of opening prices.
  - **getHigh**: Returns the array of highest prices.
  - **setHigh**: Sets the array of highest prices.
  - **getLow**: Returns the array of lowest prices.
  - **setLow**: Sets the array of lowest prices.
  - **getClose**: Returns the array of closing prices.
  - **setClose**: Sets the array of closing prices.
  - **getVolume**: Returns the array of trading volumes.
  - **setVolume**: Sets the array of trading volumes.

### Example Usage
An instance of YahooFinanceResponse might be created when receiving a response from the Yahoo Finance API, allowing for easy access to the financial data.

```java
YahooFinanceResponse response = objectMapper.readValue(jsonResponse, YahooFinanceResponse.class);
Chart chart = response.getChart();
Result[] results = chart.getResult();


---

## AuthApplication.java

This class is the entry point of the Spring Boot application for authentication services. It is responsible for bootstrapping the application and enabling scheduling capabilities.

### Annotations

- @SpringBootApplication:
  - Indicates that this class serves as the main configuration class for the Spring Boot application. It combines three annotations:
    - @Configuration: Indicates that this class contains Spring bean definitions.
    - @EnableAutoConfiguration: Enables Spring Boot’s auto-configuration feature, which automatically configures the application based on the dependencies on the classpath.
    - @ComponentScan: Scans for Spring components (like controllers, services, etc.) in the specified package and its sub-packages.

- @EnableScheduling:
  - Enables support for scheduled tasks in the application. This allows for the use of the `@Scheduled` annotation to define methods that should run at specified intervals.

### Main Method

- **Signature**: 
  ```java
  public static void main(String[] args)
