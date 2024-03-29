# 🛠 Infrastructure Layer Attacks

## Table of Contents

* [Mining Pools](infrastructure-layer.md#mining-pools)
  * [Selfish Mining](infrastructure-layer.md#selfish-mining)
  * [Bribery Attack](infrastructure-layer.md#bribery-attack)
  * [Block Withholding Attack](infrastructure-layer.md#block-withholding-attack)
  * [Pool Hopping Attack](infrastructure-layer.md#pool-hopping-attack)
  * [Block Discarding Attack](infrastructure-layer.md#block-discarding-attack)
  * [Fork After Withholding Attack](infrastructure-layer.md#fork-after-withholding-attack)
  * [Uncle-Block Attack](infrastructure-layer.md#uncle-block-attack)

## Mining Pools

### Selfish Mining

* Severity: High
* Description:\
  In selfish mining attacks the adversary mines blocks in their own fork of the blockchain without publishing them to the network. Once the attacker has computed a desired number of blocks, they are released to the network and aim to revert the main chain to that of the attackers. The purpose of this attack can be twofold; a) disruption of the network by wasting the resources of honest nodes and b) increase the rewards collected by the dishonest nodes.
* Recommendation:\
  The former incentive of the attack affects purely PoW blockchains. A PoS blockchain would not be disrupted by this incentive. The latter incentive affects both protocols and can be mitigated by applying slashing conditions, or by removing violators from their position of power which will cause them to forfeit future rewards.
* Reference:\
  [A Survey on Long-Range Attacks for Proof of Stake Protocols](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8653269)

### Bribery Attack

* Severity: High
* Description:\
  Also referred to as **Short-Range attack** relies on bribing validators or miners to work on specific blocks or forks. By doing that, the attacker can present arbitrary transactions as valid and have dishonest nodes paid to verify them. By paying them an amount equal to or more than the block rewards (in case the block is reverted by the network), it provides an incentive high enough for miners to work on the attacker’s blocks or chain. This case of bribery attacks also known as **P+epsilon attack** states that it is possible to bribe users without having to pay them, as the system will award the bribe to the dishonest nodes by making that branch the main chain. For these cases, the attacker faces a more significant problem as in case the malicious branch is reverted for some reason (attacker cannot continue the bribe, dishonest nodes stop working on that branch) the attacker would have to pay an enormous amount of bribes as the bribes will accumulate for every maliciously minted block. In PoS systems, these kinds of attacks are feasible and can be expanded to the nothing at stake problem.
* Recommendation:\
  In both cases, PoS tackles this issue by either enforcing a slashing condition or by releasing violators from their position.
* Reference:\
  [A Survey on Long-Range Attacks for Proof of Stake Protocols](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=8653269)

### Block Withholding Attack

* Severity: Medium
* Description:\
  The attacker enters a mining pool to assist the pool members in mining blocks, however, the attacker never broadcast any block to decline the estimated revenue of the pool. This attack is often considered a **Sabotage Attack** because nothing is gained by the scoundrel miner but instead aims to cause the mining pool's profitability to decline. This kind of assault will bankrupt a pay-per-share pool if continued for a long enough time.
* Recommendation:\
  Mitigation of a Block Withholding attack is complex because of the random nature of mining, but some methods have been developed such as various cryptographic commitment schemes combined with hash functions. These schemes typically prevent the pool administrator from cheating on the entire pool and make it impossible for miners in the pool to distinguish between partial proof of work and complete proof of work.

### Pool Hopping Attack

* Severity: Low
* Description:\
  This attack is based on the appeal rate. The attacker mines if the rate is high. Otherwise, the attacker leaves the pool. In order to understand how many shares have been submitted and how many blocks have been identified, the attacker uses details about the amount of submitted shares in the target mining pool. Using this data, the attacker stops mining in the target pool and contributes elsewhere. The core principle behind this attack is to achieve full profits, the attacker prefers separate pools to mine.
* Recommendation:\
  Slush's method, which scores shares based on the time they are submitted, was designed to combat pool-hopping, but is only an incomplete solution. SMPPS which strives to converge to the full value of each share in the long run can only be hopped to minimize the time until being paid in full, not to increase the expected reward. Modern methods make sure that the reward per share depends only on the future of the pool, not its past. This way, without being able to divine future random events, any time is as good as any other to mine, so there can never be any gain or loss from hopping (with the exception of block-withholding attacks). The most popular such methods are PPS, PPLNS and DGM.
* Reference:\
  [A new approach for Bitcoin pool-hopping detection](https://www.sciencedirect.com/science/article/abs/pii/S1389128621006009) [Smart Contract-Based Pool Hopping Attack Prevention for Blockchain Networks](https://www.mdpi.com/2073-8994/11/7/941)

### Block Discarding Attack

* Severity: Low
* Description:\
  In this attack, the attackers must possess a sufficient number of network connections relative to the honest nodes and conquer several slave nodes to improve their network dominance. If the attackers are aware of recently mined blocks, they automatically publish their own block, which must be quicker than the rest of the network thus, when a node publishes a block, the attackers will instantly spread their own blocks to discard the blocks of honest nodes.
* Recommendation:\
  As in 51% attack, the best way to prevent this attack is to have a large number of nodes in the network, making it harder to take the network dominance to any attacker.
* Reference:\
  [Theoretical Bitcoin Attacks with less than Half of the Computational Power](https://eprint.iacr.org/2013/868.pdf)

### Fork After Withholding Attack

* Severity: High
* Description:\
  The Fork-After-Withholding (FAW) attack revenue is equivalent to or greater than the Block Withholding (BWH) attack and the attack is four times more fruitful than the BWH attack. The Selfish mining attack and the BWH attack are merged in this attack. There are two forms of this attack:

1. In the Single-pool FAW attack, the attacker joins the target mining pool and executes the attack against it.
2. In the Multipool FAW attack by expanding the attack against many pools, the attacker intends to maximize his or her revenue.

* Recommendation:\
  Mining pool managers could provide a beacon value that is updated very frequently (i.e., every couple of seconds) and only give points for PPoWs that include a recent beacon value.
* Reference:\
  [Be Selfish and Avoid Dilemmas: Fork After Withholding (FAW) Aacks on Bitcoin](https://arxiv.org/pdf/1708.09790.pdf)

### Uncle-Block Attack

* Severity: Medium
* Description:\
  This attack is an extension of Block Withholding Attack and Fork After Withholding Attack that applies also to uncle nodes following the same kind of attack.
* Recommendation:\
  Same countermeasures of Block Withholding Attack and FAW can be applied to this attack. An extended analysis of them is presented in the reference.
* Reference:\
  [Uncle-Block Attack: Blockchain Mining Threat Beyond Block Withholding for Rational and Uncooperative Miners](https://academics.uccs.edu/\~schang2/docs/UBA\_ACNS19.pdf)
