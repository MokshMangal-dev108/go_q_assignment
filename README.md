# Order Management System for Deribit API

## Overview
This project implements a high-performance order management and market data system for interacting with the Deribit API. The system is designed to handle various functionalities such as placing, canceling, and modifying orders, viewing order books, managing positions, and streaming real-time market data using WebSocket. The focus is on achieving low-latency performance with proper error handling and logging.

## Features
### Order Management Functions
1. **Place Order**: Allows users to place buy or sell orders for supported instruments.
2. **Cancel Order**: Provides the functionality to cancel an existing order by its ID.
3. **Modify Order**: Enables users to modify the details of an existing order.
4. **Get Orderbook**: Retrieves the order book for a specified instrument.
5. **View Current Positions**: Displays the user's current positions for a specific currency.

### Real-Time Market Data Streaming
1. Implements a WebSocket server to stream continuous market updates.
2. Supports client subscriptions to symbols for orderbook updates.
3. Provides real-time data for Spot, Futures, and Options instruments.

### Market Coverage
- **Instruments**: Spot, Futures, and Options.
- **Scope**: Covers all supported symbols on the Deribit platform.

## Technical Details
### Core Components
1. **WebSocket Client**: Handles connection to Deribit's WebSocket API for sending and receiving real-time data.
2. **WebSocket Server**: Distributes real-time market updates to clients efficiently.
3. **Error Handling and Logging**: Ensures the system handles errors gracefully and logs relevant events for debugging and monitoring.

### Performance Optimization
- Low-latency performance achieved through:
  - Efficient memory management.
  - Optimized thread usage.
  - Asynchronous communication.

### Dependencies
- **C++ Libraries**:
  - [WebSocket++](https://github.com/zaphoyd/websocketpp) for WebSocket communication.
  - [nlohmann/json](https://github.com/nlohmann/json) for JSON parsing and serialization.
  - OpenSSL for secure communication.

### Key Classes and Methods
#### Class: `TestTrading`
- **`connect(const std::string& uri)`**: Connects to the specified WebSocket server.
- **`disconnect()`**: Closes the WebSocket connection.
- **`send_message(const std::string& message)`**: Sends a JSON-encoded message over the WebSocket.
- **`placeOrder(...)`**: Places a new buy/sell order.
- **`cancelOrder(const std::string& orderId)`**: Cancels an order by ID.
- **`modifyOrder(...)`**: Modifies the details of an existing order.
- **`getOrderBook(const std::string& instrument, int depth)`**: Fetches the order book for a given instrument.
- **`viewPositions(const std::string& currency)`**: Retrieves the user's current positions.
- **`subscribe(const std::string& instrument, const std::string& interval)`**: Subscribes to real-time updates for a specific instrument.
- **`unsubscribe()`**: Unsubscribes from all real-time updates.

## Installation and Usage
### Prerequisites
1. **Compiler**: A C++17-compliant compiler.
2. **Build System**: CMake (recommended).
3. **Libraries**: WebSocket++, nlohmann/json, OpenSSL.
4. **Deribit Account**: Ensure you have API credentials (Client ID and Client Secret).

### Build Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/MokshMangal-dev108/order-management-system.git
   cd order-management-system
   ```
2. Create a build directory and navigate to it:
   ```bash
   mkdir build && cd build
   ```
3. Run CMake:
   ```bash
   cmake ..
   ```
4. Build the project:
   ```bash
   make
   ```

### Running the Application
1. Launch the application:
   ```bash
   ./order-management
   ```
2. Modify the `main()` function to test specific functionalities like placing orders, viewing positions, or streaming market data.

## Configuration
- Update API credentials in the `auth()` method of the `TestTrading` class.
- Modify the WebSocket URI if using a different environment (e.g., production or test).

## Example Usage
### Place an Order
```cpp
tradingws.placeOrder("buy", "BTC-PERPETUAL", 10);
```

### Subscribe to Market Data
```cpp
tradingws.subscribe("ETH-PERPETUAL", "100ms");
```

### Cancel an Order
```cpp
tradingws.cancelOrder("order-id");
```

## Known Issues
1. Ensure the WebSocket connection is properly established before sending messages.
2. Validate API credentials and permissions for private methods.

## Future Enhancements
1. Improve reconnection logic for WebSocket failures.
2. Add more comprehensive logging and monitoring tools.
3. Enhance UI/UX for better interaction with the system.
4. Extend coverage for additional exchanges and instruments.

---

**Author**: Moksh Mangal

