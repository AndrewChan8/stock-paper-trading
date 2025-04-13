# 💹 MooDengCapital – Paper Trading Platform

**Authors & Developers**: Andrew Chan, Jacob Kolster, Miles Anderson, Liam Bouffard  
**Team**: MooDeng  
**Last Updated**: December 2, 2024

---

## 📈 Overview

**MooDengCapital** is a simulated paper trading platform designed to provide a risk-free, hands-on introduction to investing. Each registered user begins with a virtual $10,000 balance and can trade real-time priced stocks to build a portfolio, monitor trends, and learn the dynamics of the stock market. Users can also create a personalized watchlist to track stocks of interest without executing trades.

Built with a modern web stack, MooDengCapital features:

- A **React frontend**
- A **Node.js + Express backend**
- A **PostgreSQL database**

---

## 🛠️ Installation Guide

### 📦 Requirements

- Node.js and npm
- PostgreSQL
- `.env` file with configuration variables

---

## 💻 Cloning the Repository

```bash
git clone https://github.com/AndrewChan8/stock-paper-trading.git
```

---

## ⚙️ Node.js & npm Installation

Install both using the [official prebuilt installer](https://nodejs.org/en/download/prebuilt-installer).

Linux users can install via `nvm`:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
nvm install node
```

---

## 🗄️ PostgreSQL Setup

### 1. Install PostgreSQL

- [Download from official site](https://www.postgresql.org/)
- Or on Ubuntu:
  ```bash
  sudo apt-get update
  sudo apt-get install postgresql postgresql-contrib
  ```

### 2. Verify Installation

```bash
psql --version
```

### 3. Access psql

```bash
sudo -u postgres psql
```

### 4. Create the Database

```sql
CREATE DATABASE "MooDengCapital";
```

### 5. Set postgres Password (Optional)

```sql
ALTER ROLE postgres WITH PASSWORD 'tempPassword';
```

### 6. Connect to the Database

```sql
\c MooDengCapital
```

### 7. Execute SQL Schema

```sql
\i /path/to/db.sql
```

Replace `/path/to/db.sql` with the actual path (e.g., `./server/db.sql`).

### 8. Start PostgreSQL Service

```bash
sudo systemctl start postgresql
```

---

## 🚀 Starting the Application

### 🧠 Backend

```bash
cd server
node server.js
```

### 🎨 Frontend

```bash
cd client
npm install
npm start
```

Visit `http://localhost:3000` in your browser to start using MooDengCapital.

---

## 🌐 Pages Overview

### 🔑 Sign-Up / Sign-In

- Register a trader account using username, email, and password.
- Login to access portfolio, watchlist, and trading features.

### 🏠 Home Page

- Search for real stocks by ticker.
- Buy shares (if sufficient funds) or add stocks to your watchlist.
- Default display: Google (GOOG).

### 👀 Watchlist

- Monitor selected stocks without purchasing them.
- Useful for observing trends and planning future trades.

### 👤 Profile Page

- View portfolio holdings and account stats:
  - Liquid cash
  - Asset value
  - Total net worth

---

## 📂 Additional Documentation

Detailed documentation for backend and frontend functionality is available in:

- `server/README.md`
- `client/README.md`

---

## 📬 Contact & Contributions

Feel free to fork the repo, report issues, or open pull requests. We welcome contributions to expand features or improve usability.

📧 [andrewsushi.c8@gmail.com]  
💼 [linkedin.com/in/andrew-chan8]
