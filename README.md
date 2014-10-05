retrosheet-import
=================

This is a simple batch file and SQL script to prepare Retrosheet event files to be imported into a database. The .sql script will create a table in a MySQL database with all 97 columns of data. Here is a definition of each field:
http://www.retrosheet.org/datause.txt

The batch file will take all .csv files within a given directory (C:\retrosheet, in my case) and copy each one to a single .csv file. 

In order to import the .csv files into the database, launch the MySQL command line and run something like this command:
LOAD DATA LOCAL INFILE 'C:\\retrosheet\\events_master.csv' INTO TABLE <<DATABASE-NAME>>.events FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\r\n';

This takes the master .csv file created by the batch file and bulk inserts the data into the table created by the .sql script.
