## Chapter 1 Reliable, Scalable, and Maintainable Applications

### Thinking About Data Systems


- CPU is not limitation now, problem now is amount of data and how fast it is changing. 
- standard building blocks
  - databases
  - caches
  - search indexes
  - steam processing 
  - batch processing
- data systems abstract those so well we use it but don't know. 
- it is hard to combine tools when single tool is not doing the job.
- Approaches of those building blocks keeps changing with the data system having different characteristics.

what we are trying to achieve: 
- reliable
- scalable
- maintainable data systems.

- database & queue similarities, access pattern & performance
- datastore used like a message que readies, and message que used at datastore "kafka" 
- task broken down tools are stitched to perform that task using application code. 

* factors influence the design of a data system
  * skill & experience
  * legacy system dependencies
  * timescale for delivery
  * org's tolerance of sort of risk, regulatory constraints.

* Reliability
  * fault-tolerant ("possible type of faults")
  * Netflix chaos monkey ("increase rate of faults by triggering them deliberately")
  * Hardware Faults
  * Software errors
  * Human errors

#### Date: 9 - May -2025

---

* Hardware Faults
* Software errors
  - These faults are co-related across nodes (unlike hardware faults) cause many more system failures. 
  - example: leap second on june 30, runway process that uses up shared resources
    Service on which system depends slow down. Cascading failures.
  - we should do: carefully thinking about assumptions and interactions in the system, through testing; process isolation; allowing processes to crash and restart; measuring, monitoring and analyzing system behaviour

* Human Errors
 - Hardware and server faults are 10-25% rest is human.
 - we should do: well-designed abstractions, apis (however, tricky balance to get right)
   <br> Decouple the places where people mistakes from places where they can cause failures. e.g separate sandbox aws account to test things. 
   Automation, integration testing.
   <br> Allow quick and easy recovery from human errors, to minimize the impact, eg. fast rollback and rollout should be possible. 
   <br> Detailed and clear monitoring, performance & error metrics rates. (telemetry)

### Reliability
- Why important? : Damage reputation, loss in revenue, loss of productivity

### Scalability
- System's ability to cope with increasing load. 
- Consider questions like "If the system grows in a particular way, what are our options to coping with the growth"
  <br> How can we add computing resources to handle additional load? 

### Describing Load
- Load is few number we can call it load parameters.
- Choice of parameters depends on architecture of system
  - it could be requests per second to web server
  - ratio of reads and writes on db
  - no of simultaneously active users in chat room
  - hit rate on cache
  - something else
Nice example of twitter on page `11`. 

#### Date: 16 - May -2025

---

### Describing performance
- Increase load parameters and keep the system resource same. how performance is affected?
- When you increase the load how many resources required to be increase to keep performance unchanged. 

- In batch processing we care about throughput (no of records we can process per second | total time taken to complete a job on a dataset of a certain size)
- In online systems `respose time` is important i.e time between client sending a request and receiving the response. 
- Measuring average response time is not a good idea we should use `percentiles`. 
  - If you take list of response times (for specific service) and sort it from fastest ot slowest, then the median is the halfway point. 
- median is also known as the 50th percentile, abbreviated as p50.
- to find out how bad your outliers are, you can look at higher percentiles the 95th, 99th and 99.9th percentile are common. 
- e.g if 95th percentile response time is 1.5 seconds, that means 95 out of 100 requests take less than 1.5 seconds and 5 out of 100 requests take 1.5 seconds or more. 
- `head-of-line blocking` as a server can oly process a small no of things in parallel, it only takes a small no of slow requests to hold up the processing of subsequent requests.
- Due to this effect, it is important to measure response times on the client side. 
- tail latency amplification 
- The right way of aggregating response time data is to add the histograms. tools (decay, t-digest or HdrHistograme)

### Approaches for coping with load
- scaling up and scaling out
- distributing load across multiple machines known as `shared-nothing` architecture. 
- Good architectures usually involve mixture approaches: e.g using several fairly powerful machines can still be simpler and cheaper than a large number of small virtual machines. 
- Distributing stateless services across multiple machines is fairly straightforward, taking stateful data systems from single node to distributed is complex. try to keep db on a single node (scale up) until cost or high availability forced you to make it distributed. 
- System designed to handle 100,000 req/sec each in 1 kb size looks very different from system designed for 3 req/minute, each 2 gb in size -- even though the two system have the same data through-put.
- Architecture scales well for app is built around assumptions of which operations will be common and which will be rare -- load parameters.
  If those assumptions turn out to be wrong, the engineering effort for scaling is at best wasted, and at worst counterproductive. 

#### Date: 23 - May -2025

---

### Maintainability
Coming Soon....















