1.
-MIN: used to get the minimum value of a column of data.
-MAX: used to get the maximum value from a column of data.
-SUM: used to get the sum of of values in a column of data.
-AVG: used to get the average value in a column of data.
-COUNT: used to get the number of values or rows in a column.

2.
- SELECT SUM(amount)
  FROM donations;
  --> 993

- SELECT SUM(amount) AS amount, donor
  FROM donations
  GROUP BY donor;
--> amount	donor
    20	Samwell
    10	Daario
    75	Brienne
    120	Tyrion
    70	Petyr
    45	Melisandre
    25	Bran
    50	Tormund
    30	Ygritte
    7	  Gilly
    25	Jon
    60	Arya
    20	Theon
    20	Bronn
    120	Margaery
    90	Missandei
    33	Sansa
    173	Daenerys

- SELECT AVG(amount) AS amount, donor
  FROM donations
  GROUP BY donor;
--> amount	donor
    20	Samwell
    10	Daario
    75	Brienne
    40	Tyrion
    70	Petyr
    45	Melisandre
    25	Bran
    50	Tormund
    30	Ygritte
    7	  Gilly
    25	Jon
    20	Arya
    10	Theon
    20	Bronn
    120	Margaery
    22.5	Missandei
    33	Sansa
    86.5	Daenerys

- SELECT COUNT(amount)
  FROM donations
  WHERE amount > 100;
--> 2

- SELECT MAX(amount)
  FROM donations;
--> 120

- SELECT MIN(amount)
  FROM donations;
--> 5

3. Use an ORDER BY clause

4. You could use OFFSET if you were trying to look at a specfic group to get insights about them. Like if you wanted to know what the ages were of runners who finished a race after a certain time you could use OFFSET to skip that row of times in the table and look at the age column of those runners in that group.

5. You want to make sure the query returns the data in a meaningful way. Otherwise you'll just get rows of data that isn't sorted by what you're looking for.

6. WHERE filters rows before aggregation, whereas HAVING filters rows after aggregation.

7.
SELECT id, SUM(amount)
 FROM payment
 GROUP BY id
 HAVING SUM(amount) > 200;

8.
SELECT *
FROM cats
ORDER BY intake_date;

SELECT *
FROM adoptions
ORDER BY date
LIMIT 5;

SELECT *
FROM cats
WHERE gender = 'F' AND age > 2;

SELECT SUM(amount) AS amount, donor
FROM donations
GROUP BY donor
ORDER BY amount DESC
LIMIT 5;

SELECT SUM(amount) AS amount, donor
FROM donations
GROUP BY donor
ORDER BY amount DESC
LIMIT 10 OFFSET 5;
