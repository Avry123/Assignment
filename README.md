# Crypto Data Fetching and Storage Server

Overview
This Node.js application serves as a server for fetching cryptocurrency data from the WazirX API, processing it, and storing it in a MySQL database. Additionally, it provides a web interface for users to view the fetched data.

Dependencies
The application uses the following Node.js modules:

express: A web application framework for Node.js.
express-ejs-layouts: Middleware for Express.js to simplify rendering of views.
mysql: A Node.js driver for MySQL to interact with the database.
axios: A promise-based HTTP client for making API requests.
node-cron: A cron-like job scheduler for Node.js.

Configuration
Ensure that you have Node.js and npm installed on your machine.

Install Dependencies:

bash
Copy code
npm install express express-ejs-layouts mysql axios node-cron
MySQL Setup:

Make sure MySQL is running.
Create a database named crypto_data.
Adjust the database configuration in the code if needed.
Table Creation:

Set up the MySQL table using the provided SQL script:
sql
Copy code
CREATE TABLE crypto_prices (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    last FLOAT NOT NULL,
    buy FLOAT NOT NULL,
    sell FLOAT NOT NULL,
    volume FLOAT NOT NULL,
    base_unit VARCHAR(50) NOT NULL,
    UNIQUE KEY (name)
);
Usage
Start the Server:

bash
Copy code
node index.js
Access the Web Interface:

Open http://localhost:3000/ in your browser.
The page displays cryptocurrency data and allows users to fetch and store the latest data.
Manual Data Fetching:

To fetch and store data manually, visit http://localhost:3000/fetchAndStoreData or click the "GO BACK" link after data retrieval.
Functionality
Fetching Data: The server fetches cryptocurrency data from the WazirX API and processes the top 10 entries.
Storing Data: Fetched data is stored in the MySQL database, and duplicate entries are updated.
Web Interface: Users can view the stored data on the web interface, and the page automatically refreshes every 60 seconds.
Cron Job: A cron job is scheduled to fetch and process data every 60 seconds.
Web Interface
The web interface is powered by the EJS template engine. It consists of a main page (testing.ejs) that displays cryptocurrency data in a table. Users can manually trigger data fetching using the provided link.

Important Note
Ensure that your MySQL database credentials are correctly configured in the code (index.js).

Feel free to customize and extend the application based on your specific requirements.

Note: This README provides a quick overview. For detailed instructions and customization, refer to the comments in the code and relevant documentation.

