First contract example

if tx.value < 100 * block.basefee:
    stop

VB: stop if there's not enough ether to complete 
VB: idea if that it will take roughly 100 times basefee
VB: incoming tx triggers contract
VB: would be good to have opcode that describes how much has already been spent on this transaction, we could add this

elif contract.storage[1000]:
    from = tx.sender
    to = tx.data[0]
    value = tx.data[1]
    if to <= 1000:

   VB: potential exploit, what if to is close to 0, could send a malicious transaction that could overwrite this coe
   VB: also what if someone else sets "to" to 1000. 
   VB: 1000 is an arbitrary number, needs to be high enough that there's no likelihood of overlap

        stop
    if contract.storage[from] < value:
        stop

VB: Tontract register that address as having that amount of money to send

    contract.storage[from] = contract.storage[from] - value
    contract.storage[to] = contract.storage[to] + value
else:
    contract.storage[mycreator] = 10^18
    contract.storage[1000] = 1


VB: contract gets executed in every full node of the network
VB: verified by a miner 

Q: will the ethereum have rpc calls or be JSON compatible? 
A: yes, http host in dev, all the stuff that makes it easy to work with

Q: would be interesting elaborate on the secure data feeds, and how they are implemented in these contracts
A: two ways to do a secute date feed, it's a data storage contract, key value database, that feed owners set to whatever they want. this is a simple way of doing it. a more efficient way of doing this is to have your datafeed off the blockchain, any time you have a contract that is dependent on a datafeed, it would requrie transactions to include in their datafeed the assigned datafeed.

Q: in the data feed there would be a url and a signature?
A: ETH doesn't know about the internet protocls, all ETH would need to care about is public keys and signitures. 

Q: how does their (Bloomberg's) data get into your contract?
A: Contract would need to rely on one of the parties of the contract, including the signed datafeed for one of the contracts in the transaction. The contract would contain Bloomberg's public key, and provide for the data 

Q: you would verify the signiture wihtin the ES Script
A: yes


Q: How does a future event get into the blockchain?
A: Contracts only ever excecute when you send transactions to them. 

Q: How does a contract influence the Bitcoin blockchain. Can it read the blockchain?
A: One setup is the on blockchain datafeed, yes you can look inside other contracts. If they are using an off blockchain datafeed, it would be able to look at it, would require the data to be fed in through a transaction. Every contract can access any other contract.


Second contract example: 


	if tx.value < 200 * block.basefee:
	    stop
	if contract.storage[1000] == 0:
	
	 VB: error, should be 1 not 0, should increment the state 
	
	    if tx.value < 1000 * 10^18:
	        stop
	    contract.storage[1000] = 0
	    contract.storage[1001] = 998 * block.contract_storage(D)[I]
	
	VB: fetches the price of either in dollars (assuming is stored there) 
	    contract.storage[1002] = block.timestamp + 30 * 86400
	    contract.storage[1003] = tx.sender
	else:
	    ethervalue = contract.storage[1001] / block.contract_storage(D)[I]
	    if ethervalue >= 5000 * 10^18:
	        mktx(contract.storage[1003],5000 * 10^18,0,0)
	
  VB: contracts can make transactions, sending to counterpart, check if contract has expeired yet to, send the right amount to the other persons, the remainder goes back to the contract creator. 
	
	    else if block.timestamp > contract.storage[1002]:
	        mktx(contract.storage[1003],ethervalue,0,0)
	        mktx(A,5000 - ethervalue,0,0)

  VB: at the end there should be 1000 ether, plus an additional 1000 ether
  VB: first of all we calculate what the current ethere value of this quantity of dollars is, how many ethers is party A entitled to
  VB: over here, 



Contract example 3: 

if tx.value < tx.basefee * 200:
    stop
if contract.storage[tx.sender] == 0:
    stop
k = sha3(32,tx.data[1])
if tx.data[0] == 0:
    if contract.storage[k + tx.sender] == 0:
        contract.storage[k + tx.sender] = 1
        contract.storage[k] += 1
else if tx.data[0] == 1:
    if tx.value <= tx.datan * block.basefee * 200 or contract.storage[k]:
        stop
    i = 2
    while i < tx.datan:
        contract.storage[k + i] = tx.data[i]
        i = i + 1
    contract.storage[k] = 1
    contract.storage[k+1] = tx.datan
else if tx.data[0] == 2:
    if contract.storage[k] >= contract.storage[2 ^ 255] * 2 / 3:
        if tx.value <= tx.datan * block.basefee * 200:
            stop
        i = 3
        L = contract.storage[k+1]
        loc = contract.storage[k+2]
        while i < L:
            contract.storage[loc+i-3] = tx.data[i]
            i = i + 1
if contract.storage[2 ^ 255 + 1] == 0:
    contract.storage[2 ^ 255 + 1] = 1
    contract.storage[C] = 1


  VB: leave this for homework, 2/3rds voting cystem

Q: If I want to make a contract that allows me to own other address, then a contract would need to own a private key, but it seems like there is no way for a contract to have secret information, is that right? 
A: you are correct given current knowledge of crypto there is no way for a contract to hold private information, that even though they cant' have a private key it can own it's own address. contract can make a transaction. You can have a decentralized organization make transactions to a sending address VB: address to the key and address are equivalent

Q: Suppose we want to make an investment fund, assets are controlled by contract, not by me as a man, can't withdraw assets, w/o agreement of investors. Without private keys is this possible?
:A you would need to setup a contract in such a way, so that it would give your address the right to make trade,s but only the client's address the right to make the withdrawals. 
 Contract would remain ownership of the asset,s contracts are first class citizens. C

Q: by asset I don't mean ethereum, but in a different place
A: ahh that is more complex and difficult. BTC scripting language may or may not be powerful enough to do that. Now BTC scripts have been even more restrictive. you would need to have a subcurrency within ETH that represents BTC. There would need to be come mechanism like a cross-chain swap mechanism, between Blockchain and 

Q: I don't mean just BTC but any asset that is represented in another ETH contract? Can you have something that would represent shares of google in which it could be traded but not "cashed out" by investment manager? 

A: Take subcurrency contract, representing Googleshares, contract has an address, balance is X. That contract would be able to transfer google shares and it would be able to figure out the current balance of shares, this is actually fairly simple subcurrency You could have a subcurrency that includes its own built in exchange, would need to have different clauses, like DAO contract. 

Your investment type contract would have different clauses. like trans. type 1, might be sell unites of say this other subcurrency for ether. That clause would check if the transaction is you, and if it is you then it would put up a market order or accept a market order. There might be another clause, which is the withdraw clause, which might have the ability to send ether back to your client. That clause would actually check if the sender is your client. You can have these subcontracts which have sub clauses in them, and each subclause can have different level of permission. Other clauses can be acceptable from other accounts. each can be restricted to various ratios, transactions that it can make.

Q: How can you prevent DOS attacks based on malicious contracts? I
 Example might be BTC malleable transactions. 
A: We aren't affected by malleable transactions, response to each individual concern.

Q: Isn't there isn't a CPU problem with all these contracts being executed simultaneous?
A: Once you have these things broken out they can be just in time compiled into machine code, end contract engine can immediately replace this with some kind of pre-compiled version. Include "light coins" ___ <VB: didn't understand

Q: Can you walk us through executing an external contract? Something that's inside contract but outside the rest of ETH
A: "i" is the index of ethereum. 

== 

Q: Regardless of the contract author some of the other stuff is not accessible, api of the other contract.

Q: Do you see an ecosystem with a lot of small utilitarian contracts that are expensive?

A: This is an example of a simple contract, used then shut down, you could have a subcurrency to have five different clauses, clause for financial derivatives, you could reimplement the whole mastercoin spec as a subcurrency,

Q: Author needs to be really sure of the maximum fee, either based on API call or knowing the ether cost in advance? If not contract halts?
A: Right, we've gotten a lot of feedback that indicates that this is a problem so we are strongly considering an op code that gives the amount of ether left, this would allow a smooth early exit

Q: I have a question regarding reproducibility. Seems that this would get executed same way in different nodes, if these contracts would or can have any side-effects
A: wAy that i'm looking to change the scripting language to set things up, that two contracts act in same way, the contract would only be stored once, then data and code would be separate

Q: wasn't my question, if contract only gets executed once you want it to be verified by another node. Is that true?
A: Yes, then, i would imagine that a contract couldn't do anything exactly replicable on a different minter
A: Right, they would need to be fully deterministic. 
Q: No exceptions?
A: Right, no exceptions?

Q: How does ethereum access the BTC blockchain?
A: Ethereum code would need to have code to validate Merkle contracts, so you would need to have an SPV client implementation inside a contract, which is possible. You would need the merkle branch to be included, including proof of work on the block header, if this all checks out then it would have pretty good evidence that this is a legitimate BTC transaction

Q: Can a contract run periodically on its own or does it need an incoming txn?
A: Right now it needs a txn, although we could change this if we get feedback indicating this is a necessary feature

Q: There are these questions about BTC and hiding a private key, I wonder if the code optimization coudl allow obfuscation inside ethereum?
A: Optimization will do nothing to allow obfuscation. It will need to be fully written out in Ethereum script. In terms of obfuscation, but you can find this article on the BTC MAgazine or Ethereum blog, some research that has come out recently, there is a way to turn a -VB: program into an obfuscated program. right now it is extremely inefficient but it is possible that it could be included later on if it is improved

Q: My question is about the ETH how they change hands? Is it possible that they would change the source? ETH end up in only the hands of certain people, whoever can execute the contracts. They get paid in ETH.
A: Right now we are thinking of burning transaction fees. The nice thing about ETH in terms of what it is different from BTC, the supply doesn't stop growing. Doesn't accelerate. 

Q: I saw the thread on annotating smart contracts, if you could add a comment then it would help understand people how to do them. Add comments in the compiler?
A: Right now the compiler does not support comments, but it will.

Q: It feel to me that as much as I like ETH that is is really raw, like before Satoshi related it. 
A: Yes, the whole point of a pre-sale is for us to get the resources to bring it to completion. At the end we will have all the resources that BTC has. Very much like BTC in 2008 at this point.

Q: How does the contract get executed on all nodes?
A: Executing every contract in a block is a part of validation...

Fundraiser ideally starting at the same time as the texas BTC conference. 


































  
