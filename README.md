# ⛓ Blockchain Common Attack Techniques

Blockchain technology has revolutionized the way we think about data security, but it is not immune to attacks. In these documents, we will explore the most common attack techniques used against blockchain networks, including 51% attacks, double-spending, Sybil attacks, and more. We will also discuss the potential consequences of these attacks and provide recommendations for how to protect against them. This document is intended for blockchain security researchers, developers, and users who want to gain a deeper understanding of the security risks associated with blockchain technology

## Table of Contents

* [Protocol Layer](protocol-layer.md#protocol-layer)
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
* [Network Layer](network-layer.md#network-layer)
  * [P2P](network-layer.md#p2p)
    * [Sybil Attack](network-layer.md#sybil-attack)
    * [Eclipse Attack](network-layer.md#eclipse-attack)
    * [Eavesdropping Attack](network-layer.md#eavesdropping-attack)
    * [Denial of Service Attack](network-layer.md#denial-of-service-attack)
    * [BGP Hijack Attack](network-layer.md#bgp-hijack-attack)
    * [Alien Attack](network-layer.md#alien-attack)
    * [Timejacking](network-layer.md#timejacking)
    * [Network Partitioning Attack](network-layer.md#network-partitioning-attack)
  * [RPC](network-layer.md#rpc)
    * [Information Leakage ](network-layer.md#information-leakage)
    * [Denial of Service Attack ](network-layer.md#denial-of-service-attack-1)
    * [Cross-Domain Phishing Attack ](network-layer.md#cross-domain-phishing-attack)
    * [Man-in-the-middle Attack ](network-layer.md#man-in-the-middle-attack)
    * [Injection Attack](network-layer.md#injection-attack)
* [Data Layer](data-layer.md#data-layer)
  * [Encryption](data-layer.md#encryption)
    * [Cryptographic Attacks](data-layer.md#cryptographic-attacks)
    * [Private Key Prediction](data-layer.md#private-key-prediction)
    * [Length Extension Attack](data-layer.md#length-extension-attack)
    * [Hash collision attack](data-layer.md#hash-collision-attack)
  * [Transactions](data-layer.md#transactions)
    * [Transaction Replay Attack](data-layer.md#transaction-replay-attack)
    * [Transaction Malleability Attack](data-layer.md#transaction-malleability-attack)
    * [Time-Locked Transaction Attack](data-layer.md#time-locked-transaction-attack)
    * [False Top-Up Attack](data-layer.md#false-top-up-attack)
    * [Rug Pull Attack](data-layer.md#rug-pull-attack)
* [Infrastructure Layer](infrastructure-layer.md#infrastructure-layer)
  * [Mining Pools](infrastructure-layer.md#mining-pools)
    * [Selfish Mining](infrastructure-layer.md#selfish-mining)
    * [Bribery Attack](infrastructure-layer.md#bribery-attack)
    * [Block Withholding Attack](infrastructure-layer.md#block-withholding-attack)
    * [Pool Hopping Attack](infrastructure-layer.md#pool-hopping-attack)
    * [Block Discarding Attack](infrastructure-layer.md#block-discarding-attack)
    * [Fork After Withholding Attack](infrastructure-layer.md#fork-after-withholding-attack)
    * [Uncle-Block Attack](infrastructure-layer.md#uncle-block-attack)
