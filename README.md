
# Data Modelling in PostgreSQL


## Introduction 

In this project I created an ETL pipeline and Database model for a song streaming website. On a high level, this pipeline aims to convert data stored in logs into a database suitable for analytics. To do this, I implemented a Star Schema containing four tables. I followed these steps:

1. Defined tables with create statements in `sql_queries.py`.
2. Connect with database and call create statements.
3. Walk through all the `json` files in data folder. Code in `etl.py`
4. Open each `.json` file and convert to a ***pandas*** object with relevant data.
5. Take each of the converted ***pandas*** object and insert them into the database.


### How to run Project

1. Ensure `create_tables.py` ,`etl.py`, `sql_queries.py` and a data folder are present.
2. All files should be under the same folder location.
3. Data files should be kept as they are within the same folder with the rest of the scripts.
4. The `create_tables.py` file should be ran first. As it creates the database connection and creates tables.
5. etl.py can then be ran. The data base connection will be made.


### Schema

Has mentioned earlier a star schema was used with five tables in PostgreSQL. Namely:

1. Fact Table

**songplays** - records associated with song plays.

***songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent***

2. Dimension Tables

**users** - users in the app
***user_id, first_name, last_name, gender, level***

**songs** - songs in database
***song_id, title, artist_id, year, duration***

**artists** - artists in database
***artist_id, name, location, latitude, longitude***

**time** - time measurement of observations in songplays
***start_time, hour, day, week, month, year, weekday***


### Dataset

The datasets comprises of 

1. **log data**
event level information on individual songplays.

2. Song data information about the song such as Artist name, song length etc.

#### To-do

1. Add data quality checks.
2. Allow for faster ingestion with `COPY` command.

#### Libraries
1. os - searching system for files
2. glob - finding json files
3. psycopg2 - connecting with database.
4. pandas - data manipulation




### References

1. Adding serial to table.
https://www.postgresqltutorial.com/postgresql-serial/

2. Coverting tuples to dictionary
https://stackoverflow.com/questions/44706935/how-can-i-take-two-tuples-to-produce-a-dictionary