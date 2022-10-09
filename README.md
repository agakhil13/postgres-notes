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

