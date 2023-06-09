
# Project Data Lake
## Project Overview
A music streaming startup, Sparkify, has grown their user base and song database even more and want to move their data warehouse to a data lake.

In this project, we will create a script/pipeline in pyspark that will extract raw data from s3 data lake (JSON) and process those files in AWS EMR.
After processing, this data will be stored in S3 data lake as parquet files.

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

# Output data
* Songs : s3://udacity-dend-output/songs
* users : s3://udacity-dend-output/users
* artists : s3://udacity-dend-output/artists
* songplays : s3://udacity-dend-output/songplays
* time : s3://udacity-dend-output/time

### Data is present in JSON format.  
### Output data will be in Parquet format.
### AWS EMR is being used to process this big data.

# Schema Design

### Parquet files have been created based on the below schema design.
<center>
<img style="float: center;height:400px;" src="Schema_Design.jpg"><br><br>
</center>

# How to run the Python File
## 1. Through SSH
 * create the S3 storage for output
 * Create an IAM **adminaccess** role and note down the **access and secret key**. Put these values in **dwh.cfg** file.
 * Create an EMR cluster from AWS console. Follow the steps provided in the FAQ section to connect to EMR Cluster through SSH.
 * Use the command to run the file "spark-submit etl.py"
 * Finally delete the cluster and S3 storage.
## 2. Through Notebook
 * create the S3 storage for output 
 * Create an EMR cluster from AWS console. Follow the steps provided.
 * Create a notebook.
 * Copy the code from etl.py and run in the notebook.(No need for access key and spark initialization)
 * Finally delete the cluster and S3 storage.

# EMR Notebook Snapshots
# Code starts running on EMR Notebook

<center>
<img style="float: center;height:700px;" src="query1.png"><br><br>
</center>

# Songs folder created on S3

<center>
<img style="float: center;height:700px;" src="query2.png"><br><br>
</center>

# Data started getting populated in S3 in songs Folder

<center>
<img style="float: center;height:700px;" src="query3a.png"><br><br>
</center>

