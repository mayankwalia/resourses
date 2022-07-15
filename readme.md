# resourses

- ## Python Flask [link](https://github.com/mayankwalia/educative-courses/blob/master/Flask_%20Develop%20Web%20Applications%20in%20Python%20-%20Learn%20Interactively/readme.md)

-- select managers.name from managers,teams
-- where managers.team_id=teams.team_id and teams.name='All Stars';

-- select name from managers where team_id in (select team_id from teams where name='All Stars')

-- select managers.name from managers inner join teams on teams.team_id=managers.team_id where teams.name='All Stars'

-- select name from teams;

-- select match_num from matches where host_team_score>guest_team_score;

-- select jersey_home_color,jersey_away_color from teams where name='All Stars';

-- select name from players where team_id in (select team_id from teams where name='All Stars');

-- select players.name,dob from players join teams on teams.team_id=players.team_id where teams.name='All Stars';

-- select match_num,name from matches natural join match_referees join referees on referee=referee_id where match_date='2020-05-11'

-- select name from players where team_id in (select team_id from teams where name='All Stars') order by dob desc limit 1;

select name from teams where team_id not in (select team_id from players where player_id=74);

select t.names from teams as t where count(select * from matches where t.team_id=guest_team_id or  )

-- select * from players
