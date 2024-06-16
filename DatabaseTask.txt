create database Task;

use Task;

create table CustomerTable(CustomerID int not null primary key, 
FirstName varchar(50),LastName varchar(50),Email varchar(50),
PhoneNumber bigint,AddressLine1 varchar(100),AddressLine2 varchar(100),City varchar(50),
State varchar(50),PostalCode varchar(50),Country varchar(50) ) ;

Insert into CustomerTable (CustomerID,FirstName ,LastName,Email,PhoneNumber
,AddressLine1,AddressLine2,City,State,PostalCode,Country)Values(101,
'gaurav','dakare','gaurav@gmail.com',9665755122,'jivadani Road','sahakar nagar',
'Virar','maharashtra','401305','india');

select * from CustomerTable;

INSERT INTO CustomerTable (CustomerID, FirstName, LastName, Email, PhoneNumber,
    AddressLine1, AddressLine2, City, State, PostalCode, Country)
VALUES 
    (102, 'Priya', 'Sharma', 'priya.sharma@example.com', 9988776655,
     '456 Second St', 'Flat 2B', 'Delhi', 'Delhi', '110001', 'India'),
    
    (103, 'Amit', 'Patel', 'amit.patel@example.com', 7766554433,
     '789 Third St', 'Building A', 'Bangalore', 'Karnataka', '560001', 'India'),
    
    (104, 'Anjali', 'Desai', 'anjali.desai@example.com', 5544332211,
     '321 Fourth St', 'Tower B', 'Chennai', 'Tamil Nadu', '600001', 'India'),
    
    (105, 'Raj', 'Kumar', 'raj.kumar@example.com', 6677889900,
     '555 Fifth St', 'Apartment 5C', 'Kolkata', 'West Bengal', '700001', 'India'),
    
    (106, 'Neha', 'Joshi', 'neha.joshi@example.com', 1122334455,
     '987 Sixth St', 'Flat 3A', 'Hyderabad', 'Telangana', '500001', 'India'),
    
    (107, 'Vikram', 'Singh', 'vikram.singh@example.com', 3344556677,
     '741 Seventh St', 'Tower C', 'Pune', 'Maharashtra', '411001', 'India'),
    
    (108, 'Pooja', 'Shah', 'pooja.shah@example.com', 8899776655,
     '852 Eighth St', 'Building D', 'Ahmedabad', 'Gujarat', '380001', 'India'),
    
    (109, 'Sanjay', 'Verma', 'sanjay.verma@example.com', 6677889900,
     '369 Ninth St', 'Flat 4B', 'Jaipur', 'Rajasthan', '302001', 'India'),
    
    (110, 'Sunita', 'Reddy', 'sunita.reddy@example.com', 9988776655,
     '456 Tenth St', 'Apartment 2A', 'Lucknow', 'Uttar Pradesh', '226001', 'India'),
	 (111, 'Rahul', 'Gupta', 'rahul.gupta@example.com', 9876543210,
     '123 Main St', 'Apartment 1', 'Mumbai', 'Maharashtra', '400001', 'India');


	 create table OrderTable(OrderID int Not null primary key,
	 CustomerID int not null references CustomerTable(CustomerID),
	 OrderDate date,Totalamount bigint,OrderStatus varchar(50),
	 ShippingAddress varchar(50),BillingAddress varchar(50));

	 INSERT INTO OrderTable (OrderID, CustomerID, OrderDate, TotalAmount, OrderStatus, ShippingAddress, BillingAddress)
VALUES
    (1, 101, '2024-06-01', 15000, 'Shipped', '123 Main St, Mumbai', '123 Main St, Mumbai'),
    
    (2, 102, '2024-06-02', 20000, 'Processing', '456 Second St, Delhi', '456 Second St, Delhi'),
    
    (3, 103, '2024-06-03', 10000, 'Delivered', '789 Third St, Bangalore', '789 Third St, Bangalore'),
    
    (4, 104, '2024-06-04', 30000, 'Shipped', '321 Fourth St, Chennai', '321 Fourth St, Chennai'),
    
    (5, 105, '2024-06-05', 25000, 'Processing', '555 Fifth St, Kolkata', '555 Fifth St, Kolkata'),
    
    (6, 101, '2024-06-06', 1800, 'Delivered', '987 Sixth St, Hyderabad', '987 Sixth St, Hyderabad'),
    
    (7, 107, '2024-06-07', 22000, 'Shipped', '741 Seventh St, Pune', '741 Seventh St, Pune'),
    
    (8, 103, '2024-06-08', 27000, 'Processing', '852 Eighth St, Ahmedabad', '852 Eighth St, Ahmedabad'),
    
    (9, 104, '2024-06-09', 19000, 'Delivered', '369 Ninth St, Jaipur', '369 Ninth St, Jaipur'),
    
    (10, 101, '2024-06-10', 3200, 'Shipped', '456 Tenth St, Lucknow', '456 Tenth St, Lucknow');


	select * from OrderTable;

	create table ProductTable(ProductID int primary key ,
	ProductName varchar(50),ProductDescription varchar(100),
	Price Bigint,StockQuantity bigint);

	INSERT INTO ProductTable (ProductID, ProductName, ProductDescription, Price, StockQuantity)
VALUES
    (1, 'Laptop', 'High-performance laptop with SSD storage', 80000, 50),
    
    (2, 'Smartphone', 'Flagship smartphone with OLED display', 60000, 100),
    
    (3, 'Tablet', 'Lightweight tablet for work and entertainment', 40000, 75),
    
    (4, 'Headphones', 'Wireless headphones with noise-cancellation', 12000, 200),
    
    (5, 'Smartwatch', 'Fitness tracker with heart rate monitoring', 15000, 150),
    
    (6, 'Camera', 'Professional DSLR camera with 4K video recording', 90000, 30),
    
    (7, 'Printer', 'All-in-one printer for home and office use', 25000, 80),
    
    (8, 'Speaker', 'Wireless speaker with surround sound', 18000, 100),
    
    (9, 'Monitor', 'Ultra-wide monitor for immersive gaming', 70000, 50),
    
    (10, 'Keyboard', 'Mechanical gaming keyboard with RGB lighting', 10000, 120);


	select * from ProductTable;

	Q1
	List all customers and their orders 

	SELECT c.CustomerID ,c.FirstName ,c.LastName,o.OrderID ,o.OrderDate ,o.OrderStatus ,o.Totalamount ,o.OrderDate  from CustomerTable c  
	inner join OrderTable o on o.CustomerID=c.CustomerID 
	order by c.CustomerID ;

	Q2

	SELECT
    p.ProductID,
    p.ProductName,
    p.ProductDescription,
    p.Price,
    p.StockQuantity,
    o.OrderID,
    o.CustomerID,
    o.OrderDate,
    o.TotalAmount,
    o.OrderStatus,
    o.ShippingAddress,
    o.BillingAddress,
    c.FirstName AS CustomerFirstName,
    c.LastName AS CustomerLastName,
    c.Email AS CustomerEmail
FROM
    ProductTable p
LEFT JOIN
    OrderTable o ON p.ProductID = o.OrderID 
LEFT JOIN
    CustomerTable c ON o.CustomerID = c.CustomerID
ORDER BY
    p.ProductID, o.OrderDate;

	Q3

	SELECT
    OrderID,
    CustomerID,
    OrderDate,
    TotalAmount,
    OrderStatus,
    ShippingAddress,
    BillingAddress,
    COUNT(DISTINCT OrderID ) AS TotalProducts
FROM
    OrderTable
GROUP BY
    OrderID, CustomerID, OrderDate, TotalAmount, OrderStatus, ShippingAddress, BillingAddress
ORDER BY
    OrderID;

	Q4

	SELECT
    p.ProductID,
    p.ProductName,
    p.ProductDescription,
    SUM(p.Price  * p.StockQuantity) AS TotalSalesAmount
FROM
    ProductTable p
JOIN
    OrderTable od ON p.ProductID = od.OrderID 
GROUP BY
    p.ProductID, p.ProductName, p.ProductDescription
ORDER BY
    p.ProductID;

	Q5

	SELECT
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    c.PhoneNumber,
    c.AddressLine1,
    c.AddressLine2,
    c.City,
    c.State,
    c.PostalCode,
    c.Country
FROM
    CustomerTable c
LEFT JOIN
    OrderTable o ON c.CustomerID = o.CustomerID
WHERE
    o.OrderID IS NULL;


	Q6

	SELECT
    OrderID,
    CustomerID,
    OrderDate,
    TotalAmount,
    OrderStatus,
    ShippingAddress,
    BillingAddress
FROM
    OrderTable;

	Q7

	SELECT
    p.ProductID,
    p.ProductName,
    p.ProductDescription,
    p.Price,
    p.StockQuantity
FROM
    ProductTable p
LEFT JOIN
    OrderTable  od ON p.ProductID = od.OrderID 
WHERE
    od.OrderID IS NULL;

	Q8

	SELECT top 5
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    SUM(o.TotalAmount) AS TotalAmountSpent
FROM
    CustomerTable c
JOIN
    OrderTable o ON c.CustomerID = o.CustomerID
GROUP BY
    c.CustomerID, c.FirstName, c.LastName, c.Email
ORDER BY
    TotalAmountSpent DESC;


	Q9

SELECT
    OrderID,
    CustomerID,
    OrderDate,
    TotalAmount,
    OrderStatus,
    ShippingAddress,
    BillingAddress
FROM
    OrderTable
WHERE
    OrderDate >= DATEADD(DAY, -30, GETDATE());

	Q10

	SELECT
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    AVG(o.TotalAmount) AS AverageOrderAmount
FROM
    CustomerTable c
JOIN
    OrderTable o ON c.CustomerID = o.CustomerID
GROUP BY
    c.CustomerID, c.FirstName, c.LastName, c.Email
ORDER BY
    c.CustomerID;


	Q11

	SELECT
    p.ProductID,
    p.ProductName,
    p.ProductDescription,
    SUM(p.StockQuantity ) AS TotalQuantitySold
FROM
    ProductTable p
JOIN
    OrderTable od ON p.ProductID = od.OrderID 
GROUP BY
    p.ProductID, p.ProductName, p.ProductDescription
ORDER BY
    p.ProductID;


	Q12

	SELECT
    o.OrderID,
    o.OrderDate,
    o.TotalAmount AS TotalOrderAmount,
    SUM(od.StockQuantity  ) AS TotalQuantityOrdered
FROM
    OrderTable o
JOIN
    ProductTable od ON o.OrderID = od.ProductID 
GROUP BY
    o.OrderID, o.OrderDate, o.TotalAmount
ORDER BY
    o.OrderID;

	Q13

	SELECT
    YEAR(OrderDate) AS OrderYear,
    MONTH(OrderDate) AS OrderMonth,
    SUM(TotalAmount) AS TotalRevenue
FROM
    OrderTable
GROUP BY
    YEAR(OrderDate), MONTH(OrderDate)
ORDER BY
    OrderYear, OrderMonth;

	Q14

	SELECT
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    COUNT(o.OrderID) AS NumberOfOrders
FROM
    CustomerTable c
LEFT JOIN
    OrderTable o ON c.CustomerID = o.CustomerID
GROUP BY
    c.CustomerID, c.FirstName, c.LastName, c.Email
ORDER BY
    NumberOfOrders DESC;  -- Optional: Order by number of orders, descending

	Q16

	SELECT
    o.OrderID,
    o.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    o.OrderDate,
    o.TotalAmount,
    o.OrderStatus,
    o.ShippingAddress,
    o.BillingAddress
FROM
    OrderTable o
JOIN
    CustomerTable c ON o.CustomerID = c.CustomerID
ORDER BY
    o.OrderID;




	Q17

	SELECT
    YEAR(OrderDate) AS OrderYear,
    MONTH(OrderDate) AS OrderMonth,
    SUM(TotalAmount) AS TotalSalesAmount
FROM
    OrderTable
GROUP BY
    YEAR(OrderDate), MONTH(OrderDate)
ORDER BY
    OrderYear, OrderMonth;

	Q18

	SELECT
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    COUNT(o.OrderID) AS NumberOfOrders
FROM
    CustomerTable c
JOIN
    OrderTable o ON c.CustomerID = o.CustomerID
GROUP BY
    c.CustomerID, c.FirstName, c.LastName, c.Email
HAVING
    COUNT(o.OrderID) >= 3
ORDER BY
    NumberOfOrders DESC;


	Q19

	SELECT
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    SUM(o.TotalAmount) AS TotalRevenue
FROM
    CustomerTable c
JOIN
    OrderTable o ON c.CustomerID = o.CustomerID
GROUP BY
    c.CustomerID, c.FirstName, c.LastName, c.Email
ORDER BY
    TotalRevenue DESC;

	Q20

	SELECT
    OrderID,
    COUNT(*) AS NumberOfProductsOrdered
FROM
    OrderTable 
GROUP BY
    OrderID
ORDER BY
    OrderID;



