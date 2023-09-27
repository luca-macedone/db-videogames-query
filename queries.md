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