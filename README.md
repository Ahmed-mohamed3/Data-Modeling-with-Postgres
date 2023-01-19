# Project data modeling with PostgreeSQL - Udactity Data Engineer Nanodegree

### Introduction

startup by the name of Sparkify wants to examine the information they've been gathering about songs and user behavior on their brand-new music streaming service. The analytics team is particularly curious to know which songs users are listening to. They currently lack a simple way to query their data, which is stored in a directory of JSON logs on user activity on the app and a directory of JSON metadata on the songs in their app.

### Task Description

You'll use Python to create an ETL pipeline and put your knowledge of data modeling with Postgres to use in this project. You must define fact and dimension tables for a star schema for a specific analytical focus in order to finish the project, and you must create an ETL pipeline using Python and SQL to move data from files in two local directories into these tables in Postgres.

### Program execution (How to run the Python scripts)

* firstly, run the 'create_tables.py' file to generate the database and tables (dimentions & fact).
* Then run 'etl.py' python file to create the data pipeline and ETL process 


### Schema Design

* The fact table `songplays` stores the records in log data associated with song plays i.e. records with page.
* The dimension table `users` stores the users in the app.
* The dimension table `song` stores the songs in the music database.
* The dimension table `artists` stores the artists the in the music database.
* The dimension table `time` stores the timestamps of records in songplays broken down into specific units.

#### Fact Table

| COLUMN | TYPE | CONSTRAINT |
|---	|---	|---	|	
|   songplay_id	| SERIAL  	|   PRIMARY KEY	| 
|   start_time	|   time	|   NOT NULL	| 
|   user_id	|   int	|   NOT NULL	| 
|   level	|   varchar |   	| 
|   song_id	|   varchar	|   	| 
|   artist_id	|   varchar	|   	| 
|   session_id	|   int	|   	| 
|   location	|   varchar	|   	| 
|   user_agent	|   varchar	|   	| 

#### Dimensions Tables
 **Table users**
 
| COLUMN  	| TYPE  	| CONSTRAINT  	|
|---	|---	|---	|	
|   user_id	| int  	|   PRIMARY KEY	| 
|   first_name	|   varchar	|  	| 
|   last_name	|   varchar	|  	| 
|   gender	|   varchar(1) |   	| 
|   level	|   varchar	|   	| 

**Table songs**

| COLUMN  	| TYPE  	| CONSTRAINT   	|
|---	|---	|---	|	
|   song_id	| varchar  	|   PRIMARY KEY	| 
|   title	|   text	|  	| 
|   artist_id	|   varchar	|   	| 
|   year	|   int |   	| 
|   duration	|   numeric	|   	| 

**Table artists**

| COLUMN  	| TYPE  	| CONSTRAINT   	|
|---	|---	|---	|	
|   artist_id	| varchar  	|   PRIMARY KEY	| 
|   name	|   varchar	|   	| 
|   location	|   text	|   	| 
|   latitude	|   decimal	|   	| 
|   longitude	|   decimal |   	| 

**Table time**
 
| COLUMN  	| TYPE  	| CONSTRAINT   	|
|---	|---	|---	|	
|   start_time	| bigint  	|   PRIMARY KEY	| 
|   hour	|   int	|   	| 
|   day	|   int	|   	| 
|   week	|   int	|   	| 
|   month	|   int	|   	| 
|   year	|   int	|   	| 
|   weekday	|   varchar	|   	| 

### An explanation of the files in the repository

#### create_tables.py
Creating Fact and Dimension table schema

1. create_database
2. create_tables
3. drop_tables


#### sql_queries.py
1. Drop Queries
2. Create Queries
3. Insert Queries
4. Select Queries


#### etl.py
this file is responsible for building the pipeline and completing the ETL process.

There are three main processes in it:
1. process_data --> Iterating dataset to apply 'process_song_file' and 'process_log_file' functions
2. process_song_file -->  Process song dataset to insert a record into (songs & artists) dimension table
3. process_log_file --> Process log file to insert the record into (time & users) dimension tables and (songplays) fact table

