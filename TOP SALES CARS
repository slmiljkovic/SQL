-Dataset: Taop Cars Database
--Source: Exodus
--Queried using: SQLite 3

-- The database has three tables, dealers, models and sales, which have the following data
CREATE TABLE dealers (
    DealerID INTEGER PRIMARY KEY,
    DealerName TEXT,
    City TEXT,
    Country TEXT
);

INSERT INTO dealers (DealerID, DealerName, City, Country)
VALUES
    (1, 'Smith''s Car Dealership', 'Johannesburg', 'South Africa'),
    (2, 'Brown''s Auto', 'Cape Town', 'South Africa'),
    (3, 'Jones Auto Group', 'Durban', 'South Africa'),
    (4, 'Moyo Auto Sales', 'Francistown', 'Botswana'),
    (5, 'Kgosi Car Dealership', 'Gaborone', 'Botswana'),
    (6, 'Bala Car Sales', 'Maun', 'Botswana'),
    (7, 'Sibanda Motors', 'Gaborone', 'Botswana'),
    (8, 'Lekgotla Car Dealership', 'Lobatse', 'Botswana'),
    (9, 'Tau''s Car Sales', 'Selebi-Phikwe', 'Botswana'),
(10, 'Nkosi Auto', 'Molepolole', 'Botswana');
CREATE TABLE CarSales (
    ModelID INTEGER PRIMARY KEY,
    Brand TEXT,
    Model TEXT,
    Segment TEXT,
    EngineSize REAL,
    Fuel TEXT,
    PriceUSD INTEGER,
    ProfitUSD INTEGER
);

INSERT INTO CarSales (ModelID, Brand, Model, Segment, EngineSize, Fuel, PriceUSD, ProfitUSD)
VALUES
    (1, 'Toyota', 'Corolla', 'Sedan', 1.8, 'Petrol', 18000, 1800),
    (2, 'Volkswagen', 'Polo', 'Hatchback', 1.0, 'Petrol', 15000, 1500),
    (3, 'Ford', 'Ranger', 'Pickup', 2.2, 'Diesel', 30000, 6000),
    (4, 'BMW', '3 Series', 'Sedan', 2.0, 'Petrol', 35000, 3500),
    (5, 'Mercedes-Benz', 'C-Class', 'Sedan', 2.0, 'Petrol', 40000, 4000),
    (6, 'Hyundai', 'i20', 'Hatchback', 1.2, 'Petrol', 13000, 1300),
    (7, 'Nissan', 'Qashqai', 'SUV', 1.6, 'Petrol', 22000, 2200),
    (8, 'Kia', 'Rio', 'Sedan', 1.4, 'Petrol', 17000, 1700),
    (9, 'Audi', 'A4', 'Sedan', 2.0, 'Petrol', 40000, 4000),
    (10, 'Renault', 'Kwid', 'Hatchback', 1.0, 'Petrol', 12000, 1200),
    (11, 'BMW', 'X3', 'SUV', 2.0, 'Diesel', 45000, 9000),
    (12, 'Volkswagen', 'Golf', 'Hatchback', 1.4, 'Petrol', 20000, 2000),
    (13, 'Ford', 'Fiesta', 'Hatchback', 1.5, 'Petrol', 14000, 1400),
    (14, 'Toyota', 'Hilux', 'Pickup', 2.8, 'Diesel', 32000, 6400),
    (15, 'Mercedes-Benz', 'GLA-Class', 'SUV', 2.0, 'Petrol', 45000, 4500);
CREATE TABLE Sales (
    SaleID INTEGER PRIMARY KEY,
    Date TEXT,
    DealerID INTEGER,
    ModelID INTEGER,
    Quantity INTEGER,
    TotalPrice INTEGER,
    TotalProfit INTEGER
);

INSERT INTO Sales (SaleID, Date, DealerID, ModelID, Quantity, TotalPrice, TotalProfit)
VALUES
    (1, '1/5/2022', 3, 9, 1, 40000, 4000),
    (2, '1/8/2022', 9, 9, 1, 40000, 4000),
    (3, '2/12/2022', 8, 10, 2, 24000, 2400),
    (4, '2/22/2022', 4, 11, 1, 45000, 9000),
    (5, '3/1/2022', 6, 6, 3, 39000, 3900),
    (6, '3/8/2022', 10, 4, 1, 35000, 3500),
    (7, '3/9/2022', 5, 2, 2, 30000, 3000),
    (8, '3/10/2022', 5, 5, 1, 40000, 4000),
    (9, '3/11/2022', 4, 10, 1, 12000, 1200),
    (10, '3/12/2022', 2, 3, 2, 60000, 12000),
    (11, '3/15/2022', 2, 5, 1, 40000, 4000),
    (12, '3/16/2022', 5, 11, 1, 45000, 9000),
    (13, '3/17/2022', 6, 3, 2, 60000, 12000),
    (14, '3/18/2022', 5, 7, 1, 22000, 2200),
    (15, '3/19/2022', 5, 8, 2, 34000, 3400),
    (16, '3/22/2022', 6, 10, 1, 12000, 1200),
    (17, '3/23/2022', 1, 14, 1, 32000, 6400),
    (18, '3/24/2022', 1, 15, 3, 135000, 13500),
    (19, '3/25/2022', 8, 9, 1, 40000, 4000),
    (20, '3/26/2022', 10, 12, 1, 20000, 2000),
    (21, '3/29/2022', 10, 5, 2, 80000, 8000);

/* REVENUE BY COUNTRY */

SELECT Country ,SUM (TotalProfit)
FROM sales
JOIN dealers ON sales.dealerid=dealers.DealerID
GROUP BY Country;

/* TOP 3 CARS sales perfomers */

SELECT DealerName ,SUM (TotalProfit),Country
FROM sales
JOIN dealers ON sales.dealerid=dealers.DealerID
GROUP BY DealerName
LIMIT 3;

/* COMPARE Rewenue and profit between brand*/

SELECT brand AS BRAND,SUM(TotalPrice) AS Revenue,SUM(TotalProfit) AS PROFIT
FROM sales
INNER OUTER JOIN models ON sales.ModelID=models.ModelID
GROUP BY brand
ORDER BY SUM(TotalPrice) DESC;

/* REVENUE AND SAles By City AND DEaler */


SELECT DealerName,City,SUM(TotalPrice) 
FROM dealers
JOIN sales ON dealers.DealerID=sales.DealerID
Group BY City
ORDER BY SUM(TotalPrice) ;

/* sales by month*/

SELECT 
strftime('%m', Date) AS Month,
COUNT(*) AS SalesCount,
SUM(TotalPrice) AS Revenue
FROM 
sales
GROUP BY 
strftime('%m', Date)
ORDER BY 
Month;




