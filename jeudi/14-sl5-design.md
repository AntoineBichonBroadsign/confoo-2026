architecture : fit within context
context = product
produict evolve

strategic DDD :
- product perspective : find step in the product usage (workflow)
-                         then identify significant events in the flow
- list high level command(actions)/events
=> allow do split/define boundaries around domains/teams

couping intentional can be good.

Model exploration Whirlpool

reporting <> get all data => reporting target specific cases/data

look for words having multiple definitions.

====================

c4
c1 : context : product context (very high level, between products) (IE ; bank, : user, system, db, email system)
c2 : container (modules in a product) : high level (web app / DB/ mainframe/ mobile/ API, personnal banking user)
c3 : component : inside module (email copmpoenent, account sumnmaytr)
c4: class level.

look out for loops

====================

context mapping
look out for domain needing to evolve more rapidly than sone others and plan to allow it.

===================

architecture decision record : 
keep track of archiceture choice, timestamped with context and consequence listed. (allow to explain the tradoff of the choice)
TEam making the ecision should be the one writing the record.

======================

start with the problem, not the solution.
