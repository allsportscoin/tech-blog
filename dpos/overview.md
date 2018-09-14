# Overview

![overview](\imgs\dpos_overview.png)

An overview of Dpos includes:

Candidate: The guy who  want to be a candidate of validator.

Validator: The super node, who can mint a new block.

Vote: Use can vote the candidate to be validator, the system will sort the candidate by votes and the TOP N candidates will become Validator


How to be a Candidate or Validator:

There are 4 new types of transaction to support user to become a candidate, or vote the candidate to become validator:
beCandidate, unCandidate, Delegate, Undelegate

The step to be a "candidate" of validator:

Just send a beCandidate transaction to gsoc and the value must be zero, like:
soc.sendTransaction({from:soc.accounts[0], to:soc.accounts[0], value: web3.toWei(0, "soc"), type:web3.toHex(1)},

```
> soc.accounts
["0xf609bf4160d8a1029bc525f53db93dfd95ac63ac"]

> dpos.getCandidates()
["0x2e2864f483b0f3d7cedab6e559d9bff8083dd36b", "0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1", "0x620ccdc4fb56cd575cac0b936b8dce7a61159584", "0x641ad7d61d9f79aea16e512f7962f3b137c30249", "0xf609bf4160d8a1029bc525f53db93dfd95ac63ac"]
```

0xf609bf4160d8a1029bc525f53db93dfd95ac63ac has been a candidate,

Now we vote 0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1 to become Validator

```
> dpos.getAddrVote('0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1')
[]

> soc.sendTransaction({from:soc.accounts[0], to:'0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1', value: web3.toWei(0, "soc"), type:web3.toHex(3)})
"0x6ffcb13e82a4464c196f7ab452389b050cbd6b0cc74edabfad263a34eacf0b29"

> dpos.getAddrVote('0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1')
["0xf609bf4160d8a1029bc525f53db93dfd95ac63ac"]

```

the vote transaction successed.

How to get validators:
```
> dpos.getValidators()
["0x2e2864f483b0f3d7cedab6e559d9bff8083dd36b", "0x620ccdc4fb56cd575cac0b936b8dce7a61159584", "0xf609bf4160d8a1029bc525f53db93dfd95ac63ac", "0x641ad7d61d9f79aea16e512f7962f3b137c30249"]
```

If the "Validator" Can't do the job done very well, user can vote it out.

```
> soc.sendTransaction({from:soc.accounts[0], to:'0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1', value: web3.toWei(0, "soc"), type:web3.toHex(4)})
"0x9c85b89f3d6268950c055c1f4320dae2dc7fe463eb1e1a5ce0f3e7477aa38db7"
> dpos.getAddrVote('0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1')
[]
```

The candidate can withdraw from the race of become validator

```
> soc.sendTransaction({from:soc.accounts[0], to:soc.accounts[0], value: web3.toWei(0, "soc"), type:web3.toHex(2)})
"0x6b0963e10db44c52ca0de1a8e2bcb3c8a884b799d829f11f58ddc0866fae0720"
> dpos.getCandidates()
["0x2e2864f483b0f3d7cedab6e559d9bff8083dd36b", "0x3ba1bbcb2966b0f31e46d5053817b1ae83eb77c1", "0x620ccdc4fb56cd575cac0b936b8dce7a61159584", "0x641ad7d61d9f79aea16e512f7962f3b137c30249"]
>
```

