# 🧠 MooDengCapital – Backend Server

This is the backend component of the **MooDengCapital** paper trading platform. It provides a RESTful API layer between the frontend (React) and the PostgreSQL database, handling routing, logic, user authentication, and real-time interaction with financial data.

---

## 🚀 Available Scripts

### `node server.js`

Starts the backend server in the `server/` directory.

### `npm install <package>`

Installs required npm dependencies. The backend uses the following packages:

- `axios`
- `bcrypt`
- `bcryptjs`
- `cookie-parser`
- `cors`
- `dotenv`
- `express`
- `jade`
- `morgan`
- `pg`

---

## 🧱 Backend Architecture

The backend follows a **modular MVC-style structure**, separating routes, controllers, and database logic. It exposes API endpoints grouped into three categories:

1. **Core Database CRUD APIs**
2. **External Stock Price API**
3. **User Functional APIs**

---

### 📁 1. Core Database CRUD APIs

Each database table has corresponding controller methods for creating, reading, updating, and deleting records. These controller files are located in the `/controllers` directory and abstract functionality used across multiple API routes.

| Table        | Controller File                   | Example Methods                             |
|--------------|-----------------------------------|----------------------------------------------|
| `stocks`     | `controllers/stockController.js`  | `addStock`, `getStock`, `updatePrice`       |
| `users`      | `controllers/userController.js`   | `createUser`, `deleteUser`, `getUserById`   |
| `portfolios` | `controllers/portfolioController.js` | `createPortfolio`, `changeBalance`       |
| `trades`     | `controllers/transactionsController.js` | `addTrade`, `getTradeHistory`         |
| `watchlists` | `controllers/watchlistController.js` | `addToWatchlist`, `removeFromWatchlist` |

---

### 🌐 2. External Stock Price API (Vanguard)

This service fetches real-time stock prices from a third-party data provider. These prices are used across trading and portfolio calculations. Stock updates are managed via endpoints that interact with the Vanguard API.

---

### 👤 3. User Functional APIs

These high-level APIs drive key application functionality. They often interact with multiple database tables in a single request and encapsulate business logic related to trading, account setup, and portfolio analysis.

#### Example Routes & Logic

| Route                | Description                                                    |
|---------------------|----------------------------------------------------------------|
| `POST /api/signUp`  | Registers a new user and initializes a portfolio               |
| `POST /api/signIn`  | Authenticates and logs in a user                               |
| `POST /api/buyStock`| Executes a stock purchase; updates portfolio & trade history   |
| `POST /api/sellStock`| Sells shares from portfolio and updates balance                |
| `GET /api/calcWorth`| Calculates a user's total net worth using real-time prices     |
| `GET /api/portfolio`| Retrieves all stocks currently held in the user's portfolio    |

These methods typically chain together multiple controller calls and enforce data validation and authentication.

---

## 🗃️ Database Schema Overview

The backend connects to a PostgreSQL instance that stores all platform data. Below is a summary of each major table:

---

### 📊 `stocks`

Stores all unique stocks referenced by portfolios or watchlists.

| Column       | Description                                |
|--------------|--------------------------------------------|
| `stock_id`   | Primary key (int)                          |
| `symbol`     | Ticker symbol (e.g., AAPL)                 |
| `curr_price` | Latest known price                         |
| `created_at` | Timestamp of stock insertion               |

---

### 👤 `users`

Stores all registered traders with secure credentials.

| Column     | Description                                 |
|------------|---------------------------------------------|
| `user_id`  | Primary key                                 |
| `username` | Display name                                |
| `email`    | Unique identifier for login                 |
| `password` | Hashed password using bcrypt                |
| `created_at` | Timestamp of user creation                |

---

### 💼 `portfolios`

Represents a trader’s financial portfolio.

| Column        | Description                                     |
|---------------|-------------------------------------------------|
| `portfolio_id`| Primary key                                     |
| `user_id`     | Foreign key referencing `users`                 |
| `balance`     | Liquid (uninvested) funds in USD                |
| `created_at`  | Timestamp of portfolio creation                 |

---

### 🔁 `trades`

Tracks a trader's complete transaction history.

| Column           | Description                                          |
|------------------|------------------------------------------------------|
| `trade_id`       | Primary key                                          |
| `portfolio_id`   | Foreign key referencing `portfolios`                |
| `symbol`         | Stock symbol                                         |
| `trade_type`     | `'BUY'` or `'SELL'`                                  |
| `quantity`       | Number of shares involved                            |
| `price_per_share`| Execution price at the time of trade                |
| `created_at`     | Timestamp of trade                                   |

> This table is used to reconstruct portfolio holdings and compute total asset value.

---

### 👁️ `watchlists`

Stores user-specific stock watchlists.

| Column        | Description                                 |
|---------------|---------------------------------------------|
| `watchlist_id`| Primary key                                 |
| `name`        | Stock ticker symbol                         |
| `user_id`     | Foreign key referencing `users`             |
| `stock_id`    | Foreign key referencing `stocks`            |
| `created_at`  | Timestamp of when the stock was added       |

A combination of `name` and `user_id` ensures a user doesn’t duplicate a stock in their watchlist.

---

## ✅ Summary

The backend of MooDengCapital provides a structured and extensible API architecture to support a seamless and educational paper trading experience. It is modular, secure, and designed with scalability in mind.

For more details on route structures or extending functionality, explore the `/routes` and `/controllers` directories or contact the team.

