# Online Shopping Management System (OSMS)
**Overview**

The Online Shopping Management System (OSMS) is a database-driven project designed to manage various aspects of an online shopping platform. This includes customer management, product inventory, orders, reviews, payments, shipments, and more. The project uses SQL to create and manipulate a database schema, enforce constraints, and implement business logic.

# Features

1. **Customer Management:**

   * Maintain customer profiles including personal details and addresses.

2. **Product and Category Management:**

    * Organize products into categories for better discoverability.

3. **Order Management:**

   * Manage orders, order details, and track shipments.

4. **Supplier Management:**

   * Maintain supplier information and their associated products.

5. **Cart and Wishlist:**

    * Allow customers to add items to carts and wishlists.

6. **Review System:**

   * Customers can leave reviews and ratings for purchased products.

7. **Payment and Discounts:**

   * Process payments using various methods and apply discounts.

8. **Return Management:**

   * Handle product returns.

9. **Analytics:**

   * Generate reports on product popularity, average prices, and customer activity.

10. **Triggers and Procedures:**

   * Enforce business rules using triggers and reusable stored procedures.

11. **Transactions:**

   * Ensure data integrity through SQL transactions.
    
# Database Schema
The OSMS database comprises the following tables:

* **Customers:** Store customer information.

* **Categories:** Maintain product categories.

* **Products:** Manage product details.

* **Orders:** Track customer orders.

* **OrderDetails:** Record details of items in each order.

* **Suppliers:** Maintain supplier information.

* **ProductSuppliers:** Define relationships between products and suppliers.

* **Shippers:** Store information on shipping companies.

* **Shipments:** Manage shipment details.

* **Reviews:** Allow customers to leave feedback on products.

* **PaymentMethods:** Define available payment methods.

* **Payments:** Track payment transactions.

* **Discounts:** Define discount codes and their values.

* **OrderDiscounts:** Track discounts applied to orders.

* **Carts:** Manage customer shopping carts.

* **CartItems:** Store items in customer carts.

* **Addresses:** Record customer addresses.

* **Wishlists:** Allow customers to save desired products.

* **WishlistItems:** Manage items in customer wishlists.

* **Returns:** Track product returns.

# Key SQL Concepts Used
1. **Constraints:**

    * Primary keys, foreign keys, and unique constraints.

    * Check constraints for validating data (e.g., ratings between 1 and 5).

2. **Joins:**

    * Inner joins for creating views like CustomerOrders and ProductReviews.

3. **Aggregate Functions:**

    * Generate summaries using COUNT, AVG, etc., with GROUP BY and HAVING clauses.

4. **Subqueries:**

    * Nested SQL queries for advanced filtering.

5. **Triggers:**

    * Automate business rules (e.g., preventing past order dates, auto-creating shipments).

6. **Stored Procedures:**

    * Reusable SQL blocks for fetching customer orders and product details.

7. **Transactions:**

    * Implement SAVEPOINT, ROLLBACK, and COMMIT to ensure atomicity.

# Sample Data
Sample data has been added for testing:

  * Customers, categories, products, orders, payments, and more.

Example:
```
INSERT INTO Customers (FirstName, LastName, Email)
VALUES ('Jerin', 'Achol', 'achol@gmail.com');
```

# Installation and Usage

1. Install a MySQL-compatible database server.

2. Create the database:
   ```
   CREATE DATABASE OSMS;
   ```
3. Import the provided SQL script to set up the schema and sample data.

4. Use a database management tool or command-line interface to query the database.

# SQL Code Highlights

**Creating Views**
```
CREATE VIEW CustomerOrders AS
SELECT Customers.FirstName, Customers.LastName, Orders.OrderID, Orders.OrderDate
FROM Customers
JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```
# Stored Procedure
```
DELIMITER //
CREATE PROCEDURE GetCustomerOrders (IN custID INT)
BEGIN
    SELECT * FROM Orders
    WHERE CustomerID = custID;
END //
DELIMITER;
```
# Trigger
```
DELIMITER //
CREATE TRIGGER BeforeOrderInsert
BEFORE INSERT ON Orders
FOR EACH ROW
BEGIN
    DECLARE msg VARCHAR(255);
    IF NEW.OrderDate < CURDATE() THEN
        SET msg = 'Order date cannot be in the past.';
        SIGNAL SQLSTATE '45000' SET MESSAGE_TEXT = msg;
    END IF;
END //
DELIMITER;
```

# Team Members And Contribution
* **Jerin Nur Khan Achol:** Focused on creating triggers, views, and implementing complex joins and stored procedures. Additionally, worked on compiling and structuring the project report.
* **Sohi Bilkis Binte Yer:** Worked on implementing SQL operators and nested SQL queries to enhance data retrieval and manipulation capabilities. And Worked on HAVING clause and aggregate functions for advanced data analysis.
* **Sadia Sumona Shanta:** Responsible for designing and creating database tables.
* **Azra Jerin:** Responsible for inserting sample data to support functionality testing.
# License

This project is licensed under Team Venus. See the LICENSE file for more information.



