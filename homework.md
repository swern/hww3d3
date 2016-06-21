## SQL Questions

First create a database called fringe_shows
```
  #terminal
  psql
  create database fringe_shows;
  \q
```

Populate the data using the script - fringeshows.sql
```
  #terminal
  psql -d fringe_shows -f fringeshows.sql
```

Using the SQL Database file given to you as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.


## Section 1

  Revision of concepts that we've learnt in SQL today

  1. Select the names of all users.

  SELECT name FROM users;
        name       
  ------------------
   Rick Henri
   Jay Chetty
   Keith Douglas
   Ashleigh Adams
   Euan Blackledge
   Chris Flint
   Nico di Lillo
   Joe Maher
   Marie Moyles
   Iain Stewart
   Megan Strachan
   Russell Williams
   Sam Werngren
   Natalie Simpson
   Davide de Lerma
   Josh Kearns
   Renwick Drysdale
   Brian Morrice
  (18 rows)

  2. Select the names of all shows that cost less than £15.

  SELECT name FROM shows WHERE price < 15.00;

               name             
  ------------------------------
   Le Haggis
   Paul Dabek Mischief 
   Best of Burlesque
   Two become One
   Urinetown
   Two girls, one cup of comedy
  (6 rows)



  3. Insert a user with the name "Val Gibson" into the users table.

  INSERT INTO users (name) VALUES ('Val Gibson');

  INSERT 0 1

  4. Insert a record that Val Gibson wants to attend the show "Two girls, one cup of comedy".

  INSERT INTO "shows_users" (show_id, user_id) VALUES (12, 19);

  INSERT 0 1

  5. Updates the name of the "Val Gibson" user to be "Valerie Gibson".

  UPDATE users SET name = 'Valerie Gibson' WHERE name = 'Val Gibson';

  UPDATE 1

  6. Deletes the user with the name 'Valerie Gibson'.

  DELETE FROM users WHERE name = 'Valerie Gibson';
  DELETE 1

  7. Deletes the shows for the user you just deleted.
  DELETE FROM shows_users WHERE user_id = 19;
  DELETE 1


## Section 2

  This section involves more complex queries.  You will need to go and find out about aggregate funcions in SQL to answer some of the next questions.

  9. Select the names and prices of all shows, ordered by price in ascending order.

  SELECT name, price FROM shows ORDER BY price ASC;


                    name                   | price 
  -----------------------------------------+-------
   Two girls, one cup of comedy            |  6.00
   Best of Burlesque                       |  7.99
   Two become One                          |  8.50
   Urinetown                               |  8.50
   Paul Dabek Mischief                     | 12.99
   Le Haggis                               | 12.99
   Joe Stilgoe: Songs on Film – The Sequel | 16.50
   Game of Thrones - The Musical           | 16.50
   Shitfaced Shakespeare                   | 16.50
   Aaabeduation – A Magic Show             | 17.99
   Camille O'Sullivan                      | 17.99
   Balletronics                            | 32.00
   Edinburgh Royal Tattoo                  | 32.99
  (13 rows)


  10. Select the average price of all shows.

  SELECT AVG(price) FROM shows;

      avg         
  ---------------------
   15.9569230769230769
  (1 row)


  11. Select the price of the least expensive show.
  SELECT MIN(price) FROM shows;

  min  
  ------
   6.00
  (1 row)

  12. Select the sum of the price of all shows.
  SELECT SUM(price) FROM shows;

    sum   
  --------
   207.44
  (1 row)

  13. Select the sum of the price of all shows whose prices is less than £20.
  SELECT SUM(price) FROM shows WHERE price < 20;

    sum   
  --------
   142.45
  (1 row)


  14. Select the name and price of the most expensive show.



  15. Select the name and price of the second from cheapest show.
  SELECT shows.name, shows.price FROM shows ORDER BY price LIMIT 1 OFFSET 1;

  16. Select the names of all users whose names start with the letter "N".

  17. Select the names of users whose names contain "er".
  SELECT name FROM users WHERE name LIKE '%er%'
      name       
  -----------------
   Joe Maher
   Sam Werngren
   Davide de Lerma
  (3 rows)


## Section 3

  The following questions can be answered by using nested SQL statements but ideally you should learn about JOIN clauses to answer them.

  18. Select the time for the Edinburgh Royal Tattoo.

  19. Select the number of users who want to see "Shitfaced Shakespeare".

  20. Select all of the user names and the count of shows they're going to see.

  21. SELECT all users who are going to a show at 17:15.
