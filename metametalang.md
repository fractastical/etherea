
Metameta lang

A prospectus for a metaverse language including: 

"coordinates" (n dimensional locations passed as a set of vectors) 
"objects" (renderable objects that can be used or inserted at a specific point) 
"actions" (transforms of physics or rules) 
"identity" (access control layer whereby certain folks (admins/owners) have abilities within a given metaverse or area) 


(1,42,1)->(house)->(insert) by almost0x

Rationale:

Hardcoding objects in a given metaverse leads to non-upgradability.
Rendering is always dynamic and evolving via a DSL layer allows for maximum increase
A properly implemented access control layer would allow for multiple levels (ownership, edit rights, read only access, etc)

Open questions:

Are objects stored as pointers to a data file? If so, where is the data stored (ipfs? standard cloud layer?) 
Does identity need to be resolved to a universal layer? (e.g. ENS)
How extensible is the "actions" part of this? Can you support multiple rendering engines natively in such a way that the actions are passed directly to the rendering engine?

