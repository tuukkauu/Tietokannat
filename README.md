# Tietokannat


Osio 05  Join harjoitukset:
1.
select country.name as "country name", airport.name as "airport name"
    -> from country inner join airport on airport.iso_country = country.iso_country
    -> where country.name = "Finland" and airport.scheduled_service = "yes";
