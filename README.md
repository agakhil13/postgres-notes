### Postgresql commands


#### Create a database `test`
```console
CREATE DATABASE test;
```

#### List available databases
```console
\l
```

#### Connect to database `test`
```console
psql -h [HOST] -p [PORT] -U [USER] -d [DB]
```
or
```console
\c test
```

#### Delete the existing database `test`
```console
DROP DATABASE test;
```

#### Create table with postgres
```console
CREATE TABLE table_name (
    Column name + data type + constraints if any
)
```
```console
CREATE TABLE person (
id int,
first_name VARCHAR(50),
last_name VARCHAR(50),
gender VARCHAR(6),
date_of_birth DATE
);
```

#### Create table with constraint
```console
CREATE TABLE person (
id BIGSERIAL NOT NULL PRIMARY KEY,
first_name VARCHAR(50) NOT NULL,
last_name VARCHAR(50) NOT NULL,
gender VARCHAR(6) NOT NULL,
date_of_birth DATE NOT NULL
);
```

#### Delete the existing table `person`
```console
DROP DATABASE person;
```

#### List the available schema
```console
\dt
```

#### Describe table `person`
```console
\d person
```

#### Insert Record into table `person`
```console
INSERT INTO person (
first_name,
last_name,
gender,
date_of_birth)
VALUES ('Adam', 'Smith', 'Male', DATE '1996-01-13');
```

#### Execute sql commands using file path
```console
\i [path to *.sql]
```

#### Order by ASC/DESC
```console
SELECT * FROM person ORDER BY id DESC;
```

#### select Distinct values from column
```console
SELECT DISTINCT gender FROM person ORDER BY gender;

SELECT count(DISTINCT gender) FROM person;
```

#### Where clause
```console
SELECT count(*) FROM person WHERE gender = 'Female';

SELECT * FROM person WHERE gender = 'Female' AND (id = 44 OR id =53);

SELECT * FROM person WHERE gender = 'Female' AND id IN (44, 53);

SELECT * FROM person WHERE id > 10 AND id < 20;
```

#### Limit, Fetch, and Offset
```console
SELECT * FROM person LIMIT 5;
or
SELECT * FROM person FETCH FIRST 5 ROW ONLY;

SELECT * FROM person OFFSET 10 LIMIT 5;
```

#### IN and BETWEEN
```console
SELECT * FROM person WHERE id IN (1,3,5,8,22,88,36);

SELECT * FROM person WHERE id BETWEEN 5 and 10;

SELECT * FROM person WHERE date_of_birth BETWEEN DATE '2018-01-01' and '2022-01-01';
```

#### LIKE and ILIKE
```console
SELECT * FROM person WHERE email LIKE '%google.__';

SELECT * FROM person WHERE email LIKE '________@%';

ignore case use 'ILIKE':
SELECT * FROM person where email ILIKE '%GOOGLE.___';
```

#### Group By and Having
```console
SELECT country, COUNT(*) FROM person GROUP BY country;

SELECT country, COUNT(*) FROM person GROUP BY country ORDER BY count DESC;

SELECT country, COUNT(*) FROM person GROUP BY country HAVING COUNT(*) > 100 ORDER BY count DESC;

SELECT country, COUNT(*) FROM person GROUP BY country HAVING COUNT(*) BETWEEN  30 AND 50 ORDER BY count DESC;

SELECT country, COUNT(*) FROM person WHERE country IN ('Russia', 'Poland', 'France') GROUP BY country HAVING COUNT(*) BETWEEN  30 AND 50 ORDER BY count DESC;
```

#### Aggregation Functions
```console
SELECT make, model, MIN(price) FROM car GROUP BY make, model;

SELECT make, SUM(price) FROM car GROUP BY make;

SELECT make, model, price, price * .10 AS discount, (price - price * .10) AS "final price" FROM car;
```


