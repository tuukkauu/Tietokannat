# Tietokannat, Ohjelmisto 1



Osio 05  Join harjoitukset:
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




