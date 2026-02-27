high availability : serve while existing failures

things will fails all the time

redundancy :
  - compute
    - easy, load balancers, cloud offerings/trad solutions
    - challenge : 
      - stateless
      - version handling (deokployment, backward compability)
  - persistance
    - main/replica (read/write - read)
    - or cluster based
    - some db/clouds offer theses features
    - challenges :
      - sharding/redistributiomn
      - eventual consistency (read after write : may have a delay)

graceful degradation:
  - when HA can't be achieved (3rd party, cost)
  - defaul=t response/behavior if some parts are unavailable

active-active :
  - clone of infra and app in another region
  - both are running at the same time, arealdy hot
  - patterns : 
    - read local, write global
      - read from user region, write to a single region
      - simplest, higher latency on write
    - read local/ write partitionned
      - write go to region based on internal logic
        - for instance based on user location
      - more complex (sharding), less latency on write
    - read local/write local
      - complex : CONFLICT RESOLUTION during data replication to other regions
      - to be baked into the app from the start, not an afterthough
  - challenges : 
    - dynamic dns resolution (redirect automatically in case of error)
    - app sync : same version/compatible on multiople region
    - data sync/cost
    - conflict resolution
    - TESTING
      - force failure to validate it still works, regulary
    - clouds can help (dns, redundancy, replication)
      - dynamo global table
      - aurora dsql
    
    Costs : 
     - operational
        - traffic
        - compute extra
     - maintenance : 
        - testing
     - dev 
       - complexity of app

choose the right solutio for each component depending on cost

Ask : 
Which part could be async (help to avoid having HA)
''              have graceful degratation
'''            critical
 -    How critical ? ($)
 - what active active pattern
 - what conflict resolution approach
 - what testing schedule and validation                  


prez in confoo git repo
