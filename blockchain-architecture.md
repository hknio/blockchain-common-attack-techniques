# 🌍 Blockchain Architecture

Table of Contents

* [Application Layer](blockchain-architecture.md#application-layer)
* [Services and Optional Components](blockchain-architecture.md#services-and-optional-components)
* [Protocol Layer](blockchain-architecture.md#protocol-layer)
* [Network Layer](blockchain-architecture.md#network-layer)
* [Data Layer](blockchain-architecture.md#data-layer)
* [Infrastructure Layer](blockchain-architecture.md#infrastructure-layer)

## Application Layer

Serves as the interface through which users interact with blockchain services. Combines business logic with customer interactions through dApps and browser-based interfaces.

* **Browser dApps**\
  These are decentralized applications accessible through a web browser. They interact with the blockchain to provide users with various services like games, financial services, decentralized exchanges, etc.
* **Decentralized Applications** (dApps)\
  These are applications that run on a P2P network of computers rather than a single computer.

## Services and Optional Components

Provides support for the application operations and connects the blockchain with other technologies and platforms. Facilitates integration of external data, off-chain computing, digital assets, and interoperability with other blockchains.

* **Smart Contracts**\
  It contains the business rules that govern the transactional interactions within the network.
* **Governance/DAOs**\
  DAOs, or Decentralized Autonomous Organizations, are member-owned communities without a centralized authority. They make decisions using smart contracts and governance tokens.
* **Oracles**\
  Oracles provide real-world data to the blockchain and smart contracts. They act as a bridge between off-chain and on-chain data.
* **Wallets**\
  Wallets are tools that allow users to interact with a blockchain network. They can store, send, and receive digital assets.
* **Digital Assets (Tokens)**\
  These are assets that exist in the form of electronic data, such as cryptocurrencies, tokens, or digital files.
* **Data Feeds**\
  These are live streams of data that are used by smart contracts to make decisions or perform actions.
* **Off-Chain Computing**\
  This refers to computations that occur outside of the blockchain (off-chain) to reduce the load on the blockchain and increase scalability.
* **Blockchain Monitor**\
  Tools or platforms that provide insights into blockchain activities, including transaction histories, network health, and other relevant information.
* **Interoperability Solutions**\
  These enable different blockchain systems to communicate and interact, allowing for the exchange of information, transactions, and data between various blockchains.
* **Identity and Access Management (IAM)**\
  These are blockchain systems that manage and secure digital identities, controlling user authentication and authorization to secure transactions and ensure access control.
* **Blockchain APIs**\
  These provide a means for external software to interact with the blockchain.
* **Layer-2 Solutions**\
  These are scaling solutions that handle transactions off the main blockchain to increase transaction speed and decrease costs. Examples are Lightning Network for Bitcoin and Plasma, Optimistic Rollups, Zk-rollups for Ethereum.

## Protocol Layer

Defines the rules that govern blockchain operation. This includes consensus algorithms, side chains, propagation protocol, and the execution environment for smart contracts, and mechanisms for managing computational costs and enhancing privacy.

* **Consensus**\
  The method by which blockchain networks agree on the validity of transactions. Examples include Proof of Work (PoW), Proof of Stake (PoS), and others like DAG, PoA, PoE, BFT, PoL, PoET, etc.
* **Side Chains**\
  These are separate blockchain networks that run in parallel to the main blockchain, allowing for more scalability and testing of new features.
* **Propagation Protocol**\
  Rules about how information is spread across the blockchain network.
* **Virtual Machine (VM)**\
  A VM, such as the Ethereum Virtual Machine (EVM), serves as the runtime environment for smart contracts, processing transactions and maintaining the blockchain's state.
* **Gas Systems**\
  These mechanisms meter and charge for computational activities on blockchains, including executing smart contracts and making transactions. They play a crucial role in preventing network abuse by attaching a cost to each operation.
* **Privacy Enhancements**\
  Some blockchains use additional technologies to enhance privacy. For example, zk-SNARKs in Zcash or ring signatures in Monero.

## Network Layer

Implements the P2P network architecture that underlies blockchain operation. Determines how data is packetized, addressed, transmitted, routed, and received across the network.

* **Peer-to-Peer (P2P)**\
  This is a distributed network architecture where all participants (peers) have equal privileges and responsibilities. P2P networks enable direct data sharing between peers without the need for a central server or authority, promoting decentralization and resilience.
* **Communication Mechanisms**\
  These are the methods used by nodes to share data and maintain the blockchain.
* **Verification Mechanism**\
  This mechanism checks the validity of new transactions and blocks.
* **Recursive Length Prefix (RPLx)**\
  Recursive Length Prefix (RLP) is used by Ethereum to encode nested arrays of binary data.
* **Block Delivery**\
  The process of sharing new blocks with all nodes in the network.
* **Trusted Execution Environment (TEE)**\
  A secure area of a main processor that ensures code and data loaded inside are protected with respect to confidentiality and integrity.
* **Remote Procedure Call (RPC)**\
  It is a protocol that one program can use to request a service from a program located on another computer on a network without having to understand the network's details.

## Data Layer

Manages the blockchain data structure and its physical storage. Handles transactions, data blocks, encryption, validation (via digital signatures), and temporary storage (via mempool) before transactions are added to a block.

* **Digital Signatures**\
  These provide a layer of validation and security, ensuring the authenticity and integrity of a message, software, or digital document.
* **Hash**\
  A hash function takes an input and returns a fixed-size string of bytes. It is used extensively for a variety of purposes, such as transaction verification.
* **Merkle Tree**\
  Merkle Trees are used in blockchains to efficiently summarize and verify the integrity of large sets of data.
* **Transactions**\
  These are the actions executed on the blockchain, such as sending cryptocurrency from one account to another.
* **Data Blocks**\
  Blocks contain batches of validated transactions that are hashed and encoded into a Merkle tree.
* **Asymmetric Encryption**\
  This form of encryption uses two keys: a public key for encryption and a private key for decryption. It's used in blockchain for securing transactions and creating digital signatures.
* **Storage**\
  This refers to the place where all confirmed transactions are permanently recorded. It's usually in the form of a distributed ledger, replicated across all nodes in the network.
* **Memory Pool (Mempool)**\
  This is a place where transactions wait to be confirmed by the blockchain network's miners. It acts as a sort of "waiting room" for transactions before they're added to a block.

## Infrastructure Layer

Covers the underlying hardware and software infrastructure required to run the blockchain. Includes network management, blockchain nodes, virtualization for optimizing resource usage, and mining for transaction verification and new token release.

* **Mining**\
  This is the process by which transactions are verified and added to the public ledger. It's also the means through which new cryptocurrency tokens are released.
* **Network**\
  This refers to the interconnected system of nodes that maintain and update the blockchain.
* **Nodes**\
  Nodes are computers that connect to the blockchain network and have a copy of the blockchain.
* **Virtualization**\
  This refers to the creation of virtual versions of physical computing resources. For blockchains, it allows running multiple nodes on a single server or operating the entire network in a cloud-based environment, optimizing resource usage and increasing scalability.
