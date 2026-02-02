# BMW-sales-
Sales Analysis 
#Create database for cars sale p1
CREATE DATABASE sales_project;

# create and drop table for bmw sale 
DROP TABLE IF EXISTS BMW_sales;
CREATE TABLE BMW_sales(
			Model varchar (15),
            Year int ,
            Region varchar (20),
            Color varchar (8),
            Fuel_Type varchar (10),
            Transmission varchar (15),
            Engine_Size_L float,
            Mileage_KM	int ,
            Price_USD int ,
            Sales_Volume int,
            Sales_Classification varchar(5)
);

# display the table 
SELECT *
FROM BMW_sales;

#remove duplicate across all columns 
SELECT distinct * 
FROM BMW_sales;

# Q1 what is the total sales for each year from 2010-2024
SELECT  year ,sum(Sales_Volume)AS total_sales 
FROM BMW_sales
GROUP BY year 
ORDER BY year;

#  Q2 what is sales of a each model throughout the years
SELECT model ,sum(Sales_Volume)AS model_sales 
FROM BMW_sales
GROUP BY model ;

# Q3 what is the sales of a region for each model
SELECT model , region, sum(sales_volume) as total_sales 
FROM BMW_sales 
GROUP BY model ,region
ORDER BY model ,region ;

#Q4 what is the total sales of each region 
SELECT region,sum(Sales_volume)as region_sale
FROM BMW_sales
GROUP BY region;

#Q5  what is the average sales amount 
SELECT model ,avg(sales_volume) as average
FROM BMW_sales
GROUP BY model;


#Q6 which car is most expensive 
SELECT *
FROM BMW_sales
WHERE price_usd =(SELECT max(price_usd) FROM BMW_sales);

