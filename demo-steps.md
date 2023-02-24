# Start Hadoop
* docker compose up -d
* docker ps
* docker exec -it resourcemanager bash


# Verify Hadoop status
* Resource Manager: http://127.0.0.1:8088/cluster
* Namenode: http://127.0.0.1:9870/dfshealth.html#tab-overview
* Datanode: http://127.0.0.1:9864/
* Nodemanager: http://127.0.0.1:8042/node


# Populate crawled items to hdfs
* hdfs dfs -mkdir -p /data-examples
* hdfs dfs -put data-examples/part-00000-f9c472ee-27c4-443d-8c7f-74785d4c885a-c000.gz.parquet /data-examples/crawled-items.gz.parquet
* hdfs dfs -ls /data-examples/


# Submit filter items job
* spark/bin/spark-submit --master yarn --class SparkSQLMain app-examples/spark-example-1.0-SNAPSHOT.jar 



# Verify result on hdfs
* hdfs dfs -ls /job-output/filtered-items



# Verify job status on webui & download result items
* Check status at : http://127.0.0.1:8088/cluster
* Download items at : http://127.0.0.1:9870/explorer.html#/
