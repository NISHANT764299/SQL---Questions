# SQL---Questions

1 # Combine two tables:
select firstName, lastName, city, state
from Person 
left join Address 
on  Person.personId = Address.personId
