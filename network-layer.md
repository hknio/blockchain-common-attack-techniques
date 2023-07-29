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
  \
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
*   Description:\
    An eavesdropping attack refers to a passive intrusion where an unauthorized individual monitors network traffic. The attacker is essentially "listening in" on network communications, collecting sensitive data like node identification numbers, routing updates, or application-specific information. This gleaned information can be exploited further to compromise nodes, disrupt network routing, or deteriorate application performance.\


    **Impact**: Although the attack itself is passive, the potential aftermath can be quite harmful. It could lead to a breach of privacy, unauthorized access to nodes, manipulation of network routes, and degradation in the performance of applications running on the network. In some cases, it might even pave the way for more severe attacks.
*   Recommendation:

    To mitigate the risks of an eavesdropping attack, the following measures can be taken:

    1. **Encryption**: Implement secure encryption protocols like Transport Layer Security (TLS) or Secure Sockets Layer (SSL) to encrypt communications within the network. Encryption makes intercepted data unreadable and useless to eavesdroppers.
    2. **Secure Protocols**: Use secure versions of network protocols, like HTTPS instead of HTTP, to ensure the safety of data transmission.
* Reference:\
  [The RLPx Transport Protocol](https://github.com/ethereum/devp2p/blob/master/rlpx.md)

### Denial of Service Attack

* Severity: Medium
* Description:\
  A Denial of Service (DoS) attack is a type of attack in which an attacker aims to disrupt the normal functioning of a network by overwhelming it with a large number of requests or traffic. In a blockchain network, a DoS attack can take various forms, such as:

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
  \
  Ethereum alien attack means that Ethereum's similar chain (specifically, the public chain using the Ethereum P2P discv4 node discovery protocol, including Ethereum and Ether Classic) cannot distinguish whether the nodes belong to the same one because they use a compatible handshake protocol. The chain causes the address pools to pollute each other, and the communication performance of the nodes decreases, eventually causing the node to block.
* Recommendation:\
  Add network identification to P2P connection protocol, such as ChainID in Ethereum, and Magic in Bitcoin.
* Reference:\
  [The public chain of conflict! Alien Attack Vulnerability from P2P Protocol](https://blocking.net/1999/the-public-chain-of-conflict-alien-attack-vulnerability-from-p2p-protocol/)

### Timejacking

* Severity: High
* Description:\
  Timejacking is a type of attack that exploits the timestamp handling of nodes in a blockchain network, particularly prevalent in Bitcoin. In a timejacking attack, a malicious actor manipulates the network time counter of a node, pushing it to accept an illegitimate blockchain. The attacker achieves this by adding numerous deceptive peers to the network that propagate incorrect timestamps, causing a skewed network time.\
  \
  **Impact**: This manipulation can disrupt the consensus mechanism, leading to potential double-spending attacks, and can compromise the integrity of the network by causing the node to accept an alternative, attacker-controlled blockchain.
*   Recommendation:

    To mitigate timejacking attacks, implementing safeguards on the acceptance of time updates is critical. This could be done by:

    1. **Restricting Acceptance Time Ranges**: Limiting the difference between the network time and the system time of the node can help to ensure the node isn't easily swayed by incorrect timestamps.
    2. **Using System Time**: Relying more heavily on the node's system time, instead of the network time derived from peers, can protect against manipulation.
    3. **Peer Management**: Implementing robust policies for peer acceptance and management can help to filter out malicious or suspicious nodes that provide incorrect timestamps.

### Network Partitioning Attack

* Severity: High
* Description:\
  A network partitioning attack, also known as a Split-Brain or Network Isolation attack, occurs when a blockchain network is divided into separate, isolated subnets due to either malicious actions or unintentional network issues. Nodes in one partition are unable to communicate with those in the other, leading to discrepancies in the ledger's state.\
  \
  Network partitioning can disrupt the consensus mechanism, resulting in different versions of the blockchain in each partition, also known as forks. This can lead to double-spending attacks if the partitions later reconcile. Additionally, it can result in reduced security as the computational power of the network is effectively split.
* Recommendations:

1. **Redundancy and Failover Systems**: Set up redundant network connections and failover systems to maintain network communication in case of failures.
2. **Diversification of Nodes**: Diversify node deployment across different regions and ISPs to reduce the risk of simultaneous failures.
3. **Peer Discovery and Network Reconnection Policies**: Implement robust peer discovery and network reconnection policies in the nodes to enable them to discover and reconnect to other nodes in the network effectively when partitions are resolved.
4. **Use Gossip Protocols**: Use robust gossip protocols to ensure data propagation across all nodes, reducing the likelihood and impact of partitions.
5. **Consider Byzantine Fault Tolerant Consensus Mechanisms**: These mechanisms are designed to tolerate a certain degree of faulty or malicious nodes and may help in managing the effects of a network partition.

## RPC

### Information Leakage

* Severity: Low
*   Description:\
    If the interface is inadequately secured, an attacker can exploit it to access confidential information. This can include private keys, transaction data, and other critical data. The threat of [eavesdropping attacks](network-layer.md#eavesdropping-attack) also applies here, where attackers can "listen in" on communications to gather private details.\


    **Impact**: Information leakage can lead to unauthorized transactions, loss of funds, impersonation attacks, or a complete compromise of the blockchain node. This compromises both the integrity and confidentiality of blockchain operations and could lead to significant reputational and financial damage.
*   Recommendation:

    To mitigate the risk, adopt the following security measures:

    1. **Communication Encryption**: Ensure all communications are encrypted using robust protocols like TLS, rendering any intercepted data useless to an attacker.
    2. **Access Control**: Implement strong access control mechanisms, ensuring only trusted and necessary entities have access.

### Denial of Service Attack

* Severity: Medium
*   Description:\
    An attacker overwhelms the system by flooding the RPC interface with a large number of requests. This can render the system unresponsive, thereby denying service to legitimate users.\


    **Impact**: A successful DoS attack can disrupt the normal functioning of the blockchain system, leading to delayed transactions, impaired network performance, and potentially, loss of trust from users.
*   Recommendation:

    To mitigate the risk, implement the following measures:

    1. **Rate Limiting**: Implement a rate-limiting mechanism to control the number of requests a user can send to the RPC interface within a certain timeframe.
    2. **Input Validation**: Ensure all parameters are properly validated to prevent malformed inputs from causing crashes.
    3. **Queue Management**: Limit the size of the memory queue to prevent the system from being overwhelmed by incoming requests.

### Cross-Domain Phishing Attack

* Severity: Low
*   Description:\
    In this deceptive scheme, the attacker tricks the victim into visiting a malicious webpage. Upon loading, this webpage then initiates a cross-domain request, covertly connecting to the RPC port of the victim's cryptocurrency wallet. Subsequently, this unauthorized connection serves as a conduit for the attacker to carry out unauthorized transactions or steal crypto assets.

    \
    **Impact**: If successful, a cross-domain phishing attack can lead to severe consequences including unauthorized transactions, potential loss of crypto assets, compromise of personal account details, and a subsequent loss of trust in the security measures of the platform.
*   Recommendation:

    Implement the following strategies to prevent this type of attack:

    1. **Disable Cross-Domain Access**: Nodes should be configured to disable cross-domain access, effectively barring any unauthorized external connections to the RPC interface.
    2. **Access Control**: Enforce strict access controls and secure configurations for the RPC interface to limit the potential for unauthorized access and data breaches.

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
