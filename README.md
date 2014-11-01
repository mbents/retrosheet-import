retrosheet-import
=================

This is a simple batch file and SQL scripts to prepare Retrosheet event files to be imported into a database. The .sql scripts will create two tables in a MySQL database with all 97 BEVENT fields and all 84 BGAME fields. Here is a definition of each field:
http://www.retrosheet.org/datause.txt

The batch file will take all .csv files within a given directory (C:\retrosheet, in my case) and copy each one to a single .csv file. It's a good idea to keep the output files from BEVENT and BGAME in separate directories, and then point the batch file to each directory individually.

In order to import the .csv files into the database, launch the MySQL command line and run something like this command:
LOAD DATA LOCAL INFILE 'C:\\retrosheet\\events_master.csv' INTO TABLE YOUR-DATABASE-NAME.events FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\r\n';

Or this:
LOAD DATA LOCAL INFILE 'C:\\retrosheet\\events_master.csv' INTO TABLE YOUR-DATABASE-NAME.gamelog FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\r\n';

This takes the master .csv file created by the batch file and bulk inserts the data into the specified table created by the .sql script.

Retrosheet event data can be downloaded and parsed using this project: https://github.com/mbents/retrosheet-download-dotnet
