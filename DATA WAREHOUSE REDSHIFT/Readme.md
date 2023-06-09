# Project Data Warehouse
## Project Overview
A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud.

In this project, we will create an ETL pipeline that will extract raw data from s3 and load into staging tables on Redshift.
Then from these Staging Tables a star schema DW will be created on Redshift.

# Input data 
Data residing on S3 data lake
* Song data: s3://udacity-dend/song_data
  * SONG JSON File
    ##### song_data/A/B/C/TRABCEI128F424C983.json
  * SONG JSON File Contents
    ##### {"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}

* Log data: s3://udacity-dend/log_data
  * LOG JSON File
    ##### log_data/2018/11/2018-11-12-events.json
  * LOG JSON File Contents

 <center>
 <img style="float: center;height:400px;" src="log-data.png"><br><br>
 </center>

### Data is present in JSON format. So, Appropriate Reshift queries have been applied. 
### The data from the S3 buckets is to loaded into staging area in Redshift.

# Schema Design

### Fact and Dimension tables have been created based on the below schema design from staging tables in Redshift.
<center>
<img style="float: center;height:500px;" src="Schema_Design.jpg"><br><br>
</center>

# How to run the notebook

* I have used the IAC notebook to create the cluster programmatically and have used jupyter notebook **Redshift_test.ipynb**.
* First create an IAM **adminaccess** role and note down the **access and secret key**. Put these values in **dwh.cfg** file.
* Then start executing each cell of the notebook and run all cells till cluster creation. After cluster gets created.
* Check the status of the cluster if it is available. Note down the **ARN & Endpoint**. Again put these values in **dwh.cfg** file.
* Then run the **!python3 create_tables.py** to drop and create the tables.
* Then run **!python3 etl.py** to create the tables in the redshift.
* Run some queries on **Query Editor**.
* Finally delete the cluster.


# Queries ran on query editor to check the tables
# Query 1 -  No of male and female users

<center>
<img style="float: center;height:700px;" src="query1.png"><br><br>
</center>

# Query 2 - Find data whose song duration is greater than 100 in the year 2004 and title startswith "M"

<center>
<img style="float: center;height:700px;" src="query2.png"><br><br>
</center>

# Query 3 - Shows the population of all the tables

<center>
<img style="float: center;height:700px;" src="query3a.png"><br><br>
</center>
<center>
<img style="float: center;height:700px;" src="query3b.png"><br><br>
</center>
