# Practice Questions Database - LIS

```sql
select author_fname,author_lname from book_authors 
where author_fname like '_'

select title,publisher from book_catalogue where year!='2015' and year!='2017'

select title,publisher from book_catalogue except 
select title,publisher from book_catalogue where year='2015' or year='2017'

select title,publisher from book_catalogue except 
select title,publisher from book_catalogue where year in ('2015','2017')

select title,publisher from book_catalogue where year not in ('2015','2017')

select student_fname,student_lname from students 
where (dob between '2002-01-05' and '2002-05-31') 
or (dob between '2003-01-05' and '2003-05-31')


select student_fname,student_lname from students 
where (dob between '2002-01-05' and '2002-05-31') 
union
select student_fname,student_lname from students 
where (dob between '2003-01-05' and '2003-05-31')


select count(*) as "total member" from members where member_type='UG'

select department_code, count(gender) as "no of female students" from students where gender='F' group by department_code

select * from students natural join departments 


select count(*) from students as s, departments as d where s.department_code=d.department_code
```


# Practice Questions Database - FLIS

``` sql
select * from matches;

select * from teams;

select match_num from matches where (host_team_score - guest_team_score)>=ALL(select (host_team_score - guest_team_score) from matches );

-- select match_num,match_date from matches where host_team_id='T0006' or guest_team_id='T0006';

select name from players;

select team_id,count(*) from players group by team_id;

select name from players where name like '^A%';

select teams.team_id,players.name from teams natural join players where players.name like '^a'

select distinct jersey_home_color from teams union select distinct jersey_away_color from teams ;

select distinct team_id,jersey_home_color,jersey_away_color from teams order by team_id

select  count(*) from teams;

select (host_team_score*3-5) from matches;

select count(*)
from players, teams
where players.dob > '2002-10-15'
group by teams.name
order by players.dob DESC;
select distinct dob from players


-- Joins

select * from match_referees m left join referees r on m.referee=r.referee_id

select distinct name from teams

select r.name from referees as r inner join match_referees 
on r.referee_id=m.referee inner join matches as 
ma where ma.host_team_id=(select team_id from teams where name='Amigos') or
ma.guest_team_id=(select team_id from teams where name='Amigos')


select * from match_referees cross join referees

select * from matches where not(host_team_score>2 and guest_team_score<10);

select * from matches where host_team_score between 3 and 4
except select * from matches where guest_team_score=3;

select name from referees where referee_id=(select referee from match_referees group by referee order by count(*) desc limit 1)

select mr.match_num,m.match_date from match_referees as mr, matches as m, referees as r where r.name='Tony Joseph Louis' and mr.referee=r.referee_id and m.match_num=mr.match_num;
select name from teams
select name from teams where name like '__a%'

select name from players where name like 'S%' and name not like '%n'
except select name from players where name like '%n'

select count(*) from players where team_id='T0001'


select count(*) from players  where team_id='T0001' group by team_id
select since from managers
select name,dob from managers where since>='2019-01-01' and since<='2020-12-31'


select * from teams where name like '% S%'


select p.name from players as p, teams as t where p.team_id=t.team_id order by p.dob desc limit 1;


select name,dob from managers where since between '2019-01-01' and '2020-12-31'


```
