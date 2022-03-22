# Loading in Data from a CSV File into a Table in your Database

## Access MySql Shell
```
mysql –u username –p
```
## Create a Table for the Data to fill:
```
CREATE TABLE table_name (
            id INT NOT NULL AUTO_INCREMENT,
            column_1 VARCHAR(255) NOT NULL,
            column_2 DATE NOT NULL,
            column_3 DECIMAL(10 , 2 ) NULL,
            column_4 INTEGER,
            PRIMARY KEY (id)
);
```

## Import Data into MySQL Table:
```
LOAD DATA INFILE '/home/export_file.csv'
INTO TABLE table_name
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '/n'
IGNORE 1 ROWS;
```
