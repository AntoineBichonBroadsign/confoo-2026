message brokers : provider queue + storage
idemnpotency : no side effect for duplicated message, important.

- point to point
  -  1 producer, 1 conmsumer.
  - garantee delivering, simplicity, reliability, load balancing
  - single poiont of failure, message ordering, scalability, overhead

- pub sub
  - publisher to topics, multiple subscribers
  - message broker handle topic and subscription
  - subscribers listen to subscribers
  - decoupling, multiple consumer, scalability and flexibility.

- competing consumers :
  - multi consumer read the queue
  - consume concurrency
  - broker hands message to consumers
  - drawnback : message ordering, coordination

- message filtering :
  - consumer selectively receive message based on criteria
  - a message router decide what to do, not the consumer
  - drawback : complexity, overhead, scalability

- DLQ : 
  - for unprocessable messages
  - remember to look at them.
  - could be used for expired messages


- sequence convoy pattern : 
  - ensure that related message are in processed in order => enforce message ordering
  - compoenent : 
    - message queue
    - order key
    - sequential processor : broker
  - data integraity, consistency
  - reduced throughput, latency, complexity
  
- request/reply messaging :
  - requester wait for a reply. => enable synchronous communication
  - request contains the response queue name
  - simplify workflow, reliable, control & coordination
  - scalability issue, latency, single point of error

- scatter -gather : 
  - requesdt sent to multiple recipentm, responses are aggregasted
   - => parallel processing and aggregation on result
  - requester sends a  message
  - scatter recipient handle message, procsedd and sent to gather ueue
  - gatherer gather fromn the gather queue, and aggregate the result
  - scalability, resilience
  - complexity, latency, scalability

- saga : 
 - break a transactio in smaller independant test
 - saga coordinator, send in step queue sucessively
    - transaction step consumer sent ACK to ACK queue
    - neach ACK trigger next message from coordinatior
    - backup function in case of error/no ACK
  biggest problem . compensating logic to define.


  

