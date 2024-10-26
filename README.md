# MySQL-Assignment-5
This  Assignment explains about the Sorting and Grouping data
## Create a table named Country 
create table country (Id INT PRIMARY KEY  ,Country_name varchar (30)not null,Population int not null,Area varchar(30) not null
);
DESC country;

## Create  table named Persons 
create table Persons (Id INT PRIMARY KEY not null,F_name varchar (30) not null,L_name  varchar (30) ,
Population int not null,Rating float(10,2) not null, Country_Id CHAR (10) not null  unique ,Country_name varchar(30) not null );

DESC Persons ;
# insert 10 rows into each tables 

INSERT INTO country (Id ,Country_name ,Population ,Area )
VALUES (1,'India',12000000,'Asia'), (2,'USA',10000000,'North america'), (3,'Canada',500000,'North america'), (4,'Australia',2000000,'North east '), 
(5,'China',500000,'Asia'), (6,'Japan',15000000,'Asia'), (7,'Bhutan',49000,'Asia'), (8,'New zealand',20000000,'North east'), 
(9,'United Kingdom',14000000,'Europe'),(10,'Germany',25000000,'Europe');
select * from country;

insert into persons (Id,F_name,L_name,Population,Rating,Country_Id,Country_name) values 
(1,'Ajay','Cr',14000000,4.0,'IN','India'),
(2,'Albert','John',25000000,3.8,'GER','Germany'),
(3,'Jerin','Joseph',14000000,4.8,'UK','United Kingdom'),
(4,'Catherine','john',2000000,5.0,'AUS','Australia'),
(5,'shangu','shenz',500000,3.5,'CHI','China'),
(6,'shangan','sheen',15000000,4.5,'JPY','Japan'),
(7,'Nathan','cris',10000000,5.0,'US','USA'),
(8,'Fernades','Dcruz',500000,4.8,'CAN','Canada'),
(9,'Cristina','Maria',20000000,4.2,'NYZ','New zealand'),
(10,'John','Jacob',25000000,3.9,'DEN','Denmark');
select * from persons;




#1. Write an SQL query to print the first three characters of Country_name from the Country table. 
SELECT  Country_name,substring(Country_name,1,3) AS FIRST_THREE_CHARACTERS FROM country;

#2. Write an SQL query to concatenate first name and last name from Persons table. 
SELECT F_name,L_name, CONCAT(F_name,' ',L_name) AS Full_name FROM persons;

#3. Write an SQL query to count the number of unique country names from Persons table. 
select distinct count(Country_name)from persons;

#4. Write a query to print the maximum population from the Country table. 
select max(Population) as maximum_population from country;

#5. Write a query to print the minimum population from Persons table. 
select min(Population)as minimum_population from persons;

#6. Insert 2 new rows to the Persons table making the Lname NULL. Then write another query to count Lname from Persons table. 
insert into persons (Id,F_name,L_name,Population,Rating,Country_Id,Country_name) values 
(11,'Arun',null,3000000,3.9,'SRI','Sri lanka'),
(12,'Jimmy',null,59000000,4.5,'SIN','Singapore');

select count(L_name) as null_L_name_count from persons;

#7. Write a query to find the number of rows in the Persons table.
select count(Id) as total_number_of_rows from persons;
 
#8. Write an SQL query to show the population of the Country table for the first 3 rows. (Hint: Use LIMIT) 
select Population from country limit 3;

#9. Write a query to print 3 random rows of countries. (Hint: Use rand() function and LIMIT) 
select * from country order by rand() limit 3;

#10. List all persons ordered by their rating in descending order. 
select F_name,L_name,Rating from persons order by Rating desc;

#11. Find the total population for each country in the Persons table. 
select Country_name,sum(Population) as Total_population from persons group by Country_name;

#12. Find countries in the Persons table with a total population greater than 50,000 
select Country_name,sum(Population) as Total_population from persons group by Country_name having sum(Population)>50000;


#13. List the total number of persons and average rating for each country, 
-- but only for countries with more than 2 persons,  ordered by the average rating in ascending order.
select Country_name,count(*)as Total_no_of_persons,avg(Rating)as average_rating from persons
group by  Country_name having count(*)>2 order by Average_rating asc ;
