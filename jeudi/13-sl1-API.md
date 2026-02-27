some http verbs are idempotent : 
get/head/options/put/delete

POSDT/patch are not

delete/put could also be not because of side effect


sdimle solution : cache reponse.
key : could be hash of the parameters
parameters : not only request content (ip, user id, etc, could not be enough), not enough most of the time.

client side : idempotenticy key header.=> easier


Backend side : create middleware to handle idempotency to incercept & cache
keep in mind checking path of query vs one from cache when pulling from cache : could be collision cause by bug/other.
/!/ add header idempotenty-replayed if pulled from catch to easier debug.

can use same system anywhere, not only around http controller

TTL for cache : depends on retry logic, business requiremet, use case :
mobile= > short (spotty connectivity, real time)
batching jobs => day-ish (time running, no hurry)
Susbscription management system => weeks (human interaction, ticket handling)
IF requirement/ regulatory  compliance : infinity (tracability, making sure we run each request, never twice)

========

Error handloing
=> cache error or not ? => decide yourself.

===========

race condition : 
2 request as]t the same timeish
=> cache locking on key, if cache found duriong the wait=> return cached value.

