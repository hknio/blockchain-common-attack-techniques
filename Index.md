# Blockchain Common Attack Techniques
Blockchain technology has revolutionized the way we think about data security, but it is not immune to attacks. In these documents, we will explore the most common attack techniques used against blockchain networks, including 51% attacks, double-spending, Sybil attacks, and more. We will also discuss the potential consequences of these attacks and provide recommendations for how to protect against them. This document is intended for blockchain security researchers, developers, and users who want to gain a deeper understanding of the security risks associated with blockchain technology

## Table of Contents
*   [Protocol Layer](./Protocol-Layer.md#protocol-layer)
    *   [Consensus](./Protocol-Layer.md#consensus)
        *   [Long Range Attack](./Protocol-Layer.md#long-range-attack)
        *   [Race Attack](./Protocol-Layer.md#race-attack)
        *   [Liveness Denial](./Protocol-Layer.md#liveness-denial)
        *   [Finney Attack](./Protocol-Layer.md#finney-attack)
        *   [Vector76 Attack](./Protocol-Layer.md#vector76-attack)
        *   [Alternative Historical Attack](./Protocol-Layer.md#alternative-historical-attack)
        *   [51% Attack](./Protocol-Layer.md#51-attack)
        *   [Stake Grinding Attack](./Protocol-Layer.md#stake-grinding-attack)
        *   [Coin Age Accumulation Attack](./Protocol-Layer.md#coin-age-accumulation-attack)
        *   [Nothing-at-Stake Attack](./Protocol-Layer.md#nothing-at-stake-attack)
        *   [Block Double Production](./Protocol-Layer.md#block-double-production)
*   [Network Layer](./Network-Layer.md#network-layer)
    *   [P2P](./Network-Layer.md#p2p)
        *   [Sybil Attack](./Network-Layer.md#sybil-attack)
        *   [Eclipse Attack](./Network-Layer.md#eclipse-attack)
        *   [Eavesdropping Attack](./Network-Layer.md#eavesdropping-attack)
        *   [Denial of Service Attack](./Network-Layer.md#denial-of-service-attack)
        *   [BGP Hijack Attack](./Network-Layer.md#bgp-hijack-attack)
        *   [Alien Attack](./Network-Layer.md#alien-attack)
        *   [Timejacking](./Network-Layer.md#timejacking)
*   [Data Layer](./Data-Layer.md#data-layer)
    *   [Encryption](./Data-Layer.md#encryption)
        *   [Cryptographic Attacks](./Data-Layer.md#cryptographic-attacks)
        *   [Private Key Prediction](./Data-Layer.md#private-key-prediction)
        *   [Length Extension Attack](./Data-Layer.md#length-extension-attack)
        *   [Hash collision attack](./Data-Layer.md#hash-collision-attack)
    *   [Transactions](./Data-Layer.md#transactions)
        *   [Transaction Replay Attack](./Data-Layer.md#transaction-replay-attack)
        *   [Transaction Malleability Attack](./Data-Layer.md#transaction-malleability-attack)
        *   [Time-Locked Transaction Attack](./Data-Layer.md#time-locked-transaction-attack)
        *   [False Top-Up Attack](./Data-Layer.md#false-top-up-attack)
        *   [Rug Pull Attack](./Data-Layer.md#rug-pull-attack)
*   [Infrastructure Layer](./Infrastructure-Layer.md#infrastructure-layer)
    *   [RPC](./Infrastructure-Layer.md#rpc)
        *   [Information Leakage](./Infrastructure-Layer.md#information-leakage)
        *   [Denial of Service Attack](./Infrastructure-Layer.md#denial-of-service-attack-1)
        *   [Cross-Domain Phishing Attack](./Infrastructure-Layer.md#cross-domain-phishing-attack)
        *   [Man-in-the-middle Attack](./Infrastructure-Layer.md#man-in-the-middle-attack)
        *   [Injection Attack](./Infrastructure-Layer.md#injection-attack)
    *   [Mining Pools](./Infrastructure-Layer.md#mining-pools)
        *   [Selfish Mining](./Infrastructure-Layer.md#selfish-mining)
        *   [Bribery Attack](./Infrastructure-Layer.md#bribery-attack)
        *   [Block Withholding Attack](./Infrastructure-Layer.md#block-withholding-attack)
        *   [Pool Hopping Attack](./Infrastructure-Layer.md#pool-hopping-attack)
        *   [Block Discarding Attack](./Infrastructure-Layer.md#block-discarding-attack)
        *   [Fork After Withholding Attack](./Infrastructure-Layer.md#fork-after-withholding-attack)
        *   [Uncle-Block Attack](./Infrastructure-Layer.md#uncle-block-attack)