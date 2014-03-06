Green ether
====================

**Goal**: Create a distributed reputation system that exists on the blockchain and does not rely on any third party service or force real name verification, but nonetheless enables high trust. Ideal features include incentives for network participation and disincentives for "trust-violating" measures. This would ideally tie into some "proof of excellence" or, as I have called it, "[proof of awesomeness](http://evergreenthoughts.quora.com/Proof-of-Awesomeness)" measure that better represents value to the network than existing PoW/PoS mechanisms. 

Green ether contract
---------------------

**Endorsements**:  

  - Upon contract initialization 50 "genesis green ether" is created *ex nihilo* and given to the person initializing the contract 
  - each endorsement has a value from 1-5
  - every time someone receives an endorsement of x value, x is subtracted from the endorser, recipient gets 2x  
  - each endorsement also has a "hop value" which is the distance from the genesis endorsement

**Value**:  

  - green = highest single value endorsement 
  - value of an endorsement is  ( value / hops ) * 20  

  ex. 
  
      first level strong endorsement would be 5 / 1 * 20 = 100
  
      first level weak endorsement 1 / 2 * 20 = 20
  
      second level strong endorsement would be 5 / 2 * 20 = 50
  
      second level weak endorsement would be 1 / 2 * 20 = 10
  
      third level strong endorsement would be 5 / 3 * 20 = 33.33

   - As seen above, distance from genesis transaction is extremely important for establishing in network trust. 

**Reputation Query**:  

   - you can query a user's ethereum hash to get his "reputation", reputation is green score - black score  


**Overview**:  

  - input paths

    -- initialization

    -- query user for reputation 
    
    -- send endorsement (cost: value of endorsement)
    
    -- withdraw endorsement (cost: .5x value of endorsement) (optional?)


Black (i.e nullification) ether contract
---------------------

   - vote of x number people with green score over y is sufficient to nullify a green score of z 
   ex. 
      a person of a score of 30 is responsible for theft, at least 5 people with a reputation of x + 20 (i.e. 50) must vote to initialize a black ether transaction. The black ether attributed is the difference of the mean of the voters (i.e. 45 ) minus the green ether value of the thief (i.e. 30). In this case, a black ether of 15 would be attributed, lowering the thief's reputation to 15 (30 - 15) 
   - endorsers get a "negative endorsement" which traverses backwards over the chain via anti-hops, with a maximum of 2 hops
   - "black" ether  degrades over time, with a half-life of .1 years per point (???)

Basic income contract
---------------------

  - funded via primary transfer
  - some portion of currency inflation goes into this (either via Ether main currency or some subcurrency)
  - iterates through every member and sends x ether to every member with a green score over y

"Loyalty" contract
---------------------

  - product query via product hash 
  - price check references "green" and only allows transaction if green score is over x (i.e. 10)
  - price check references "green score" and gives 10% discount if green score is over y (i.e. 40)


Considerations
---------------------

  - Work on implementation
  - How far should the black ether go back up the chain and what threshold should be necessary to trigger black ether?
  - if you allow increase in green ether down the chain, how do you prevent spurious endorsements? 

