# Tietokannat, Ohjelmisto 1

Osio 03 Yhteen tauluun kohdistuvien kyselyiden harjoitukset

3.1

select * from goal;

![3 1](https://github.com/user-attachments/assets/fac41f2c-2d10-4ef8-b294-20d51f0f8c94)


3.2

SELECT airport.name, airport.type FROM airport WHERE airport.iso_country = "FI";

![3 2](https://github.com/user-attachments/assets/d056229f-3f2a-43b4-8a56-11e564ef5947)


3.3

SELECT airport.name 
FROM airport 
WHERE airport.iso_country like "%FI%" 
ORDER by name asc;

![3 3](https://github.com/user-attachments/assets/443ad4db-69d8-47e5-b737-f36cb959da4c)


3.4

SELECT airport.name, airport.type
FROM airport
WHERE airport.iso_country = "FI"
ORDER BY type, name;

![3 4](https://github.com/user-attachments/assets/22c4fe40-a1a5-4940-9d47-b20d9f9462a7)


3.5

SELECT name
FROM country
WHERE name LIKE "F%";

![3 5](https://github.com/user-attachments/assets/e98203d3-42ce-417e-b9a2-431d11d89a87)


3.6

SELECT name
FROM country
WHERE name LIKE "%F%";

![3 6](https://github.com/user-attachments/assets/613f85ac-f596-4df0-a9c3-3dfa2f98f793)


3.7

SELECT location
FROM game
WHERE screen_name = "Vesa";

![3 7](https://github.com/user-attachments/assets/afede980-5131-494f-a135-bb80bbeb23cb)


3.8

SELECT co2_consumed
FROM game
WHERE screen_name ="Ilkka";

![3 8](https://github.com/user-attachments/assets/b0f4adde-0f07-4a6f-b2db-f40f076c9ac5)


3.9

SELECT distinct co2_budget FROM game;

![3 9](https://github.com/user-attachments/assets/c8a2dd0d-6080-4ce3-b948-d2bfc82f14a5)




# Osio 04 Where-osan liitosehto:

4.1

select country.name as "country name", airport.name as "airport name"
from country, airport
where country.name = "Iceland"
and airport.iso_country = country.iso_country;

![4 1](https://github.com/user-attachments/assets/1072b3da-6312-43d8-8f07-26e5a06eadfe)

![4 1 2](https://github.com/user-attachments/assets/aace7a1a-cf56-4db6-9d74-2449a2a9e47b)



4.2

select airport.name as "airport name" 
from airport, country
where country.name = "France"
and airport.iso_country = country.iso_country
and airport.type = "large_airport";

![4 2](https://github.com/user-attachments/assets/0b61f7f8-1266-4ff6-828a-0d9d731d3bce)


4.3


select country.name as country_name, airport.name as airport_name
from country, airport
where country.continent = "AN"
and airport.iso_country = country.iso_country;

![4 3](https://github.com/user-attachments/assets/59cd7139-4259-4f47-90c6-258e6f5768d3)

![4 3 2](https://github.com/user-attachments/assets/486a64a8-a6aa-4c08-b1b4-76c5a3a58404)


4.4

select airport.elevation_ft
from airport, game
where game.screen_name = "Heini"
and airport.ident = game.location;

![4 4](https://github.com/user-attachments/assets/0e957086-5640-4fae-90de-042433776ad2)


4.5

select airport.elevation_ft * 0.3048 as elevation_m
from airport, game
where game.screen_name = "Heini"
and airport.ident = game.location;

![4 5](https://github.com/user-attachments/assets/da708b41-c4c4-470c-8138-95e734901667)


4.6

select airport.name
from airport, game
where game.screen_name = "Ilkka"
and airport.ident = game.location;

![4 6](https://github.com/user-attachments/assets/4cdb520a-2bbf-40b5-8e5f-e660c538e238)


4.7

select country.name
from country, airport, game
where game.screen_name = "Ilkka"
and country.iso_country = airport.iso_country
and airport.ident = game.location;

![4 7](https://github.com/user-attachments/assets/222f0099-9fbb-4063-905c-b3760cf785ae)


4.8

select goal.name
from goal, game, goal_reached
where game.screen_name = "Heini"
and goal.id = goal_reached.goal_id
and goal_reached.game_id = game.id;

![4 8](https://github.com/user-attachments/assets/7f5dedaf-3105-4599-852c-a53d164f2adf)


4.9

select airport.name
from airport, game, goal, goal_reached
where goal.name = "CLOUDS" and game.screen_name = "Ilkka"
and airport.ident = game.location
and game.id = goal_reached.game_id
and goal_reached.goal_id = goal.id;

![4 9](https://github.com/user-attachments/assets/9b303222-0d7d-4c25-acdc-706b2e4dcd4f)



4.10

select country.name
from country, game, goal, goal_reached, airport
where goal.name = "CLOUDS" and game.screen_name = "Ilkka"
and airport.ident = game.location
and game.id = goal_reached.game_id
and goal_reached.goal_id = goal.id
and country.iso_country = airport.iso_country;

![4 10](https://github.com/user-attachments/assets/acc83c11-2974-4617-a9c9-25b38a5f8244)




# Osio 05  Join harjoitukset:

5.1

select country.name as "country name", airport.name as "airport name"
    -> from country inner join airport on airport.iso_country = country.iso_country
    -> where country.name = "Finland" and airport.scheduled_service = "yes";

![5 1](https://github.com/user-attachments/assets/4b9ad243-4f67-4af5-91a3-c31ceece8c07)



5.2

select game.screen_name, airport.name
    -> from game
    -> inner join airport on game.location = airport.ident;

![5 2](https://github.com/user-attachments/assets/7a46bf2f-b5a3-4903-801b-899b36441031)


5.3

select game.screen_name, country.name
    -> from game
    -> inner join airport on game.location = airport.ident
    -> inner join country on airport.iso_country = country.iso_country;

![5 3](https://github.com/user-attachments/assets/970558ec-114d-463b-acc6-8e421e9b5c60)


5.4

select airport.name, game.screen_name
    -> from game
    -> right join airport on game.location = airport.ident
    -> where airport.name like "%Hels%";

![5 4](https://github.com/user-attachments/assets/d28c5e47-52b8-4767-b93a-5d7951f44e3b)


5.5

SELECT goal.name, game.screen_name
    -> FROM goal_reached
    -> LEFT JOIN game ON goal_reached.game_id = game.id
    -> RIGHT JOIN goal ON goal_reached.goal_id = goal.id;

![5 5](https://github.com/user-attachments/assets/a7daa3e5-2883-4de4-9e6b-c0e0dbcd6c20)


# Osio 06  Sisäkyselyt:

6.1

SELECT name 
FROM country 
WHERE iso_country in(
			SELECT iso_country
			FROM airport
			WHERE name in(
						SELECT name
						FROM airport
						WHERE name like "%Satsuma%"
						)
			);

![6 1](https://github.com/user-attachments/assets/ffc22e24-5b2e-42bb-9752-44ad265d4ff5)


6.2

SELECT name
FROM airport
WHERE iso_country in(SELECT iso_country
					FROM country
					WHERE name = "Monaco"
					);

![6 2](https://github.com/user-attachments/assets/95d35ed2-90ed-40c2-8b29-0b67e92f71a2)


6.3

select screen_name
from game
where id in(SELECT game_id
			from goal_reached
			where goal_id in(select id
							from goal
							where name = "CLOUDS"
							)
			);

![6 3](https://github.com/user-attachments/assets/be9a5ed8-ee18-4e31-91ff-2c9e6c67a48f)


6.4

select name
from country
where iso_country not in(select iso_country
				from airport
			);

![6 4](https://github.com/user-attachments/assets/a4c44a0a-b6c3-48ce-8311-cc8aa991ab9d)


6.5

select name
from goal
where goal.id not in(select goal_id
				from goal_reached
				where game_id in(select game.id
								from game
								where screen_name in(select screen_name
														from game
														where screen_name = "Heini"
														)
									)
				);

![6 5](https://github.com/user-attachments/assets/fb910810-e89d-4590-8d3d-e11ce5421228)



# Osio 07 Koostetietokyselyt:

7.1

select max(elevation_ft)
from airport;

![7 1](https://github.com/user-attachments/assets/5be9b9d4-cd23-45ab-8495-21a94559fa09)


7.2

select continent, count(*)
from country
group by continent;

![7 2](https://github.com/user-attachments/assets/22defca7-29f7-4bcf-bf06-720e138541b8)


7.3

select game.screen_name, count(*)
from game
join goal_reached on game.id = goal_reached.game_id
join goal on goal.id = goal_reached.goal_id
group by game.screen_name;

![7 3](https://github.com/user-attachments/assets/2847e905-577c-4f9e-80f2-a32b238f4a1b)


7.4

select screen_name
from game
where co2_consumed in(select min(co2_consumed)
				from game
				);

![7 4](https://github.com/user-attachments/assets/3f5bfb90-c183-48fe-a6dd-78098b7bc1ad)


7.5

SELECT country.name, COUNT(*)
FROM country
JOIN airport ON country.iso_country = airport.iso_country
GROUP BY country.name
ORDER BY count(airport.name) DESC
LIMIT 50;

![7 5](https://github.com/user-attachments/assets/e13cf501-cd72-4e75-8c72-14e7e514c0e8)


7.6

SELECT country.name
FROM country
JOIN airport ON country.iso_country = airport.iso_country
GROUP BY country.iso_country
HAVING COUNT(*) > 1000;

![7 6](https://github.com/user-attachments/assets/c9d43bca-4ec4-44db-8936-7abae3e8f4dc)


7.7

SELECT name
FROM airport
WHERE elevation_ft = (SELECT MAX(elevation_ft) FROM airport);

![7 7](https://github.com/user-attachments/assets/141a1118-a485-48ca-9895-f506c33b6e38)


7.8

SELECT country.name
FROM country
JOIN airport ON airport.iso_country = country.iso_country
WHERE airport.elevation_ft = (SELECT MAX(elevation_ft) FROM airport);

![7 8](https://github.com/user-attachments/assets/28b24f3b-dc9b-4443-b683-f82181ea0de4)


7.9

select count(*)
from goal
where goal.id in (select goal_id
				from goal_reached
				where game_id in (select game.id
								from game
								where screen_name = "Vesa"
								)
				);

![7 9](https://github.com/user-attachments/assets/e63befb8-8d35-4521-a0dd-0e07a870d6af)


7.10

SELECT name
FROM airport
WHERE latitude_deg = (
    SELECT MIN(latitude_deg)
    FROM airport
);

![7 10](https://github.com/user-attachments/assets/23a8d73d-ea5d-42ec-af5b-692f86d23b1d)



# Osio 08 Päivityskyselyt:


8.1

update game
set location = (select ident
				from airport
				where name = "Nottingham Airport"
				),
				co2_consumed = co2_consumed + 500
where screen_name = "Vesa";

![8 1](https://github.com/user-attachments/assets/17100278-1415-4e4d-bd0e-b2db84bb826c)


8.2

delete from goal_reached
where game_id in ( select id
		from game
		);
			
delete from goal_reached
where goal_id in ( select id 
		from goal
		);

select * from goal_reached;

![8 2](https://github.com/user-attachments/assets/36f5a9b1-15a5-47e6-b457-e2f1cdff50ec)


8.3

![8 3](https://github.com/user-attachments/assets/6bb4566c-f893-4b45-88ce-efa772d0e17a)


8.4

select from game where id = "1";

delete from game where id = "2";

delete from game where id = "3";

select * from game;

![8 41](https://github.com/user-attachments/assets/84c019e9-795f-499c-9b59-f4ea15fc5841)

![8 42](https://github.com/user-attachments/assets/a7518901-5b44-4dc0-9519-e40acf5bf487)











