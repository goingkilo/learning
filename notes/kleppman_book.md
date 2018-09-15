reliability - tolerating hardware,software faults and human error. System should work correctly in the face of adversity. 
scalability - measuring load & performance, latency percentiles, throughput
	as the system grows in data volume, traffic volume or complexity, there must be reasonable ways of sustaining the growth
maintainability - operability, simplicity, evolvability. Over time many people will work on the system.

store data so that they or another application can find it later
(Persistence)
remember the result of a computation so as to speed up reads (Cache)
allow users to search data by keyword and filter it in various ways (Search indexes)
send message to another process, to be handled asynchronously (Stream Processing)
periodically crunch a large amount of data (Batch processing)

Data systems
Redis is a datastore that can be used as a messagequeue, Kafka is a messagequeue that provides database like durability guarantees

One possible architecture for a data system that combines several components.
app1 listens to requests, writes to primary persistence. (P)
app2 listens to primary persistence changes, updates info to search. (S)
also updates to in memory cache so that app1 can serve requests fast (C)
app1 uses search for full text search queries 
app1 passes async tasks to messagequeue, whose consumer app3 does outside world stuff, such as send email or crunch (SP)

Summary of components and functions
 http r/w
 cache r/w
 search r/w (index/ query)
 db (r/q)
 mq (listen/post)
 * repeat for big data versions



 notes:
 durable queues and topics ?