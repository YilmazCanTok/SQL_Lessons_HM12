SELECT COUNT(*) FROM film
WHERE film.length>
(SELECT AVG(film.length) FROM film);

SELECT COUNT(*) FROM film
WHERE film.rental_rate = ANY
(SELECT MAX(film.rental_rate) FROM film);

SELECT * FROM film
WHERE film.rental_rate = ALL
(SELECT MIN(film.rental_rate) FROM film)
AND 
film.replacement_cost = ALL
(SELECT MIN(film.replacement_cost) FROM film)
ORDER BY film.title ASC;

SELECT * FROM payment 
WHERE amount = ANY
(SELECT MAX(amount) FROM payment);
