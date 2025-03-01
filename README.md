# Crypto Database Project "FlipCoin" by Shan Sindy, Karzan Rashid, Akam Gerdi
# (02/28/2025)
## Project Overview
This project is a **relational database** designed to manage cryptocurrency transactions, users, and role-based access control. The database is implemented in **MySQL** and follows a well-structured **ER diagram** to ensure data integrity.

## Repository Contents
- `CreateCryptoDBMS.sql` - Creates database tables and schema.
- `ExampleDataCrypto.sql` - Populates the database with sample data.
- `ExampleQueriesCrypto.sql` - Executes SQL queries for data retrieval.
- `ER_diagram.png` - The Entity-Relationship Diagram.
- `Crypto Database Project.pdf` - The final presentation file (02/28/2025).

## Technologies Used
- **MySQL** for database management.
- **SQL constraints** like `FOREIGN KEY`, `UNIQUE`, and `CHECK` for data integrity.
- **Django & Vue.js (Future Work)** for frontend and API integration.
- **Binance/CoinGecko API (Planned)** for real-time price updates.

## Features
- Secure user authentication & role-based access  
- Automated transaction tracking using foreign key constraints  
- Prevents orphaned transactions using `ON DELETE CASCADE`  
- `LEFT JOIN` to ensure all users appear in reports  
- Supports **real-time crypto price updates** (future feature)  

## SQL Queries Examples
```sql
-- Retrieve all users
SELECT * FROM Users;

-- Get total crypto holdings per user
SELECT 
    U.Username, 
    IFNULL(SUM(T.Amount), 0) AS TotalHoldings
FROM Users U
LEFT JOIN Transactions T ON U.UserID = T.UserID AND T.TransactionType = 'BUY'
GROUP BY U.Username;
