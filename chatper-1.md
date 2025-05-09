
- CPU is not limitation now, problem now is amount of data and how fast it is chaning. 
- standard building blocks
  - databases
  - caches
  - search indexes
  - steam processing 
  - batch processing
- data systems abstract those so well we use it but don't know. 
- it is hard to combine tools when single tool is not doing the job.
- Approaches of those building blocks keeps changing with the datasystem having different carecteristics.

what we are trying to achieve: 
- reliable
- scalable
- maintainable data systems.

- database & queqe similarities, access pattern & performance
- datastore used like a message que redies, and message que used at datastore "kafka" 
- task broken down tools are stiched to perform that task using application code. 

* factors influence the desing of a data system
  * skill & experience
  * legacy system dependencies
  * timescale for delivery
  * org's tolerance of sort of risk, regulatory contanstraints.

* Reliability
  * fault-tolerent ("possible type of faults")
  * Netflix chaos monkey ("increate rate of faults by triggering them deliberately")
  * Hardware Faults
  * Software errors
  * Human errors

Date: 9 - May -2025

* Hardware Faults
* Software errors
  - This faults are co-related across nodes (unlike hardware faults) cause many more system failures. 
  - example: leap second on june 30, runway process that uses up shared resources
    Service on which system depends slow down. Cascading failures.
  - we should do: carefully thinking about assumptions and interactions in the system, through testing; process isolation; allowing proceesses to crash and restart; measuring, monitoring and alayzing system behaviour

* Human Errors
 - Hardware and server faults are 10-25% rest is human.
 - we should do: well designed abstractions, apis (however, tricky balance to get right)
   <br> Decouple the places where people mistakes from places where thye can cause failures. e.g seperate sandbox aws account to test things. 
   Automation, integration testing.
   <br> Allow quick and easy recovery from human errros, to minimize the impact, eg. fast rollback and rollout should be possible. 
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
  - no of simultaneoursly active users in chat room
  - hit rate on cache
  - something else
Nice example of twitter on page `11`. 

### Describing performance
- 



















