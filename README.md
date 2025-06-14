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


