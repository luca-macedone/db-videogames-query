## SELECT

- 1
    ```sql
    SELECT * FROM software_houses sh 
    WHERE sh.country = 'United States'
    ```

- 2
    ```sql
    SELECT * FROM players p 
    WHERE p.city = 'Rogahnland' 
    ```

- 3
    ```sql
    SELECT * FROM players p 
    WHERE p.name LIKE '%a' 
    ```

- 4
    ```sql
    SELECT * FROM reviews r  
    WHERE r.player_id = 800
    ```

- 5
    ```sql
    SELECT * FROM tournaments t 
    WHERE t.`year` = 2015
    ```

- 6
    ```sql
    SELECT * FROM awards a 
    WHERE a.description LIKE '%facere%'
    ```

- 7
    ```sql
    SELECT DISTINCT videogame_id  FROM category_videogame cv 
    WHERE cv.category_id = 2 OR cv.category_id = 6
    ```

- 8
    ```sql
    SELECT * FROM reviews r 
    WHERE r.rating >= 2 AND  r.rating <= 4
    ```

- 9
    ```sql
    SELECT * FROM videogames v 
    WHERE YEAR(v.release_date) = 2020
    ```

- 10
    ```sql
    SELECT DISTINCT videogame_id  FROM reviews r 
    WHERE r.rating = 5
    ```

- 11 (bonus)
    ```sql
    SELECT COUNT(rating) as 'number' , AVG(rating) as 'avg_rating'  FROM reviews r 
    WHERE  r.videogame_id = 412
    ```

- 12 (bonus)
    ```sql
    SELECT COUNT(id) as 'number' FROM videogames v 
    WHERE  v.software_house_id = 1 AND YEAR (v.release_date) = 2018
    ```

## GROUP BY

- 1
    ```sql
    SELECT COUNT(id) as 'total', country  FROM software_houses sh 
    GROUP BY sh.country 
    ```

- 2
    ```sql
    SELECT videogame_id, COUNT(id)  FROM reviews r 
    GROUP BY videogame_id  
    ```

- 3
    ```sql
    SELECT pegi_label_id , COUNT(videogame_id)  FROM pegi_label_videogame plv 
    GROUP BY pegi_label_id  
    ```

- 4
    ```sql
    SELECT YEAR(release_date), COUNT(id)  FROM videogames v  
    GROUP BY YEAR(release_date) 
    ```

- 5
    ```sql
    SELECT device_id, COUNT(videogame_id) FROM device_videogame dv 
    GROUP BY device_id 
    ```

- 6
    ```sql
    SELECT videogame_id FROM reviews r 
    GROUP BY videogame_id 
    ORDER BY AVG(rating) 
    ```

## JOIN

- 1
    ```sql
    SELECT DISTINCT p.* FROM players p
    JOIN reviews r 
    ON p.id = r.player_id 
    ```

- 2
    ```sql
    SELECT DISTINCT  tv.videogame_id FROM tournament_videogame tv
    JOIN tournaments t ON tv.tournament_id = t.id 
    WHERE t.`year` = 2016
    ```

- 3
    ```sql
    SELECT v.*, cv.id as 'category_id' FROM videogames v 
    JOIN category_videogame cv ON v.id = cv.videogame_id 
    ```

- 4
    ```sql
    SELECT DISTINCT sh.* FROM software_houses sh  
    JOIN videogames v ON v.software_house_id = sh.id 
    WHERE YEAR(v.release_date) >= 2020
    ```

- 5
    ```sql
    SELECT av.* FROM award_videogame av  
    JOIN videogames v ON av.videogame_id = v.id 
    JOIN software_houses sh ON v.software_house_id = sh.id
    ```

- 6
    ```sql
    SELECT DISTINCT  v.*, c.*, pl.* FROM videogames v 
    JOIN reviews r  ON r.videogame_id = v.id 
    JOIN category_videogame cv ON cv.videogame_id = v.id 
    JOIN categories c ON cv.category_id = c.id 
    JOIN pegi_label_videogame plv ON plv.videogame_id = v.id 
    JOIN pegi_labels pl ON plv.pegi_label_id = pl.id 
    WHERE r.rating = 4 OR r.rating = 5
    ```

- 7
    ```sql
    SELECT DISTINCT v.name FROM videogames v 
    JOIN tournament_videogame tv ON v.id = tv.videogame_id 
    JOIN player_tournament pt ON pt.tournament_id = tv.tournament_id 
    JOIN players p ON pt.player_id = p.id 
    WHERE p.name LIKE 'S%'
    ```

- 8
    ```sql
    SELECT DISTINCT  t.city, a.name  FROM tournaments t 
    JOIN tournament_videogame tv ON tv.tournament_id = t.id 
    JOIN videogames v ON tv.videogame_id = v.id
    JOIN award_videogame av ON av.videogame_id = v.id
    JOIN awards a ON av.award_id = a.id
    WHERE av.`year` = 2018 AND av.award_id = 1
    ```

- 9
    ```sql
    SELECT p.* FROM players p 
    JOIN player_tournament pt ON pt.player_id = p.id 
    JOIN tournaments t ON pt.tournament_id = t.id 
    JOIN tournament_videogame tv ON tv.tournament_id = t.id
    JOIN videogames v ON tv.videogame_id = v.id
    JOIN award_videogame av ON av.videogame_id = v.id
    JOIN awards a ON av.award_id = a.id 
    WHERE a.name = "Gioco più atteso" AND av.year = 2018 AND t.`year` = 2019
    ```


