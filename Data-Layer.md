# Data Layer Attacks

Table of Contents
- [Data Layer Attacks](#data-layer-attacks)
  - [Encryption](#encryption)
    - [Cryptographic Attacks](#cryptographic-attacks)
    - [Private Key Prediction](#private-key-prediction)
    - [Length Extension Attack](#length-extension-attack)
    - [Hash collision attack](#hash-collision-attack)
  - [Transactions](#transactions)
    - [Transaction Replay Attack](#transaction-replay-attack)
    - [Transaction Malleability Attack](#transaction-malleability-attack)
    - [Time-Locked Transaction Attack](#time-locked-transaction-attack)
    - [False Top-Up Attack](#false-top-up-attack)
    - [Rug Pull Attack](#rug-pull-attack)

## Encryption
### Cryptographic Attacks
- Severity: High
- Description:  
  A cryptographic attack is a method for circumventing the security of a cryptographic system by finding a weakness in a code, cipher, cryptographic protocol or key management scheme. This process is also called "cryptanalysis".<br/>
  Some common attack methods are: Analytic Attack / Implementation Attack / Statistical Attack / Brute Force / Frequency Analysis and the Ciphertext Only Attack / Known Plaintext / Chosen Ciphertext  / Chosen Plaintext / Meet in the Middle / Man in the Middle  / Birthday attack / Replay attack / Collision attack, among many others.
- Recommendation:  
  Depending on the attack, several measures could be used to prevent any cryptographic flaws, for example, avoiding the usage of unknown encryption libraries, using SSL/TLS in communication channels, etc.
- Reference:  
[Cryptographic attacks](https://en.wikipedia.org/wiki/Category:Cryptographic_attacks#:~:text=A%20cryptographic%20attack%20is%20a,is%20also%20called%20"cryptanalysis".)  
### Private Key Prediction
- Severity: High
- Description:  
  A private key prediction refers to a situation where an attacker is able to predict or discover a private key that corresponds to a specific public address on the blockchain. The private key is used to sign and authorize transactions, and it should be generated and stored securely by the user. If a private key is predicted or discovered by someone else, they would be able to access the funds and assets associated with the corresponding address. This may happen due to a lack of randomness during the key generation process. 
- Recommendation:  
In order to prevent predictions, the seed phrase or private key should be generated using enough entropy to make it impossible to guess or predict. It should be used a True Random Number Generator (TRNG), which provides unpredictable output by physical means.
- Reference:  
[Hardware random number generator](https://en.wikipedia.org/wiki/Hardware_random_number_generator)  
### Length Extension Attack 
- Severity: Low
- Description:  
  A length extension attack is a type of cryptographic attack that targets hash-based message authentication codes (HMACs) and other similar constructs. It exploits a specific property of certain cryptographic hash functions, such as the SHA-1 and MD5 algorithms, which allows an attacker to compute a new hash value based on an original message and a known hash value, without knowing the original message or the key used to create the original hash.<br/>
  In a length extension attack, the attacker is able to append new data to the original message and calculate a new hash value that is valid for the original key. This allows the attacker to create a modified version of the original message and present it as the original message, without detection.
- Recommendation:  
  There are several ways to prevent length extension attacks:
<ol>
  <li>Use a different hash function: Avoid SHA-1 and MD5 algorithms, modern hash functions such as SHA-256 and SHA-3 are not vulnerable to length extension attacks.</li>
  <li>Use a keyed hash function: By using a keyed hash function, such as HMAC (Hash-based Message Authentication Code), the attacker will not be able to compute the new hash value without the key, even if they have the original message and the original hash value.</li>
  <li>Use a unique and random value (salt) for each message: By using a unique and random value, known as a salt, for each message, the attacker will not be able to use the same technique to calculate the new hash value for multiple messages.</li>
  <li>Use a message authentication code (MAC): A message authentication code (MAC) is a specific type of keyed hash function that is designed to be resistant to length extension attacks.</li>
  <li>Use a secure protocol design: Length extension attacks can also be prevented by using a secure protocol design. This involves carefully designing the protocol to ensure that it does not rely on the properties of the hash function that can be exploited by an attacker.</li>
</ol>
  
  It's important to note that the best way to prevent length extension attacks is to use a combination of these techniques and to keep software updated and follow best practices.
- Reference:  
[Length extension attack](https://en.wikipedia.org/wiki/Length_extension_attack)  
### Hash collision attack
- Severity: High
- Description:  
  A hash collision attack is a type of cryptographic attack that aims to find two different inputs that produce the same output hash value. In other words, it is a situation where two different inputs (e.g. messages, files, etc.) have the same hash value.<br/>
  Hash functions are designed to produce unique outputs (hashes) for each input, but certain types of hash functions, such as the MD5 and SHA-1 algorithms, have been shown to be vulnerable to collision attacks.
- Recommendation:  
  To prevent hash collision attacks, it is recommended to use a secure hash function such as SHA-256 or SHA-3, which have been designed to be resistant to collisions.
- Reference:  
[Signature Forgery Attacks on the IOTA Cryptocurrency](https://github.com/mit-dci/tangled-curl/blob/master/vuln-iota.md)

## Transactions
### Transaction Replay Attack
- Severity: High
- Description:  
  Also known as **Double Spend** attack.
  Double spending is one of the problems that blockchain technologies attempt to solve since their very inception. Most, if not all of the attacks in the blockchain, aim to perform a double spend at some point in their execution. In this attack scenario, an attacker attempts to spend the same currency at least two times, hence double-spend. This attack is definitely not possible in the physical terms of currency. It is not possible to buy a resource from one vendor and then spend the exact same coins with another vendor. The attacker attempts to perform a transaction, wait for the merchant to approve it, and then reverts it and spends the same currency in another transaction. In blockchains, this can be achieved by presenting a conflicting transaction possibly in a different branch. BFT systems with the use of absolute finality are considered to be robust against the double spend problem.
- Recommendations: 
<ol>
  <li>Check whether a UTXO has been spent. </li>
  <li>Use nonce to prevent transaction replay.  </li>
</ol>

### Transaction Malleability Attack
- Severity: High
- Description:  
A transaction malleability attack is a type of attack in which an attacker modifies the transaction ID (also known as a "txid") of a transaction before it is included in a block on the blockchain. This can be done by changing the signature on the transaction, which does not affect the actual contents of the transaction, but does change the txid.<br/>
As a result, the modified transaction will have a different txid than the original transaction, which can cause confusion and lead to issues such as double spending.<br/>
This is a known issue in Bitcoin and other blockchain networks that use transaction signatures to validate transactions.<br/>
We can define two types of transactions malleability:
  * **Signature Malleability**
The first form of malleability is in the signatures themselves. Each signature has exactly one DER-encoded ASN.1 octet representation, but OpenSSL does not enforce this, and as long as a signature isn't horribly malformed, it will be accepted. In addition for every ECDSA signature (r,s), the signature (r, -s (mod N)) is a valid signature of the same message.
  * **ScriptSig Malleability**
The signature algorithm used in Bitcoin does not sign any of the scriptSig to create the signature. While signing the whole scriptSig would be impossible - the signature would be signing itself - this does mean that additional data can be added such that it will be pushed on the stack prior to the required signatures and public keys. Similarly, OP_DROP can be added to leave the stack exactly as before prior to scriptPubKey execution.
- Recommendation:  
  To mitigate this type of attack, it is recommended to use a new transaction format, such as Segregated Witness (SegWit) which has been implemented in bitcoin to prevent transaction malleability. Also always check if the signature library used is malleable.
- References:  
  * [Transaction_Malleability](https://en.bitcoinwiki.org/wiki/Transaction_Malleability)  
  * [bip-0066-Strict DER signatures](https://github.com/bitcoin/bips/blob/master/bip-0066.mediawiki)  
  * [eip-2-Homestead Hard-fork Changes](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-2.md)  
### Time-Locked Transaction Attack
- Severity: Low
- Description:  
  Make tokens unavailable to token recipients by specifying the block height at which utxo can be spent.
- Recommendation:  
  Check whether a transaction is time-locked when receiving coins.
### False Top-Up Attack
- Severity: High
- Description:  
  Initiate a specially structured transaction to conduct a false transfer, resulting in a real top-up in the exchange.
- Recommendations:  
<ol>
  <li>Check all fields in the transaction event log.  </li>
  <li>The exchange or receiver should complete payment after the transaction was confirmed by enough blocks.  </li>
</ol>

- Reference:  
  [XRP false top-up](https://developers.ripple.com/partial-payments.html)  
### Rug Pull Attack
- Severity: High
- Description: 
  A Rug Pull Attack is a type of attack on a decentralized finance (DeFi) smart contract in which an attacker exploits the trust and confidence of investors by abruptly withdrawing the funds from the smart contract, leaving investors with worthless tokens. The attacker will usually do this by creating a fake token or project that seems legitimate and promising, then encouraging people to invest in it. Once the attacker has amassed a large amount of funds, they will withdraw the funds from the smart contract, leaving investors with worthless tokens and causing a significant loss for them.
- Recommendation:  
  There are several ways to prevent Rug Pull Attacks in decentralized finance (DeFi) smart contracts:
<ol>
  <li>Due Diligence: Before investing in any token or project, it is important to conduct thorough research and due diligence on the team behind the project, their experience, and the technology they are using. This can help to identify red flags and potential scams.</li>
  <li>Whitelists: Some projects use whitelists to limit participation in the token sale to only pre-approved investors. This can help to prevent rug pulls by scammers trying to quickly raise funds from a large number of unsuspecting investors.</li>
  <li>Smart Contract Auditing: Before deploying a smart contract, it should be audited by a reputable third-party auditor like <a href="https://hacken.io" target="_blank"> hacken.io</a> to ensure that it has been designed securely and without any vulnerabilities.</li>
  <li>Community awareness: Communities can play a huge role in preventing rug pull attacks by sharing information and warnings about potential scams, and also by promoting best practices for investors.</li>
  <li>Using decentralized exchanges (DEX) with a good liquidity, these platforms are less likely to be affected by a rug pull.</li>
</ol>