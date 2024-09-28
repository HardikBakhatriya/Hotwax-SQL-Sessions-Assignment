# Hotwax-SQL-Sessions-Assignment1
 Q1.Cretating table through the E-R Diagram and establishing the relationship for the same.
 CREATE TABLE orders (
    order_id VARCHAR(45) PRIMARY KEY,
    product_id VARCHAR(20),
    user_id VARCHAR(45),
    total DOUBLE,
    date DATE,
    status VARCHAR(50)
);

CREATE TABLE products (
    product_id VARCHAR(20) PRIMARY KEY,
    product_name VARCHAR(100),
    product_description TEXT,
    product_returnable VARCHAR(45),
    owner_id VARCHAR(105)
);

CREATE TABLE users (
    user_id VARCHAR(20) PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);

CREATE TABLE address (
    pincode VARCHAR(10) PRIMARY KEY,
    city VARCHAR(255),
    state VARCHAR(256)
);

ALTER TABLE orders
ADD FOREIGN KEY (product_id) REFERENCES products(product_id);

ALTER TABLE orders
ADD FOREIGN KEY (user_id) REFERENCES users(user_id);

ALTER TABLE users
ADD FOREIGN KEY (pincode) REFERENCES address(pincode);


Q2.Writing sql query for the given requirements 
1) Check status of your order.
SELECT status FROM orders WHERE order_id = :order_id;
  
2) Find total amount of your orders.
SELECT SUM(total) AS total_amountFROM orders WHERE user_id = :user_id;

3)Update your city.
UPDATE address SET city = :new_city WHERE pincode = :pincode;

4) Change product description.
UPDATE products SET product_description = :new_description WHERE product_id = :product_id;

5) Display returnable products.
SELECT product_id, product_name FROM products WHERE product_returnable = 'yes';
