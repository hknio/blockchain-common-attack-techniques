# 🗂 Blockchain Common Attack Techniques

Blockchain technology has revolutionized the way we think about data security, but it is not immune to attacks. In these documents, we will explore the most common attack techniques used against blockchain networks, including 51% attacks, double-spending, Sybil attacks, and more. We will also discuss the potential consequences of these attacks and provide recommendations for how to protect against them. This document is intended for blockchain security researchers, developers, and users who want to gain a deeper understanding of the security risks associated with blockchain technology

## Table of Contents

* [Protocol Layer](index/protocol-layer.md#protocol-layer)
  * [Consensus](index/protocol-layer.md#consensus)
    * [Long Range Attack](index/protocol-layer.md#long-range-attack)
    * [Race Attack](index/protocol-layer.md#race-attack)
    * [Liveness Denial](index/protocol-layer.md#liveness-denial)
    * [Finney Attack](index/protocol-layer.md#finney-attack)
    * [Vector76 Attack](index/protocol-layer.md#vector76-attack)
    * [Alternative Historical Attack](index/protocol-layer.md#alternative-historical-attack)
    * [51% Attack](index/protocol-layer.md#51-attack)
    * [Stake Grinding Attack](index/protocol-layer.md#stake-grinding-attack)
    * [Coin Age Accumulation Attack](index/protocol-layer.md#coin-age-accumulation-attack)
    * [Nothing-at-Stake Attack](index/protocol-layer.md#nothing-at-stake-attack)
    * [Block Double Production](index/protocol-layer.md#block-double-production)
* [Network Layer](index/network-layer.md#network-layer)
  * [P2P](index/network-layer.md#p2p)
    * [Sybil Attack](index/network-layer.md#sybil-attack)
    * [Eclipse Attack](index/network-layer.md#eclipse-attack)
    * [Eavesdropping Attack](index/network-layer.md#eavesdropping-attack)
    * [Denial of Service Attack](index/network-layer.md#denial-of-service-attack)
    * [BGP Hijack Attack](index/network-layer.md#bgp-hijack-attack)
    * [Alien Attack](index/network-layer.md#alien-attack)
    * [Timejacking](index/network-layer.md#timejacking)
* [Data Layer](index/data-layer.md#data-layer)
  * [Encryption](index/data-layer.md#encryption)
    * [Cryptographic Attacks](index/data-layer.md#cryptographic-attacks)
    * [Private Key Prediction](index/data-layer.md#private-key-prediction)
    * [Length Extension Attack](index/data-layer.md#length-extension-attack)
    * [Hash collision attack](index/data-layer.md#hash-collision-attack)
  * [Transactions](index/data-layer.md#transactions)
    * [Transaction Replay Attack](index/data-layer.md#transaction-replay-attack)
    * [Transaction Malleability Attack](index/data-layer.md#transaction-malleability-attack)
    * [Time-Locked Transaction Attack](index/data-layer.md#time-locked-transaction-attack)
    * [False Top-Up Attack](index/data-layer.md#false-top-up-attack)
    * [Rug Pull Attack](index/data-layer.md#rug-pull-attack)
* [Infrastructure Layer](index/infrastructure-layer.md#infrastructure-layer)
  * [RPC](index/infrastructure-layer.md#rpc)
    * [Information Leakage](index/infrastructure-layer.md#information-leakage)
    * [Denial of Service Attack](index/infrastructure-layer.md#denial-of-service-attack-1)
    * [Cross-Domain Phishing Attack](index/infrastructure-layer.md#cross-domain-phishing-attack)
    * [Man-in-the-middle Attack](index/infrastructure-layer.md#man-in-the-middle-attack)
    * [Injection Attack](index/infrastructure-layer.md#injection-attack)
  * [Mining Pools](index/infrastructure-layer.md#mining-pools)
    * [Selfish Mining](index/infrastructure-layer.md#selfish-mining)
    * [Bribery Attack](index/infrastructure-layer.md#bribery-attack)
    * [Block Withholding Attack](index/infrastructure-layer.md#block-withholding-attack)
    * [Pool Hopping Attack](index/infrastructure-layer.md#pool-hopping-attack)
    * [Block Discarding Attack](index/infrastructure-layer.md#block-discarding-attack)
    * [Fork After Withholding Attack](index/infrastructure-layer.md#fork-after-withholding-attack)
    * [Uncle-Block Attack](index/infrastructure-layer.md#uncle-block-attack)