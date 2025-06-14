# SQL---Questions

1 Combine two tables:

select firstName, lastName, city, state
from Person 
left join Address 
on  Person.personId = Address.personId


2 Duplicate emails :

select email as Email from Person
group by Email 
having Count(Email) >1

3 Rising temperature:

select id
from  (
    select id, temperature,
           lag(temperature) over (order by recordDate) as prev_temp
    from  Weather
) as temp_table
where temperature > prev_temp

4 Employee bonus:

select e.name , b.bonus from Employee e
left join Bonus b
on e.empId  = b.empId
where  bonus < 1000 or  bonus is Null

5 Find customer referee : 

select name 
from Customer
where referee_id != 2 or referee_id IS NULL

6 Customers who never order :

select name as customers from Customers 
where id not in (
    select customerId from Orders
)

7 nDelete duplicate emails:

delete p1
from Person p1, Person p2
where p1.email = p2.email
and p1.id > p2.id

8 Big countries: 

select name, population, area
from World 
where area >= 3000000 or population >= 25000000

9 Classes more than 5 students :

select class
from Courses
group by class
having count(class)>=5

10 Sales person:

select name from SalesPerson
where sales_id not in (
    select distinct sales_id
    from Orders
    where com_id = (
        selecrt com_id from Company where name = 'RED'
    )
)

11 Triangle judgement:

case 
when x+y >z and y+z>x and z+x >y then 'Yes' else 'No' 
end as triangle
from Triangle

12 Biggest single number:

select max(num) as num from MyNumbers
where num in (
    select num from MyNumbers
    group by num
    having count(*) = 1
    )

13 Not boring movies: 

select * from Cinema 
where description != 'boring' and id%2 !=0
order by rating desc

14 Swap salary: 

update Salary set sex = case
            when sex = 'm' then 'f' 
            else 'm'  end

15  Product sales analysis 1:

select Product_name, year, price from Sales 
left join Product 
on Sales.product_id = Product.product_id

16 Project employees 1:

select p.project_id ,round(avg(e.experience_years),2) as average_years from Project p
left join Employee e
on p.employee_id = e.employee_id
group by p.project_id

17 Sales analysis III :

select product_id, product_name from Product
where product_id in (
    select product_id from Sales
    group by product_id
    having min(sale_date) >= '2019-01-01' AND max(sale_date) <= '2019-03-31'
)



