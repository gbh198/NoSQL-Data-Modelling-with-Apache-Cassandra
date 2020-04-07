Gia-Bao HUYNH | [LinkedIN](https://www.linkedin.com/in/gbh198/) | DURING QUARANTIE TIME | [UDACITY Data Engineering NanoDegree](https://www.udacity.com/course/data-engineer-nanodegree--nd027)

# **NoSQL Data Modelling with Apache Cassandra**

## Table of Contents
-	Preamble
-	Introduction
-	Data Source
- Schema Design
-	Project Template
-	How To Use
- Potential Bugs

## Preamble
This repo is my work for the Data Modelling project with Apache Cassandra in UDACITY [Data Engineering NanoDegree](https://www.udacity.com/course/data-engineer-nanodegree--nd027). Thank you Udacity team for all the support you have provided. 

## Introduction
A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their music streaming app. The analysis team has some difficult questions (queries) demanding answers. Currently, all data generated are in CSV format residing in data stores on the app. They come up with a NoSQL database solution such as Apache Cassandra to store and retrieve data. 

NoSQL approach is totally different to the way we used to think of SQL. A NoSQL Apache Cassandra database offers some special features that best fit the use of Big Data: Schema Denormalization, Distributed System with highly-horizontal scability, column-oriented storage and of cours... a free-and-open-source tool.

That denormalization is a must when doing data modelling with Apache Cassandra helps reduce time complexity of READS because DBMS will not travel a lot by bridges called "joins" to pull data. Moreover, denoramalization with Apacha Cassandra style could do much more than that by increasing speed of WRITES. It seems constrast to the logic of Star or Snowflake schema but in Cassandra we say no to 'joins' and we ensure one query queried in one table! No more joins, no more time running around.
[Find out more...](https://docs.datastax.com/en/dse/6.7/cql/cql/ddl/dataModelingApproach.html)

Column-oriented storage is another benefit of Cassandra that could make data organization (by data patritions distributed to hard-disk blocks) is optimized. 
[Checkout](https://en.wikipedia.org/wiki/Column-oriented_DBMS) a good write of this technique.

However, Apache Cassandra also has its own drawbacks in CAP theorem and ad-hoc queries. 
Ad-hoc queries with potential joins or complex techniques will not work on isolated tables in Cassandra. 
CAP theorem stating that it is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees: Consistency (C), Availability(A), Partition tolerance (P). Cassandra goes for AP, sacrificing C.
While nodes are going to fail as nature of a distributed system, the choice of AP is best to serve for apps that require data availability. Immediate consistency is not satisfied but Eventual Consistency will be. 

[Find out more...](https://en.wikipedia.org/wiki/CAP_theorem)

It always depends on the use-cases that we intend to apply but it is good to bear in mind such drawbacks.

Apache also offers CQL, similar to SQL with other conventions such as no JOINS nor GROUP BY. 
[A doc](http://cassandra.apache.org/doc/latest/cql/) from Apache Cassandra offical website will say it all. 

It is my job, as a data engineer, to build a database and, afterwards, insert all data extracted from CSV files to this database. In the context of this project I only made a demo of Jupyter Notebook for all steps. We can always create a python files with automation fashion.

## Data Source

For this project, we'll be working with one dataset: event_data. The directory of CSV files partitioned by date. Here are examples of filepaths to two files in the dataset:
- event_data/2018-11-08-events.csv 
- event_data/2018-11-09-events.csv

Here is a demo photo of a file after processing:

![Image of Yaktocat](https://github.com/gbh198/NoSQL-Data-Modelling-with-Apache-Cassandra/blob/master/image_event_datafile_new.jpg)

Or you can check full version at [event_datafile_new.csv](https://github.com/gbh198/NoSQL-Data-Modelling-with-Apache-Cassandra/blob/master/event_datafile_new.csv).

## Schema Design

As discussed above, one query per table therefore this database is comprised of 3 tables for 3 following queries: 

1. Give me the artist, song title and song's length in the music app history that was heard during  sessionId = 338, and itemInSession  = 4
2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'



## Project Template
 
-	**Data Modelling with Apache Cassandra.ipynb** – This notebook explains all logical opearation for complete process.


## How To Use
**Required libraries and programs**

- Jupyter Notebook
- Apache Cassandra Installed
- Python Libraries Installed 

Checkout **Data Modelling with Apache Cassandra.ipynb** file.

## Potential Bugs

For run-time bugs, if it throws bugs about checkpoints and data will not return more than 6000 rows, run this command on terminal:
rm -r .ipynb_checkpoints

