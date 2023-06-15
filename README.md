# Aiven-Demo

#Phase I - Aiven for Kafka Service
Creating a kafka service and getting connected was incredibly simple.  Loved the simplicity of the interface.

#Phase II - Produce data
My first challenge was creating a producer.  Knowing I had to figure out 4 integrations and that flink would likely 
take some time, I opted to look at Aiven resources that were publicly available and found the fake data producer
(https://github.com/aiven/python-fake-data-producer-for-apache-kafka).  Getting that to work was relatively trivial 
other than the laptop I was using had no tools or apps installed.  

#Phase III - Transform data
My second challenge was to get the data to conform with the requirements of the assignment.  Specifically an uuid and 
date field that conforms to iso 8601 formatting.  My first attempt at data transformation was with a flink application.
My flink knowledge is mostly conceptual, so I was prepared to spend some time learning while I build.  This was the 
first big challenge and time suck for me.  My problem had more to do with one of the key:value pairs in the JSON message
created by the python producer.  The fake data producer for 'realstock' created a key called "timestamp" in the message.  
When I tried to manipulate that data using flink, I couldn't get it to NOT see the column as a reserved word.  All sorts 
of `` and escape characters didn't work.  

After some time, I decided to pivot and modify the producer itself to get the data I needed. That is what you will see 
represented in the realstockproducer.py. This proved challenging because my docker skills were a little rusty.  Eventually 
I figured out the the python files were in the container (not pulled as part of the clone command) and then I opened the 
docker container directly and made the modifications I needed.

#Phase IV - Create Flink filter app
Once I had the data generated correctly and loaded into a new topic, flink became a pretty simple task.  Admittedly, I went 
for a simple filter at this point because I had wasted too much time on Phase III.  The SQL used for my flink app is in the 
flinkapplication file which outlines the SQL for the source table, sink table, and filter condition.

#Phase V - Metrics and Observability
Creating InfluxDB and Grafana was as simple as it gets.  The integration was seemless and intuitive.  At this point, I was 
getting comfortable with the console and how to manage integrations.  It was point and click from here.

#Summary
Although I had to dust off some skills and experient with some new ones, I found the UX to be clean and intuitive.  Additionally,
I found the Aiven youtube channel, docs, and github to be a wealth of super useful information.  I am very impressed with Aiven 
and the value of what Aiven after only scratching the surface! I appreciate the opportunity to complete the exercise.  
