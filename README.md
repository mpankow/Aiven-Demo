# Aiven-Demo
Demo recording notes:

Spinning up a kafka cluster was incredibly simple.  
My first challenge was creating a producer.  I opted to look at Aiven resources that were publicly available and found the fake data producer.
Generating data and getting into kafka was, again, very simple.  

My second challenge was to get the data to conform with the requirements of the assignment.
I am mostly unfamiliar with Flink from a practical standpoint, but I thought I would try to use 
Flink to transform the data from the source topic into the destination topic by adding the uuid and iso 8601 fields.
This was the first big challenge and time suck for me.  In hindsight, I think I know the source of my problems. 
The fake data producer for 'realstock' created a field called "timestamp" in the JSON message.  When I tried to 
manipulate that data using flink, I couldn't get it to NOT see the column as a reserved word.  All sorts of `` and escape 
characters didn't work.

I opted to save some time by modifing the producer itself to get the  data I wanted.  That is what you will see represented
in the realstockproducer.py.  
This was also a challenge, because my docker skills were a little rusty.  Eventually I figured out where are the python 
files were and opened the docker container directly and made the modifications I needed.

Once I had data generated correctly and loaded, flink became a pretty simple task.  Admittedly, I went for a simple filter 
at this point because I had wasted too much time on the docker step and previous attempt at a flink application.

Creating InfluxDB and Grafana was as simple as it gets.  

I did have to spend some time getting familiar with the interface of Aiven console, etc. as well which took some time.  
In the end, however, I am very impressed by the UX and the value of what Aiven brings even though I barely scratched 
the surface!  Thank you for the opportunity to complete the exercise.
