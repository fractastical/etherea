
##Metameta lang

###A prospectus for a metaverse language including: 

"coordinates" (n dimensional locations passed as a set of vectors) 

"objects" (renderable objects that can be used or inserted at a specific point) 

"actions" (transforms of physics or rules) 

"identity" (access control layer whereby certain folks (admins/owners) have abilities within a given metaverse or area) 


(1,42,1)->(house.1234.aws.com)->(insert) by almost0x

almost0x inserts a house object at the coordinates 1,42,1

((1,42,1)->(2,41,0))->(go) by solanaN00b

SolanaN00b moves location from 0,0,0 to 1,42,1 and then in the direction 2,41,0. (i.e. each location is a set of vectors). This allows any given location to also be a portal into a different location. 

##Rationale:

Hardcoding objects in a given metaverse leads to non-upgradability.

Rendering is always dynamic and evolving via a DSL layer allows for maximum increase

A properly implemented access control layer would allow for multiple levels (ownership, edit rights, read only access, etc)

##Open questions:

Are objects stored as pointers to a data file? If so, where is the data stored (ipfs? standard cloud layer?) 

Does identity need to be resolved to a universal layer? (e.g. ENS)

How extensible is the "actions" part of this? Can you support multiple rendering engines natively in such a way that the actions are passed directly to the rendering engine?

How can the ownership layer be clearly transcribed, esp. in such a way that natively works cross platform? (may be an impossible dream) 
