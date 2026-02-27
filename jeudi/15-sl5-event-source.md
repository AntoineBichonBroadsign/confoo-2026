event drived : event short lived, signlas
event sourced :event are source of thrut, persisted and immutable.

event sourcing attractive : 
- audit trail
- rebuildable state
- time travel
- reduce direct coupling


what went wroing : 

complexity (checkbox ui => long time to process as everything is async)
=> eventual consitency

everything is event => read capacity limited.
=> risk when large tenant onboard, burst of events.
=> number of total events growing larger exponentially


problemes : 
- noisy neigbor : impact on other tenants
- staturated connection ($$$$ to increase)
- catchup after deployment : 
  - find where you left off
  - read backlog
  - go live
  - => this takes time. 
    - rebuilding from start take weeks.
    - During the deployment, users a in readonly mode

fix event number pb : 
- snapshots
  - work for large streams, not large number of streams.
- sharding
  - temporary
- stateful actor model
  - complex
- reduce event qwuantity.


Back to simplicity : crud, udev choose archi. Faster delivery.
- 
   