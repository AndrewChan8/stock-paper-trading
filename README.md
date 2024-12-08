# CS422

## Abstract

MooDengCapital is a papertrading service that aims to make pragmatic and risk-free education accessible to all. Through becoming 
a registered trader, users are provided a clean-slate balance of $10,000 to build a financial portfolio of real stocks. Additionally, a watchlist page is available to each user, where they can monintor and group certain stocks of interest. Through buying and selling stocks with real-time prices, users can analyze trends and learn about the inner workings of the stokc market all while developing a simulated portfolio. 

## Authors

Miles Anderson, Liam Bouffard, Andrew Chan, Jacob Kolster </br>
Team: MooDeng </br>
Class: CS 422, Fall 2024 </br>
Last Modified: 12/2/2024

## Installation

### Requirements
The project requires these tools:
* PostgreSQL
* .env file
* Node.js
* Npm (Node Package Manager)

### Mac
Installation Instructions for mac can be found in the submission documents.

### Repository
Download the repository with the following command: 
```
git clone https://github.com/AndrewChan8/CS422.git
```

## `node.js` & `npm` Installation

Node.js is a javascript runtime environment that is used to help build web applications. NPM is a common 
package manager used in conjunction with node.js. Both of these can be installed succinctly for MacOS and 
Windows using the pre-built installer at [https://nodejs.org/en/download/prebuilt-installer](https://nodejs.org/en/download/prebuilt-installer).

Linux users can install node.js and npm through `nvm` by following and running the commands posted at:
[https://nodejs.org/en/download/package-manager](https://nodejs.org/en/download/package-manager)

## PostgreSQL & Database Setup

Follow these steps to set up PostgreSQL and create the `MooDengCapital` database.

### Step 1: Install PostgreSQL

First, download and install PostgreSQL by visiting the official website:  
[Download PostgreSQL](https://www.postgresql.org/).

Alternatively, you can install PostgreSQL via a package manager. On Ubuntu, use:

    sudo apt-get update
    sudo apt-get install postgresql postgresql-contrib

### Step 2: Verify Installation
After installation, verify that PostgreSQL is installed by checking the version:

    psql --version

This will show you the installed version of PostgreSQL.

### Step 3: Access PostgreSQL

Log into PostgreSQL as the postgres user:

    sudo -u postgres psql

### Step 4: Create the Database

Inside the PostgreSQL prompt, create the MooDengCapital database:

    CREATE DATABASE "MooDengCapital";

### Step 5: Set a Password for the postgres User

You can set a password for the postgres user (the default superuser) to secure your database:

    ALTER ROLE postgres WITH PASSWORD 'tempPassword';

### Step 6: Connect to the MooDengCapital Database

Once the service is running, connect to the MooDengCapital database:

    \c MooDengCapital

### Step 7: Execute SQL Script

To create the necessary tables and structure for your project, execute the SQL script (db.sql) in the PostgreSQL shell:

    \i /path/to/db.sql

Replace /path/to/db.sql with the correct path to your db.sql file (e.g., ./server/db.sql).

This will create the required tables in the MooDengCapital database.

### Step 8: Start PostgreSQL Service (If Not Already Running)

Ensure that the PostgreSQL service is running. You can start it with the following command:

    sudo systemctl start postgresql


## Final Startup

To startup the web application on your local host, you will need to download the repo and have both the frontend and backend server running. 
#### Starting Backend
open a terminal, cd into the `server` directory and execute `node server.js`. 
#### Starting Frontend
open another terminal, cd into the `client` directory and execute `npm start`.



## Overview of Pages

### Sign-Up/Sign-In

Sign-Up used to register a username, email, and password with a new trader account, automatically signs in on completion. Sign-in used to connect with already registered trader account. This is necessary to access functionality such as buying/selling stock or adding a stock to the watchlist

### Home Page

Used to search stocks by their ticker. Given a successful search a user has an option to add any number of shares that don't exceed the
balance of their portfolio, or add the stock to their watchlist. By default Google (GOOG) is shown.

### Watchlists Page

Users can add stocks of interest to their watchlist page. Instead of buying stocks, here they can monitor them to keep track of trends
within the market. 

### Profile Page

The center for a trader's financial overview! Displays all shares within a user's portfolio, as well as other vital information such as
liquid money, asset money, and net worth.


## Further Reading

Dedicated READMEs are provided for the backend and frontend in the `server` and `client` directories respectively.
