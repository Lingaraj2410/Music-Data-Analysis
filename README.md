Tested on: Spark 2.0
-----------------------

Copy the project and uzip it
Move the entire directory structure to /home/acadgild

Run MySQL
sudo service mysqld start

Make sure all the scripts in /home/acadgild/project/scripts have  774 permissions
Run below command:

chmod 774 /home/acadgild/project/scripts/*

Build the scala project
-----------------------
1. Install SBT

Reference link:

https://acadgild.com/blog/sbt-in-centos/

2. Navigate to the following path to Spark source project:

cd /home/acadgild/project/scripts/MusicDataAnalysis

Run the command given below to build a JAR file for execution:

sbt clean package


Scripts:
--------
generate_web_data.py -- Generates some random data coming from web application

python /home/acadgild/project/scripts/generate_web_data.py


generate_mob_data.py -- Generates some random data coming from mobile application

python /home/acadgild/project/scripts/generate_mob_data.py

sudo service mysqld start

start-daemons.sh -- Launches all necessary daemons

sh /home/acadgild/project/scripts/start-daemons.sh


create_hive_hbase_lookup.sh -- Creates hive table over HBase

sh /home/acadgild/project/scripts/create_hive_hbase_lookup.sh


populate-lookup.sh -- Populates lookup tables

sh /home/acadgild/project/scripts/populate-lookup.sh


dataformatting.sh -- Performs data formatting

sh /home/acadgild/project/scripts/dataformatting.sh


data_enrichment.sh -- Performs data enrichment and cleaning

sh /home/acadgild/project/scripts/data_enrichment.sh

data_analysis.sh -- Performs data analysis

sh /home/acadgild/project/scripts/data_analysis.sh

Scheduling:
-----------
We'll be using crontab for job scheduling.
Job has to run every 3 hours

sudo crontab -e

(Press i to enter insert mode)

* */3 * * * /home/acadgild/project/scripts/wrapper.sh

(Press Esc and then type :wq! and press Enter)
