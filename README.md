# HadoopWordCountSample
# Usage
Create 2 sample data files:
`echo "A long time ago in a galaxy far far away" > /home/cloudera/testfile1`   
`echo "Another episode of Star Wars" > /home/cloudera/testfile2`   

Assuming username is cloudera for following commands:
Create a directory on the HDFS file system
`hdfs dfs -mkdir /user/cloudera/input` 

Copy the files from local filesystem to the HDFS filesystem:
```hdfs dfs -put /home/cloudera/testfile1 /user/cloudera/input```
```hdfs dfs -put /home/cloudera/testfile2 /user/cloudera/input```   

Run the Hadoop WordCount example with the input and output specified.
(If your run failed first cleadn output: `hdfs dfs -rmdir output_new`)   
```bash
hadoop jar /usr/lib/hadoop-mapreduce/hadoop-streaming.jar \
-input /user/cloudera/input \   
-output /user/cloudera/output_new \   
-mapper /home/cloudera/HadoopWordCountSample/wordcount_mapper.py \   
-reducer /home/cloudera/HadoopWordCountSample/wordcount_reducer.py```  

