# PGWL01
-- Select all data
SELECT * FROM persons p

--Count all data
SELECT count(*)  FROM persons p

-- Select id, firstname, lastname, color data 
SELECT p.id, p.firstname, p.lastname, p.color FROM persons p

-- Select id, firstname, lastname, color data where color = biru
SELECT p.id, p.firstname, p.lastname, p.color FROM persons p WHERE p.color = 'biru'

-- Select count data group by color
SELECT p.color, count(*) as jumlah FROM persons p group by p.color ORDER BY p.color

-- Count persons using gmail
SELECT count(*)  FROM persons p WHERE p.email like '%@gmail.com'


-- Select persons with same born and city
SELECT * from persons p WHERE p.born = p.city 

-- Select count persons where job = guru

SELECT count(*) from persons p WHERE p.job = 'Guru'

-- Select count persons where born in Yogyakarta
SELECT count(*) from persons p WHERE p.born  = 'Yogyakarta'


-- Select persons with age from date_of_birth
SELECT p.id, p.firstname, p.lastname, p.date_of_birth, age(p.date_of_birth) as umur FROM persons p

-- Select persons with day name from date_of_birth
SELECT p.id, p.firstname, p.lastname, p.date_of_birth, to_char(p.date_of_birth, 'Day') as hari FROM persons p

-- Select data with dayname & age from date_of_birth
SELECT p.id, p.firstname, p.lastname, p.nik, p.email, p.born, p.date_of_birth, date_part('year', age(p.date_of_birth)) as year_age, date_part('month', age(p.date_of_birth)) as month_age, date_part('day', age(p.date_of_birth)) as day_age, to_char(p.date_of_birth, 'Day') as day_of_birth   FROM  persons p

-- select city witch is not yogyakarta
SELECT p.city  FROM persons p WHERE p.city NOT IN ('Yogyakarta');

--input data
INSERT INTO persons (city) VALUES ('Bantul');


--order data from old ppl
select p.id, p.firstname, p.date_of_birth from persons p order by p.date_of_birth ASC 
 
--selecting job from specific job 
select * from persons p where p.job = 'Pilot' or  p.job = 'Sopir'

--selecting data by specific job and age(s)
select * from persons p where job = 'Pilot' and extract (year from age(p.date_of_birth)) > 30

SELECT *, AGE(p.date_of_birth) AS age FROM persons p WHERE job = 'Pilot' AND EXTRACT(YEAR FROM AGE(p.date_of_birth)) > 30;

