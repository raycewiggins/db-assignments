RDF CP3A
1. INSERT adds data, UPDATE updates databases with new data, and DELETE removes data
2. Each SQL command starts with a command word followed by an argument for the table which is to be changed, and then a VALUES command that is followed by another argument which contains the various values you wish to update the table with.
3. Of the many datatypes decimals, char, and date are a few common ones that you could use in a database. The decimal  type could be used for certain types of scores that have decimal places. Char is a common string dataype that can be used to store words, such as the names of users which has limit on the number of characters. The datatype could be used to store chronological data such as when a post was last updated on a blog.
4. 
  a. char, boolean, int, int. 
  
  ```sql
  b. 
    CREATE TABLE wedding (
      id int,
      first_name char,
      last_name char,
      rsvp boolean,
      number_of_guests int,
      number_of_meals float
    );

  c. 
  ALTER TABLE wedding ADD COLUMN thank_you boolean;
  
  d. 
  ALTER TABLE wedding DROP COLUMN number_of_meals;
  
  e. 
  ALTER TABLE wedding ADD COLUMN table_number int;
  
  f. 
  DROP TABLE wedding;
  ```

5. 
```sql
    CREATE TABLE library (
        id int,
        isbn int,
        title char,
        author char,
        genre int,
        publishing_date date,
        copies int,
        available_copies int
    );
```    
  a. 
  ```sql
    INSERT INTO library (id, isbn, title, author, genre, publishing_date, copies, available_copies)
    VALUES
    (1, 1234, "First", "Person", "Reference", 2017-11-20, 4, 1),
    (2, 1434, "Second", "Person", "Reference", 2017-11-20, 4, 1),
    (3, 1534, "Third", "Person", "Reference", 2017-11-20, 4, 1);
  ```
  b. 
  ```sql
    UPDATE library SET available_copies=3 WHERE id=1;
  ```
  c.
  ```sql
    DELETE FROM library WHERE id=1;
  ```

6. 
```sql
CREATE TABLE spacecrafts (
      id int,
      name char,
      launched int,
      origin char,
      description text,
      orbiting_body char,
      operating boolean,
      miles_away int
  );
```
  a.
  ```sql
  INSERT INTO spacecrafts (id, name, launched, origin, description, orbiting_body, operating, miles_away)
  VALUES
  (1, "Cassini 1", 1998, "USA", "A satelitte currently observing Saturn", Saturn, True, 8910238710),
  (2, "Cassini 2", 1998, "USA", "A satelitte currently observing Saturn", Saturn, True, 8910238710),
  (3, "Cassini 3", 1998, "USA", "A satelitte currently observing Saturn", Saturn, True, 8910238710);
  ```
  b.
  ```sql
  DELETE FROM spacecrafts WHERE id=1;
  ```

  c.
  ```sql
    UPDATE spacecrafts SET operating=false WHERE id=2;
  ```

7.
```sql
CREATE TABLE inbox (
      id int,
      subject char,
      sender char,
      recipients ,
      body text,
      time_stamp date,
      is_read boolean,
      id_in_chain int
  );
```
  a.
  ```sql
    INSERT INTO inbox (id, subject, sender, recipients, body, time_stamp, is_read, id_in_chain)
    VALUES
    (1, "Hello World", "Rayce", "Carol", "Welcome to SQL", 2017-11-2, True, 2),
    (2, "Hello World", "Rayce", "Carol", "Welcome to SQL", 2017-11-2, True, 3),
    (3, "Hello World", "Rayce", "Carol", "Welcome to SQL", 2017-11-2, True, 4);
  ```

  b.
  ```sql
    DELETE FROM inbox WHERE id=1;
  ```

  c.
  ```sql
    UPDATE inbox SET is_read=false WHERE id=2;
  ```