# Loading in Data from a CSV File into a Table in your Database

## Access MySql Shell
Access your terminal window and log into MySQL using the following command:

```
mysql –u username –p
```
## Create a Table for the Data to fill:
The columns in your MySQL table need to match the data from the CSV file you plan to import. 

### Select Database to use:
```
USE database_name;
```
### Create Table:
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
Import the data from the CSV file into the MySQL database, using the following lines:
```
LOAD DATA INFILE '/home/export_file.csv'
INTO TABLE table_name
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '/n'
IGNORE 1 ROWS
(column_1, column_2, column_3, column_4);
```
- LOAD DATA INFILE – Defines the location of the CSV file to be imported. Change the path (between the quotes) to match the path and filename of your CSV file. If the CSV file is located on the local machine, you can use the LOAD DATA LOCAL INFILE statement instead.
- INTO TABLE – This indicates the destination table you are importing the CSV file into. Change the table_name to the name of your table.
- FIELDS TERMINATED BY – By default, comma-separated value files use a comma to identify individual data values. If your export file uses a different delimiter, you can modify this value.
- ENCLOSED BY – This specifies that a double-quote mark " surrounds values.
- LINES TERMINATED BY – Use this line to specify the code for a line break.
- IGNORE 1 ROWS; – Many CSV files export with the column labels as the first line. This command tells MySQL to ignore the first row as you have already created your table with the appropriate column headings. The semicolon at the end specifies the end of the command for MySQL to execute.
