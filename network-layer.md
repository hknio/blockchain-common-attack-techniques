---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 📦 Network Layer Attacks

## Table of Contents

* [P2P](network-layer.md#p2p)
  * [Sybil Attack](network-layer.md#sybil-attack)
  * [Eclipse Attack](network-layer.md#eclipse-attack)
  * [Eavesdropping Attack](network-layer.md#eavesdropping-attack)
  * [Denial of Service Attack](network-layer.md#denial-of-service-attack)
  * [BGP Hijack Attack](network-layer.md#bgp-hijack-attack)
  * [Alien Attack](network-layer.md#alien-attack)
  * [Timejacking](network-layer.md#timejacking)
* [RPC](network-layer.md#rpc)
  * [Information Leakage ](network-layer.md#information-leakage)
  * [Denial of Service Attack ](network-layer.md#denial-of-service-attack-1)
  * [Cross-Domain Phishing Attack ](network-layer.md#cross-domain-phishing-attack)
  * [Man-in-the-middle Attack ](network-layer.md#man-in-the-middle-attack)
  * [Injection Attack](network-layer.md#injection-attack)

## P2P

### Sybil Attack

* Severity: High
* Description:\
  An attacker creates multiple fake identities, or "Sybils," in order to gain control over a significant portion of the network's resources or influence the outcome of consensus decisions. The attacker can then use this control to disrupt the network's operations or steal resources from legitimate users.\
  A Sybil attack can take the form of creating multiple fake nodes or "Sybil nodes" that the attacker controls. The attacker can then use these nodes to manipulate the network's consensus process, such as by controlling more than half of the network's computational power in a proof-of-work consensus mechanism or by controlling a large number of votes in a proof-of-stake mechanism.
* Recommendations:
  * Sybil attack prevention is done by creating a mechanism that can reliably identify the true identities of network participants, and then using this information to limit the number of resources that any one participant can control. For example, a blockchain network might use a reputation-based system to assign each node a score based on its past behavior, and then use this score to limit the amount of computational power that each node can use.\\
  * Using "proof of identity" can be used to prevent Sybil attacks, which requires users to prove their identity through a trusted third party or a government-issued ID.\\
  * Another solution can be that each node monitors the behavior of other nodes and checks for the nodes which are forwarding the blocks of only one particular user. Such nodes are quickly identified, blacklisted and notified to other nodes, and thus the Sybil attack can be restricted.
* Reference:\
  [Preventing Sybil Attack in Blockchain using Distributed Behavior Monitoring of Miners](https://ieeexplore.ieee.org/document/8944507)

### Eclipse Attack

* Severity: High
* Description:\
  An attacker isolates a specific node from the rest of the network by controlling the majority of the nodes that the targeted node is connected to. This allows the attacker to control the flow of information to and from the targeted node, allowing them to disrupt the network's operations or steal resources from the targeted node.
* Recommendations:\
  Nodes can be eclipsed if an attacker has access to sufficient IP addresses. The easiest way to avoid this is for a node to restrict inbound connections and be deliberate about any connections made with other nodes.\
  Other common approaches include:
  * **Random node selection:** By structuring a peer-to-peer network in a way in which each node connects to a randomized set of IP addresses each time it syncs with the network rather than adhering to a repeating, exploitable set of node criteria
  * **Deterministic node selection:** Taking the opposite approach from random node selection, deterministic node selection involves the insertion of specific node IP addresses into their corresponding predetermined fixed slots every time they connect with the network. By fixing the connections of the network’s nodes, an attacker will have a harder time maneuvering malicious nodes through the network and converging around a target, and the repeated insertion of attacker-controlled addresses will not necessarily contribute to the success of an eclipse attack attempt.
  * **Increased node connections:** By increasing the required number of node-to-node connections, a network would be able to increase the likelihood that a node will connect to a legitimate user. However, there are node constraints and bandwidth constraints which limit the extent to which a network can increase the number of node connections without sacrificing performance, limiting the efficacy of this approach as a stand-alone solution to eclipse attacks.
  * **New node restrictions:** By making it more expensive or difficult to create new nodes within a network, the blockchain architect can set a higher bar for malicious actors to flood the network with attacker-controlled nodes. Oftentimes this approach involves limiting the number of nodes per IP address or device, although this defensive measure can be circumvented by an attacker deploying a botnet composed of devices which have their own unique IP addresses.
* Reference:\
  [Eclipse Attacks: Explanations and Preventions](https://www.gemini.com/cryptopedia/eclipse-attacks-defense-bitcoin)

### Eavesdropping Attack

* Severity: Low
* Description:\
  The attacker passively listens to network communications to gain access to private information, such as node identification numbers, routing updates, or application-sensitive data. The attacker can use this private information to compromise nodes in the network, disrupt routing, or degrade application performance.
* Recommendation:\
  Encrypt communications using encryption protocols, such as TLS.
* Reference:\
  [The RLPx Transport Protocol](https://github.com/ethereum/devp2p/blob/master/rlpx.md)

### Denial of Service Attack

* Severity: Medium
* Description:\
  A Denial of Service (DoS) attack is a type of attack in which an attacker aims to disrupt the normal functioning of a network by overwhelming it with a large number of requests or traffic. In a blockchain network, a DoS attack can take various forms, such as:\\

1. Flooding the network with a high number of invalid transactions, making it difficult for legitimate transactions to be processed.
2. Overloading the network with a high number of requests to the nodes, making them unable to keep up with the traffic, and causing them to crash.
3. Attempting to isolate specific nodes from the rest of the network by overwhelming them with a large number of requests.
4. Attempting to overload the consensus mechanism of the network, making it difficult for it to reach a decision.

* Recommendation:\
  Preventing a DoS attack on a blockchain network can be done by using techniques such as rate limiting, which limits the number of requests that a network will accept from a single source, or using a distributed architecture, which makes it more difficult for an attacker to overwhelm a specific node or set of nodes. Additionally, using a decentralized peer discovery mechanism, which allows nodes to find new peers without relying on a central authority, can decrease the chance of a DoS attack.

### BGP Hijack Attack

* Severity: Low
* Description:\
  A BGP (Border Gateway Protocol) hijack attack is a type of cyber-attack that targets the routing infrastructure of the internet. It occurs when an attacker redirects internet traffic meant for a specific network or IP address to a different network or IP address under the attacker's control. In a blockchain network, a BGP hijack attack can be used to disrupt the communication between nodes in the network, preventing them from reaching consensus and leading to a fork in the blockchain.
* Recommendations:
  * Increase the number of nodes in different regions.
  * [SABRE: Protecting Bitcoin against Routing Attacks](https://arxiv.org/abs/1808.06254)
* References:
  * [BGP Hijacking](https://en.wikipedia.org/wiki/BGP\_hijacking)
  * [Hijacking Bitcoin: Routing Attacks on Cryptocurrencies](https://ieeexplore.ieee.org/document/7958588)
  * [KlaySwap crypto users lose funds after BGP hijack](https://medium.com/s2wblog/post-mortem-of-klayswap-incident-through-bgp-hijacking-898f26727d66)
  * [Blockchain meets Internet Routing](https://btc-hijack.ethz.ch/)

### Alien Attack

* Severity: Low
* Description:\
  Alien attack, also known as address pool pollution, refers to an attack method that induces nodes of the same chain to invade and pollute each other. The main reason for the vulnerability is that the same chain system does not identify non-similar nodes in the communication protocol.\
  Ethereum alien attack means that Ethereum's similar chain (specifically, the public chain using the Ethereum P2P discv4 node discovery protocol, including Ethereum and Ether Classic) cannot distinguish whether the nodes belong to the same one because they use a compatible handshake protocol. The chain causes the address pools to pollute each other, and the communication performance of the nodes decreases, eventually causing the node to block.
* Recommendation:\
  Add network identification to P2P connection protocol, such as ChainID in Ethereum, and Magic in Bitcoin.
* Reference:\
  [The public chain of conflict! Alien Attack Vulnerability from P2P Protocol](https://blocking.net/1999/the-public-chain-of-conflict-alien-attack-vulnerability-from-p2p-protocol/)

### Timejacking

* Severity: High
* Description:\
  Timejacking exploits a theoretical vulnerability in Bitcoin timestamp handling. During a timejacking attack, a hacker alters the network time counter of the node and forces the node to accept an alternative blockchain. This can be achieved when a malicious user adds multiple fake peers to the network with inaccurate timestamps.
* Recommendation:\
  A timejacking attack can be prevented by restricting acceptance time ranges or using the node’s system time.

## RPC

### Information Leakage

* Severity: Low
* Description:\
  An attacker can exploit vulnerabilities in the RPC interface to gain access to sensitive information, such as private keys or transaction data. The [Eavesdropping Attack](network-layer.md#eavesdropping-attack) apply to this category as well.
* Recommendation:\
  Encrypt communications using encryption protocols, such as TLS.

### Denial of Service Attack

* Severity: Medium
* Description:\
  An attacker can flood the RPC interface with a large number of requests, overwhelming the system and causing it to become unavailable to legitimate users.
* Recommendation:

1. Prevent malformed parameters from crashing the software.
2. Limit memory queue size.

### Cross-Domain Phishing Attack

* Severity: Low
* Description:\
  The hacker tricks the victim into opening a malicious webpage, connects to the cryptocurrency wallet RPC port through a cross-domain request, and then steals crypto assets.
* Recommendation:\
  Prohibit nodes from enabling cross-domain access.

### Man-in-the-middle Attack

* Severity: Low
* Description:\
  An attacker can intercept and modify requests sent to the RPC interface, potentially altering the intended behavior of the blockchain.
* Recommendations:

1. Use Secure Communication Protocols: It is important to use secure communication protocols such as HTTPS, SSH or SSL/TLS to encrypt the communication between the client and the RPC interface, making it much more difficult for an attacker to intercept and modify requests.
2. Implement Authentication: Implementing authentication mechanisms such as password or token-based authentication, would ensure that only authorized users can access the RPC interface and prevent unauthorized access.
3. Use Firewalls and Network Segmentation: Firewalls can be used to restrict access to the RPC interface to only trusted sources, and network segmentation can be used to isolate the RPC interface from other parts of the network.
4. Input validation: The inputs to the RPC interface should be properly sanitized and validated before processing, to prevent injection attacks.
5. Regularly update software: Keep the software and system up to date with the latest security patches to prevent known vulnerabilities from being exploited.
6. Monitor logs: Regularly monitor the logs of the RPC interface for suspicious activity, and have an incident response plan in place to quickly detect and respond to any security breaches.

### Injection Attack

* Severity: Low
* Description:\
  An attacker can use malformed inputs to inject malicious code into the RPC interface, which can be used to steal sensitive information or disrupt the operation of the blockchain.
* Recommendations:

1. Input validation: The inputs to the RPC interface should be properly sanitized and validated before processing. This can help to prevent injection attacks by ensuring that only valid inputs are accepted and executed.
2. Use prepared statements: Use prepared statements or parameterized queries to separate the data from the code, this can prevent SQL injection.
3. Use an ORM: Object-Relational Mapping (ORM) libraries can provide a layer of abstraction between the code and the database, preventing SQL injection.
4. Use a Web Application Firewall (WAF): A Web Application Firewall (WAF) can be used to detect and block malicious inputs, including injection attacks.
5. Limit permissions: Limit the permissions of the account that the RPC uses to access the database, to prevent an attacker from using the account to execute malicious code.
