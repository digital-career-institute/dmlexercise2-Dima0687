# DML exercise

Tables:

Albums:

Columns: AlbumID (Primary Key), Title, ReleaseYear, Genre, Price, StockQuantity
```SQL
CREATE TABLE Albums(album_id INT PRIMARY KEY, title VARCHAR(50), release_year INT, genre VARCHAR(20), price DECIMAL(10,2), stock_quantity INT);

+----------------+---------------+------+-----+---------+-------+
| Field          | Type          | Null | Key | Default | Extra |
+----------------+---------------+------+-----+---------+-------+
| album_id       | int           | NO   | PRI | NULL    |       |
| title          | varchar(50)   | YES  |     | NULL    |       |
| release_year   | int           | YES  |     | NULL    |       |
| genre          | varchar(20)   | YES  |     | NULL    |       |
| price          | decimal(10,2) | YES  |     | NULL    |       |
| stock_quantity | int           | YES  |     | NULL    |       |
+----------------+---------------+------+-----+---------+-------+
```


Artists:

Columns: ArtistID (Primary Key), ArtistName, Country

```SQL
CREATE TABLE Artist(artist_id INT PRIMARY KEY, artist_name VARCHAR(100), country VARCHAR(50));
+-------------+--------------+------+-----+---------+-------+
| Field       | Type         | Null | Key | Default | Extra |
+-------------+--------------+------+-----+---------+-------+
| artist_id   | int          | NO   | PRI | NULL    |       |
| artist_name | varchar(100) | YES  |     | NULL    |       |
| country     | varchar(50)  | YES  |     | NULL    |       |
+-------------+--------------+------+-----+---------+-------+
```

Exercise Tasks:
note: add some data entries before fetching it

```SQL
INSERT INTO Albums (album_id, title, release_year, genre, price, stock_quantity) VALUES
(101, 'Abbey Road', 1969, 'Rock', 19.99, 30),
(102, 'Thriller', 1982, 'Pop', 24.50, 25),
(103, 'A Night at the Opera', 1975, 'Rock', 21.99, 20),
(104, 'Elvis Presley', 1956, 'Rock and Roll', 14.75, 15),
(105, 'ABBA Gold', 1992, 'Pop', 29.95, 40);

+----------+----------------------+--------------+---------------+-------+----------------+
| album_id | title                | release_year | genre         | price | stock_quantity |
+----------+----------------------+--------------+---------------+-------+----------------+
|      101 | Abbey Road           |         1969 | Rock          | 19.99 |             30 |
|      102 | Thriller             |         1982 | Pop           | 24.50 |             25 |
|      103 | A Night at the Opera |         1975 | Rock          | 21.99 |             20 |
|      104 | Elvis Presley        |         1956 | Rock and Roll | 14.75 |             15 |
|      105 | ABBA Gold            |         1992 | Pop           | 29.95 |             40 |
+----------+----------------------+--------------+---------------+-------+----------------+


INSERT INTO Artist (artist_id, artist_name, country) VALUES
(1, 'The Beatles', 'United Kingdom'),
(2, 'Michael Jackson', 'United States'),
(3, 'Queen', 'United Kingdom'),
(4, 'Elvis Presley', 'United States'),
(5, 'Abba', 'Sweden');

+-----------+-----------------+----------------+
| artist_id | artist_name     | country        |
+-----------+-----------------+----------------+
|         1 | The Beatles     | United Kingdom |
|         2 | Michael Jackson | United States  |
|         3 | Queen           | United Kingdom |
|         4 | Elvis Presley   | United States  |
|         5 | Abba            | Sweden         |
+-----------+-----------------+----------------+
```

# Select Queries:

Retrieve all album titles along with their release years.

```SQL
SELECT title, release_year FROM albums;

+----------------------+--------------+
| title                | release_year |
+----------------------+--------------+
| Abbey Road           |         1969 |
| Thriller             |         1982 |
| A Night at the Opera |         1975 |
| Elvis Presley        |         1956 |
| ABBA Gold            |         1992 |
+----------------------+--------------+
```

Display the genres available in the store without repetition.
```SQL
SELECT DISTINCT genre from albums;

+---------------+
| genre         |
+---------------+
| Rock          |
| Pop           |
| Rock and Roll |
+---------------+
```

List all artists' names along with their respective countries.

```SQL
SELECT artist_name,country FROM artist;

+-----------------+----------------+
| artist_name     | country        |
+-----------------+----------------+
| The Beatles     | United Kingdom |
| Michael Jackson | United States  |
| Queen           | United Kingdom |
| Elvis Presley   | United States  |
| Abba            | Sweden         |
+-----------------+----------------+
```

Fetch the album titles released in a specific year.

```SQL
SELECT title FROM albums WHERE release_year > 1970 AND release_year < 1990;
+----------------------+
| title                |
+----------------------+
| Thriller             |
| A Night at the Opera |
+----------------------+

// OR

SELECT title FROM albums WHERE release_year = 1982;
+----------+
| title    |
+----------+
| Thriller |
+----------+
```

# Insert Queries:

Add a new album titled "Greatest Hits" released in the year 2023 to the database with a price of $15 and a stock quantity of 50.

```SQL
INSERT INTO albums VALUES(106, 'Greatest Hits', 2023, 'Pop', 15.00, 50);

+----------+----------------------+--------------+---------------+-------+----------------+
| album_id | title                | release_year | genre         | price | stock_quantity |
+----------+----------------------+--------------+---------------+-------+----------------+
|      101 | Abbey Road           |         1969 | Rock          | 19.99 |             30 |
|      102 | Thriller             |         1982 | Pop           | 24.50 |             25 |
|      103 | A Night at the Opera |         1975 | Rock          | 21.99 |             20 |
|      104 | Elvis Presley        |         1956 | Rock and Roll | 14.75 |             15 |
|      105 | ABBA Gold            |         1992 | Pop           | 29.95 |             40 |
|      106 | Greatest Hits        |         2023 | Pop           | 15.00 |             50 |
+----------+----------------------+--------------+---------------+-------+----------------+
```
Insert a new artist named "New Artist" from "Canada" into the Artists table.

```SQL
INSERT INTO artist VALUES(6, 'New Artist', 'Canada');

+-----------+-----------------+----------------+
| artist_id | artist_name     | country        |
+-----------+-----------------+----------------+
|         1 | The Beatles     | United Kingdom |
|         2 | Michael Jackson | United States  |
|         3 | Queen           | United Kingdom |
|         4 | Elvis Presley   | United States  |
|         5 | Abba            | Sweden         |
|         6 | New Artist      | Canada         |
+-----------+-----------------+----------------+
```

Update Queries:

# Update
the price of all albums in the "Pop" genre to $20.

```SQL
UPDATE albums SET price = 20.0 WHERE genre = "Pop";

+----------+----------------------+--------------+---------------+-------+----------------+
| album_id | title                | release_year | genre         | price | stock_quantity |
+----------+----------------------+--------------+---------------+-------+----------------+
|      101 | Abbey Road           |         1969 | Rock          | 19.99 |             30 |
|      102 | Thriller             |         1982 | Pop           | 20.00 |             25 |
|      103 | A Night at the Opera |         1975 | Rock          | 21.99 |             20 |
|      104 | Elvis Presley        |         1956 | Rock and Roll | 14.75 |             15 |
|      105 | ABBA Gold            |         1992 | Pop           | 20.00 |             40 |
|      106 | Greatest Hits        |         2023 | Pop           | 20.00 |             50 |
+----------+----------------------+--------------+---------------+-------+----------------+
```

Increase the stock quantity of the album titled "Thriller" by 10 units.

```SQL
UPDATE albums SET stock_quantity = stock_quantity + 10 WHERE title = "Thriller";

+----------+----------------------+--------------+---------------+-------+----------------+
| album_id | title                | release_year | genre         | price | stock_quantity |
+----------+----------------------+--------------+---------------+-------+----------------+
|      101 | Abbey Road           |         1969 | Rock          | 19.99 |             30 |
|      102 | Thriller             |         1982 | Pop           | 20.00 |             35 |
|      103 | A Night at the Opera |         1975 | Rock          | 21.99 |             20 |
|      104 | Elvis Presley        |         1956 | Rock and Roll | 14.75 |             15 |
|      105 | ABBA Gold            |         1992 | Pop           | 20.00 |             40 |
|      106 | Greatest Hits        |         2023 | Pop           | 20.00 |             50 |
+----------+----------------------+--------------+---------------+-------+----------------+
```

# Delete Queries:
Remove an album titled "Dangerous" from the database.

```SQL
INSERT INTO albums VALUES(107, 'Dangerous', 1991, 'Pop', 20.0,5);
+----------+----------------------+--------------+---------------+-------+----------------+
| album_id | title                | release_year | genre         | price | stock_quantity |
+----------+----------------------+--------------+---------------+-------+----------------+
|      101 | Abbey Road           |         1969 | Rock          | 19.99 |             30 |
|      102 | Thriller             |         1982 | Pop           | 20.00 |             35 |
|      103 | A Night at the Opera |         1975 | Rock          | 21.99 |             20 |
|      104 | Elvis Presley        |         1956 | Rock and Roll | 14.75 |             15 |
|      105 | ABBA Gold            |         1992 | Pop           | 20.00 |             40 |
|      106 | Greatest Hits        |         2023 | Pop           | 20.00 |             50 |
|      107 | Dangerous            |         1991 | Pop           | 20.00 |              5 |
+----------+----------------------+--------------+---------------+-------+----------------+

DELETE FROM albums WHERE title = 'Dangerous';
+----------+----------------------+--------------+---------------+-------+----------------+
| album_id | title                | release_year | genre         | price | stock_quantity |
+----------+----------------------+--------------+---------------+-------+----------------+
|      101 | Abbey Road           |         1969 | Rock          | 19.99 |             30 |
|      102 | Thriller             |         1982 | Pop           | 20.00 |             35 |
|      103 | A Night at the Opera |         1975 | Rock          | 21.99 |             20 |
|      104 | Elvis Presley        |         1956 | Rock and Roll | 14.75 |             15 |
|      105 | ABBA Gold            |         1992 | Pop           | 20.00 |             40 |
|      106 | Greatest Hits        |         2023 | Pop           | 20.00 |             50 |
+----------+----------------------+--------------+---------------+-------+----------------+
```
Delete an artist named "Old Artist" from the Artists table.

```SQL
INSERT INTO artist VALUES(7,'Old Artist', 'Somewhere');
+-----------+-----------------+----------------+
| artist_id | artist_name     | country        |
+-----------+-----------------+----------------+
|         1 | The Beatles     | United Kingdom |
|         2 | Michael Jackson | United States  |
|         3 | Queen           | United Kingdom |
|         4 | Elvis Presley   | United States  |
|         5 | Abba            | Sweden         |
|         6 | New Artist      | Canada         |
|         7 | Old Artist      | Somewhere      |
+-----------+-----------------+----------------+

DELETE FROM artist WHERE artist_name = 'Old Artist';

+-----------+-----------------+----------------+
| artist_id | artist_name     | country        |
+-----------+-----------------+----------------+
|         1 | The Beatles     | United Kingdom |
|         2 | Michael Jackson | United States  |
|         3 | Queen           | United Kingdom |
|         4 | Elvis Presley   | United States  |
|         5 | Abba            | Sweden         |
|         6 | New Artist      | Canada         |
+-----------+-----------------+----------------+
```
