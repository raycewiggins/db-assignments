1. You can use a JOIN statement using a common key (column), which will give a new table with data from both tables.

2.
INNER JOIN - generates a new table with rows with only data that have matching keys. Any row that does not have a match to the primary key will not be added to the new table.

RIGHT OUTER and LEFT OUTER joins are flipsides of the same process. First an INNER JOIN is executed and then depending on whether its a LEFT or a RIGHT join rows will be added to the 1st or 2nd table respectively with 'null' in place for the information that does not match the query.

FULL OUTER JOIN is a combination of LEFT and RIGHT joins, which returns a table with columns containing 'null' from both tables when the join condition is not met.

CROSS JOIN gives a new table of all possible combinations of columns from both tables. Therefore each row of the first table will have as many combinations as there are rows of the second table.

3. A primary key is the column with which you would like to match a second column. The foreign key is the column that contains the values you are trying to match with those in the primary key.

4. Aliasing is a way of shorthand for table names so you don't have type as much when writing queries.

5.
SELECT p.name, c.salary, c.vacation_days
FROM professor AS p
JOIN compensation AS c
ON p.id = c.professor_id;

6. You might want to use a NATURAL if you have a good understanding of your tables and just want to make a quick and simple JOIN of the common columns.

7.
SELECT e.name, ss.shift_id, s.date , s.start_time
  FROM employees AS e
  INNER JOIN scheduled_shifts AS ss
      on e.id = ss.employee_id
  RIGHT OUTER JOIN shifts AS s
      on ss.shift_id = s.id;

8.
  a. SELECT first_name, foster_dog_id
      FROM volunteers;

  b. SELECT c.name "Cat Name", ca.date "Adoption Date", a.first_name "Adopter Name"
      FROM cats c, cat_adoptions ca, adopters a
      WHERE ca.cat_id = c.id and ca.adopter_id = a.id;

  c. SELECT a.first_name, d.name
      FROM adopters a
      CROSS JOIN dogs d;

  d. SELECT c.name
      FROM cats c
      LEFT JOIN cat_adoptions ca ON ca.cat_id = c.id
      WHERE ca.cat_id IS NULL;

  d2. SELECT d.name
        FROM dogs d
        LEFT JOIN dog_adoptions da ON da.dog_id = d.id
        WHERE da.dog_id IS NULL;

  e. SELECT v.first_name, d.name
      FROM volunteers v
      JOIN dogs d
      ON v.foster_dog_id = d.id;

  f. SELECT a.first_name "Adopter Name"
      FROM adopters a, dog_adoptions da
      WHERE a.id = da.adopter_id

9.
  a. SELECT p.name
      FROM patrons p
      LEFT JOIN holds h ON h.patron_id = p.id
      WHERE h.isbn = '9136884926'
      ORDER BY h.rank DESC

  b. SELECT b.title "Checked Out Titles"
      FROM books b
      LEFT JOIN transactions t ON t.isbn = b.isbn
      WHERE t.checked_in_date IS NULL

  c. I can't figure this one out.

  d. SELECT DISTINCT b.title
      FROM books b
      LEFT JOIN transactions t ON t.isbn = b.isbn
      WHERE t.checked_out_date > CURRENT_DATE - INTERVAL '5 YEARS';

  e. SELECT * FROM patrons p
      JOIN transactions t ON p.id = t.patron_id;
