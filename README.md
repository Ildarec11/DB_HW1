# DB_HW1
<ul>
  <li>
    select * from employee e join employee e2 on e.chief_id = e2.id and e.salary > e2.salary limit 40;

T2

select * from employee e where e.salary = ( select max (salary) from employee e2 where e2.department_id = e.department_id) limit 40;


 T3

select id from department d where (select count(id) from employee e where e.department_id = d.id) <=3 limit 40;

 T4

select * from employee e where ( select count (id) from employee e2 where e.chief_id = e2.id and e2.department_id = e.department_id) = 0 limit 40;

T5

with sum_salary as
  ( select department_id, sum(salary) salaries
    from   employee
    where department_id notnull 
    group  by department_id )
select department_id
from   sum_salary a       
where  a.salaries = ( select max(salaries) from sum_salary )

   </li>
</ul>
