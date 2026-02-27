client decide what data to get
server decide where to fetch it

allow subscriptions

have defined data format.


! endpoint : post /graphql only
fragments : reusable queryes
variables

mutation : update


schemas : 
- client can only request data from schema
- version using deprecation
- type inheritance on data oject delcaration
- strongly typed, enums
- schema : describe api.
  - allow autocompletion on requetes
- queries pre-set with vairable
- build in error handling (field validation)


design zpprocah : 
 - schema first : crete schema, generate code. Good when starting on blur
 - code first : write the bakend, it generate the schema

- can't change the approah

5 pillars : 
- product centric
- hirearchical
- strong typing
- client specified response
- self documenting

subscriptions : 
- allow server to pusdh changes to clients
- transport independant


FEDERATION: 
-server  aggregator of multiple source (BFF)

postgresl support exposde graphql
