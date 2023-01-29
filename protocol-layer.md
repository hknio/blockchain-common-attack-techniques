# 🤝 Protocol Layer Attacks

## Table of Contents

* [Consensus](protocol-layer.md#consensus)
  * [Long Range Attack](protocol-layer.md#long-range-attack)
  * [Race Attack](protocol-layer.md#race-attack)
  * [Liveness Denial](protocol-layer.md#liveness-denial)
  * [Finney Attack](protocol-layer.md#finney-attack)
  * [Vector76 Attack](protocol-layer.md#vector76-attack)
  * [Alternative Historical Attack](protocol-layer.md#alternative-historical-attack)
  * [51% Attack](protocol-layer.md#51-attack)
  * [Stake Grinding Attack](protocol-layer.md#stake-grinding-attack)
  * [Coin Age Accumulation Attack](protocol-layer.md#coin-age-accumulation-attack)
  * [Nothing-at-Stake Attack](protocol-layer.md#nothing-at-stake-attack)
  * [Block Double Production](protocol-layer.md#block-double-production)

## Consensus

### Long Range Attack

* Severity: High
* Description:\
  A Long-Range attack is an attack scenario where the adversary goes back to the genesis block and forks the blockchain. The new branch is populated with a partially, or even completely, different history than the main chain. The attack succeeds when the branch that is crafted by the adversary becomes longer than the main chain, hence it overtakes it. Long-Range attacks fall into three different categories, namely Simple, Posterior Corruption, and Stake bleeding. In some sense, Long-Range attacks in PoS protocols are related to selfish mining attacks of PoW protocols as the attacker in both cases is adding blocks that are kept secret. Obviously, selfish mining attacks cannot go back to the genesis block of PoW protocols as the computational effort needed is prohibiting, therefore, the impact that they may have is limited. Nevertheless, both attacks fork the main chain and try to append forged blocks where the attacker potentially includes different transactions.
* Recommendation:\
  Assigning a list of bootstrap nodes, implementing checkpoints, and assigning a range of blocks to always be considered true. Any of these recommendations can prevent this attack from succeeding.
* References:
  * [A Survey on Long Range Attacks for Proof of Stake Protocols](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8653269)
  * [Rewriting History: A Brief Introduction to Long Range Attacks](https://blog.positive.com/rewriting-history-a-brief-introduction-to-long-range-attacks-54e473acdba9)

### Race Attack

* Severity: High
* Description:\
  Is a type of “Unconfirmed Transaction” Attack. A race attack is executed when an attacker creates two conflicting transactions. The first transaction is sent to the victim, who accepts the payment (and sends a product, for instance) without waiting for confirmation of the transaction. At the same time, a conflicting transaction returning the same amount of cryptocurrency to the attacker is broadcast to the network, eventually making the first transaction invalid.
* Recommendation:\
  Wait at least 6 or more confirmations on the network to consider a transaction safe and irreversible.

### Liveness Denial

* Severity: High
* Consensus affected: PoS / DPoS
* Description:\
  Liveness Denial is a form of Denial of Service attack in PoS protocols. In this attack, some or all of the validators decide to take action and purposefully block transactions by stopping publishing blocks. By avoiding to perform their validator duties, the blockchain will come to a halt as new blocks would not be able to be validated and published in the blockchain. A liveness requirement which slowly drains the stake of inactive validators will ensure that even if the majority of validators are either offline or performing a liveness denial attack, they would not compromise the network.
* Recommendation:\
  In cases where liveness cannot be assessed, the community will be able to decide (off-chain communication) to fork the blockchain and remove the inactive validators. In all cases, validators who conduct this type of attack jeopardize their position in the network as validators and their stake if a slashing condition exists

### Finney Attack

* Severity: High
* Consensus affected: PoW
* Description:\
  The Finney attack is named after Hal Finney, who suggested it [in this comment](https://bitcointalk.org/index.php?topic=3441.msg48384#msg48384). (Hal is the first recipient of a Bitcoin transaction, and the first person to comment on the release of the Bitcoin source code.) The Finney Attack is a type of double-spending attack that proceeds as follows:

1. The attacker mines blocks normally; in the block he is trying to find, he includes a transaction that sends some of his coins back to himself (from his main wallet to another that he also controls) without broadcasting this transaction.
2. When he finds a block, he does not broadcast it; instead, he sends the same coins to a merchant for some goods or services.
3. Once the merchant accepts the payment and irreversibly provides the service, the attacker broadcasts his block; the transaction that sends the coins to himself, included in this block, will override the unconfirmed payment to the merchant.

* Recommendation:\
  Wait at least 6 or more confirmations on the network to consider a transaction safe and irreversible.
* Reference:\
  [What is a Finney Hack or Finney Attack?](https://academy.bit2me.com/en/que-es-un-hackeo-finney-ataque-finney/)

### Vector76 Attack

* Severity: High
* Consensus affected: PoW
* Description:\
  Also known as a **one-confirmation attack**. Is a combination of Race attack and Finney attack. In this case, a malicious miner creates two nodes, one is connected only to the exchange node, and the other is connected to well-connected peers in the blockchain network. With this, the miner creates two transactions, one with a high value and one with a low value. Then, the attacker premines and withholds a block with the high-value transaction from an exchange service. After a block announcement, the attacker quickly sends the premined block directly to the exchange service. It along with some miners will consider the premined block as the main chain and confirm this transaction. Thus, this attack exploits the fact that one part of the network sees the transaction the attacker has included into a block while the other part of the network doesn’t see this transaction. After the exchange service confirms the high-value transaction, the attacker sends the low-value transaction to the main network, which finally rejects the high-value transaction. As a result, the attacker’s account is credited the amount of the high-value transaction. Though there’s a high chance for success with this type of attack, it’s not common because it requires a hosted e-wallet that accepts the payment after one confirmation and a node with an incoming transaction.
* Recommendation:\
  Wait at least 6 or more confirmations on the network to consider a transaction safe and irreversible.

### Alternative Historical Attack

* Severity: High
* Consensus affected: PoW / PoS / DPoS
* Description:\
  Also known as **blockchain reorganization attack**. Chain reorgs more often occur naturally as a result of network latency, and “re-organizing” the blockchain is a built-in feature of Bitcoin and similar protocols, designed to keep everyone on the right track. When honest nodes restore order to the blockchain, reorgs pass unnoticed by the public. The routine and naturally occurring reorgs usually nullify (or “orphan”) just one or two invalid blocks.\
  In simple words, a “reorg attack” is a deliberate attempt to rewrite history by creating an alternate legitimate chain of transactions (i.e. the chain with the most proof-of-work). It’s usually done by mining an alternate chain in secret, then broadcasting the results once that chain is longer than the legitimate one. If the motive is profit, the alternate chain would contain double-spend attempts of some kind. Even if an attack of this kind is detected and rectified by honest miners, it can cause havoc and disruption.
* Recommendation:\
  In a blog post, Vitalik Buterin introduces a concept he calls “weak subjectivity” where nodes weigh blocks that were seen earlier higher than those seen later when selecting the most work chain in the case of a potential reorg. The intention is to punish miners who delay submitting their blocks to the network by requiring them to produce a much higher total work chain than under traditional Nakamoto consensus before nodes will reorg.
* References:
  * [Chain Reorganisation](https://learnmeabitcoin.com/technical/chain-reorganisation)
  * [What is chain reorganization in blockchain technology?](https://cointelegraph.com/explained/what-is-chain-reorganization-in-blockchain-technology)
  * [Blockchain attacks and reorgs: Experiences from the past](https://coingeek.com/blockchain-attacks-and-reorgs-experiences-from-the-past/)
  * [An Empirical Analysis of Chain Reorganizations and Double-Spend Attacks on Proof-of-Work Cryptocurrencies](https://allquantor.at/blockchainbib/pdf/lovejoy2020empirical.pdf)

### 51% Attack

* Severity: High
* Consensus affected: PoW / PoS / DPoS
* Description:\
  Also known as **majority attack**. In PoW systems, the entity which controls the majority of the hashing power at a specific timeframe can have complete control over the blockchain, for instance, they can fork the main chain and start mining on their branch. Slowly and steadily, the attackers will be able to outpace the main chain and have their branch take its place.\
  Since in PoW protocols block generation is probabilistic, there are many chances to have conflicting branches, which diminish as we move past the 51% barrier. Therefore, the adversary will have the main chain, but branch reversions will often happen at that point.\
  In PoS protocols this attack is still viable but with a slightly different impact. It is possible for one validator or a coordinated set of validators to own more than 34% (for BFT PoS) of that blockchain’s stake. In this case, a majority attack can impact the blockchain by performing finality reversion, where an already finalized block is being challenged by finalizing another competing block, causing Liveness Denial or Censorship.
* Recommendation:\
  Once a blockchain grows large enough, the likelihood of a single person or group obtaining enough computing power to overwhelm all the other participants rapidly drops to very low levels.
* References:
  * [Understanding a 51% Attack on the Blockchain](https://www.section.io/engineering-education/understanding-the-51-attack-on-blockchain/#ways-to-prevent-a-51-attack)
  * [What Is a 51% Attack?](https://academy.binance.com/en/articles/what-is-a-51-percent-attack)

### Stake Grinding Attack

* Severity: High
* Consensus affected: PoS / DPoS
* Description:\
  Also known as **precomputation attack**.\
  Is a class of attack that afffects PoS protocols where a validator performs some computation or takes some other step to try to bias the randomness in their own favor. For example:\


1. In Peercoin, a validator could "grind" through many combinations of parameters and find favorable parameters that would increase the probability of their coins generating a valid block.
2. In one now-defunct implementation, the randomness for block N+1 was dependent on the signature of block N. This allowed a validator to repeatedly produce new signatures until they found one that allowed them to get the next block, thereby seizing control of the system forever.
3. In NXT, the randomness for block N+1 is dependent on the validator that creates block N. This allows a validator to manipulate the randomness by simply skipping an opportunity to create a block. This carries an opportunity cost equal to the block reward, but sometimes the new random seed would give the validator an above-average number of blocks over the next few dozen blocks. See here and here for a more detailed analysis.

* Recommendation:\
  (1) and (2) are easy to solve; the general approach is to require validators to deposit their coins well in advance, and not to use information that can be easily manipulated as source data for the randomness. There are several main strategies for solving problems like (3). The first is to use schemes based on [secret sharing](https://en.wikipedia.org/wiki/Secret\_sharing) or [deterministic threshold signatures](https://eprint.iacr.org/2002/081.pdf) and have validators collaboratively generate the random value. These schemes are robust against all manipulation unless a majority of validators collude (in some cases though, depending on the implementation, between 33-50% of validators can interfere in the operation, leading to the protocol having a 67% liveness assumption).\
  The second is to use cryptoeconomic schemes where validators commit to information (i.e. publish sha3(x)) well in advance, and then must publish x in the block; x is then added into the randomness pool.
* Reference:\
  [Bribery and stake grinding attacks](https://web.stanford.edu/class/archive/ee/ee374/ee374.1206/downloads/l18\_notes.pdf)

### Coin Age Accumulation Attack

* Severity: High
* Consensus: PoS / DPoS
* Description:\
  In the early version of Peercoin protocol, the user’s stake would accumulate more weight the more time it was staked without having any time restrictions. Given enough time, an attacker would have accumulated enormous amounts of stake in the system which would allow them to take over the network. The coin age mechanism worked as an amplification technique to the stake of its validators.
* Recommendation:\
  As a mitigation technique, the coin age mechanism was capped at a certain amount of time or was completely removed.
* Reference:\
  [Robust Proof of Stake: A New Consensus Protocol for Sustainable Blockchain Systems](https://www.mdpi.com/2071-1050/12/7/2824/pdf)

### Nothing-at-Stake Attack

* Severity: Medium
* Consensus affected: PoS / DPoS
* Description:\
  ![Nothing-at-stake-attack](../images/nothing-at-stake-attack.png)\
  The “nothing-at-stake” problem refers to the fact that block creators on generic proof-of-stake protocols do not have anything at stake when the network forks. This is one of the primary criticisms of proof-of-stake consensus mechanisms. When a proof-of-work based network, like Bitcoin, forks, every active miner creating blocks on the network must _choose_ which fork to mine on. A mining unit cannot create blocks on both forks at the same. The scarcity of the hash power is what forces (in theory) the fork to resolve. When a proof-of-stake protocol forks though, the scarce resource for block production is not hash power but token stake, and, in a fork, an equivalent amount of stake is created on the new network. This means a block creator can start creating blocks on both networks immediately and they do not have to choose (the computation cost of creating a block in a POS system is generally trivial because miners are not competing with each other based on computation). This makes it difficult, if not impossible, for a simple POS system to resolve forks; moreover, it can make double-spend attacks much cheaper in the case of fork resolution.
* Recommendation:\
  [Casper explanations](https://blog.ethereum.org/2015/08/01/introducing-casper-friendly-ghost/) outlined methods of defense. The original [Cosmos whitepaper](https://github.com/cosmos/cosmos/blob/master/WHITEPAPER.md) also discussed several defenses. Most solutions center on punishing block creators if it can be proven that they are creating blocks on another network.
* Reference:
  * [Nothing-at-Stake Problem](https://smithandcrown.com/glossary/nothing-stake-problem/)
  * [Robust Proof of Stake: A New Consensus Protocol for Sustainable Blockchain Systems](https://www.mdpi.com/2071-1050/12/7/2824/pdf)

### Block Double Production

* Severity: High
* Consensus affected: PoW / PoS / DPoS
* Description:\
  Block Double Production is an attack on a blockchain network in which an attacker uses their computational power to mine or validate multiple valid blocks at the same time. This can lead to a fork in the blockchain, with two different versions of the same block being created. The attacker can then choose which version of the block to broadcast to the network, effectively allowing them to double-spend coins or reverse transactions. This could also be a precursor to a long-range attack or a short-range attack.
* Recommendation:\
  Preventing Block Double Production attack is done by implementing a mechanism that can detect this kind of attack and then responding to it in a way that will minimize the damage that it causes. For example, a blockchain network might have a mechanism in place to automatically switch to a different version of the blockchain if it detects that a fork has occurred.
