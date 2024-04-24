-- 1. Retrieve all information from the customer table.
<br>
<br>
```SELECT * FROM customer;```

-- 2. Retrieve the film ID, title, and release year from the film table 
-- for films released between 2005 and 2010.
<br>
<br>
```SELECT film_id, title, release_year```
<br>
```FROM film```
<br>
```WHERE release_year BETWEEN '2005' AND '2010';```


-- 3. Retrieve unique last names from the actor table.
<br>
<br>
```SELECT DISTINCT last_name```
<br>
```FROM actor;```
<br>

-- 4. Show the title, rental duration, and rental rate and then the 
-- rental cost (rental duration multiplied by rental rate) for each film.
<br>
<br>
```SELECT title,rental_duration,rental_rate, rental_duration * rental_rate AS rental_cost```
<br>
```FROM film;```
<br>

-- 5. Retrieve the title, rental rate, and length of films with a rental 
-- duration greater than 5 days.
-- (NOTE: rental_duration not shown, but used to select films)
<br>
<br>
```SELECT title,rental_rate```
<br>
```FROM film;```
<br>
```WHERE rental_duration > 5;```
<br>

-- 6. Retrieve the title, rental rate, and length of films with a length 
-- 1.5 and 2 hours (i.e. between 90 and 120 minutes).
<br>
<br>
```SELECT title,rental_rate```
<br>
```FROM film;```
<br>
```WHERE length BETWEEN 90 and 120;```
<br>


-- 7. Retrieve the title and rating of films rated 'R' or 'PG'.
-- (Figure out which table holds that data).
<br>
<br>
```SELECT title, rating ```
<br>
```FROM film;```
<br>
```WHERE rating = 'R' or rating = 'PG';```
<br>


-- 8. Retrieve the title, rental duration, rental rate, and rental cost 
-- (calculated field as above) for films where their 
-- rental cost is greater than €30.00.
<br>
<br>
```SELECT title,rental_duration,rental_rate, (rental_duration * rental_rate) AS rental_cost```
<br>
```FROM film;```
<br>
```WHERE rental_duration * rental_rate > 30;```


-- 9. Retrieve the maximum rental duration from the film table.
<br>
<br>
```SELECT MAX(rental_duration) AS longest_rent_for```
<br>
```FROM film;```


-- 10. Retrieve the title, rental duration, and rental rate of films 
-- with a rental duration between 1 and 3 days.
<br>
<br>
```SELECT title, rental_duration, rental_rate```
<br>
```FROM film;```
<br>
```WHERE rental_duration BETWEEN 1 and 3;```


-- 11. Calculate the longest, shortest, and average rental duration of films.
-- (Try to show the average as just a whole-number of days: e.g. 5 not 5.23xxx)
<br>
<br>
```SELECT MAX(rental_duration), MIN(rental_duration), ROUND( AVG(rental_duration) ) -- , CAST( AVG(rental_duration) AS INTEGER )```
<br>
```FROM film;```
<br>


-- 12. Retrieve titles, rental durations, and rental rates of films with 
-- rental durations not in the range of 3 to 5 days.
<br>
<br>
```SELECT title, rental_duration, rental_rate```
<br>
```FROM film;```
<br>
```WHERE NOT (rental_duration >= 1 AND rental_duration <= 3); -- WHERE rental_duration NOT BETWEEN 1 and 3;```


-- 13. Retrieve city IDs, names, and country IDs for cities named 
-- 'La Paz', 'Lausanne', or 'London'.
<br>
<br>
```SELECT city_id, city, country_id ```
<br>
```FROM city```
<br>
```WHERE city IN ('La Paz', 'Lausanne', 'London');```


-- 14. Retrieve category IDs and names for categories labelled 
-- 'Action', 'Animation', 'Children', or 'Classics'.
<br>
<br>
```SELECT *```
<br>
``` FROM category```
<br>
```WHERE name IN ('Action', 'Animation', 'Children', 'Classics'); -- WHERE name='Action' OR name='Animation' OR name='Children' OR name='Classics' ;```


-- 15. Retrieve category IDs and names for categories not labelled 
-- 'Action', 'Animation', 'Children', or 'Classics'.
<br>
<br>
```SELECT *  ```
<br>
```FROM category```
<br>
```WHERE name NOT IN ('Action', 'Animation', 'Children', 'Classics');```


-- 16. Retrieve address IDs and addresses containing 'Santiago' in 
-- any part of the address.
<br>
<br>
```SELECT address_id, address ```
<br>
```FROM address```
<br>
```WHERE address LIKE '%Santiago%';```


-- 17. Retrieve addresses and districts that have exactly four characters
-- in the district name.
<br>
<br>
```SELECT address, district ```
<br>
```FROM address```
<br>
```WHERE LENGTH(district)=4; -- WHERE district IN (SELECT DISTINCT district FROM address WHERE LENGTH(district)=4);```


-- 18. Retrieve films with titles that begin with a seven-letter word
-- starting 'D-r-i' followed by a space and anything else.
<br>
<br>
``` SELECT title ```
<br>
```FROM film```
<br>
```WHERE title LIKE 'Dri____ %';```


-- 19. Retrieve films with titles starting with 
-- the word 'wonderful', or ending with the word 'wonderful'.
-- (Try to allow for any word with six letters and then 'ful'
--  e.g. 'beautiful', 'masterful', 'Colourful'.)
<br>
<br>
``` SELECT title ```
<br>
```FROM film```
<br>
```WHERE title LIKE '______ful%' OR title LIKE '%______ful' ;```

-- 20. Retrieve all records from the actor table.
<br>
<br>
``` SELECT * FROM actor; ```


-- 21. Retrieve addresses, address lines 2, and districts where either 
-- address line 1 or address line 2 is NULL.
<br>
<br>
``` SELECT address, address2  ```
<br>
```FROM address```
<br>
```WHERE address2 IS NULL; ```


-- 22. Retrieve last names and first names of actors, 
-- ordered by last name alphabetically first and then for each
-- group of records shown with the same last_name - order the first names 
-- in descending order.
<br>
<br>
``` SELECT last_name, first_name  ```
<br>
```FROM actor```
<br>
```ORDER BY last_name ASC, first_name DESC; ```



-- 23. Retrieve last names and first names of actors, ordered by 
-- last name in descending order and first name in ascending order.
<br>
<br>
``` SELECT last_name, first_name  ```
<br>
```FROM actor```
<br>
```ORDER BY last_name DESC, first_name ASC;```

-- 24. Count the occurrences of last names and the number of distinct 
-- last names in the actor table.
<br>
<br>
``` SELECT   COUNT(last_name) AS number_names_total ,COUNT(DISTINCT last_name) AS number_distinct_names ```
<br>
```FROM actor```
<br>


-- 25. Count the occurrences of first names and the number of distinct 
-- first names in the actor table.
<br>
<br>
``` SELECT  COUNT(*) AS number_first_names,COUNT(DISTINCT first_name) AS number_distinct_first_names  ```
<br>
```FROM actor```
<br>


-- 26. Produce a list of Country ID's with a Count of the number of cities 
-- with that Country ID where the list is 
-- ordered by the Country ID.
<br>
<br>
``` SELECT  city, COUNT(country_id)  ```
<br>
```FROM city```
<br>
```GROUP BY city```
<br>
```ORDER BY COUNT(country_id) DESC;```


-- 27. Refine the above query to show a list, sorted by 
-- Country ID that shows a count of the citys with that Country ID
-- but where the Country has at least 30 cities.
<br>
<br>
``` SELECT  city, COUNT(country_id)  ```
<br>
```FROM city```
<br>
```GROUP BY city```
<br>
```HAVING COUNT(country_id) <=30```
<br>
```ORDER BY COUNT(country_id) DESC;```

