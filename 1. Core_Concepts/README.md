![confidentiality](https://github.com/uv-goswami/Cryptography/blob/main/Diagrams/Confidentiality.png)


### 🔐 How Confidentiality is Achieved: A Deeper Look

Confidentiality is the goal of keeping information secret. It's not a single tool but a property that is built using various cryptographic methods and primitives. 

#### Core Methods & Their Mechanics

* **Symmetric Encryption:** Achieves confidentiality by using a single key to both encrypt and decrypt. For example, to secure an email, you'd use a symmetric algorithm like **AES** with a key to scramble the message. The recipient must have the exact same key to unscramble it.
* **Asymmetric Encryption:** Achieves confidentiality using a key pair. If Alice wants to send a confidential message to Bob, she uses Bob's **public key** to encrypt it. The only key that can decrypt that message is Bob's corresponding **private key**. This ensures that only Bob can read the message.
* **Hybrid Encryption:** This is how most modern systems (like **HTTPS/TLS**) achieve confidentiality. It combines the strengths of both methods. First, the two parties use **asymmetric encryption** to securely agree on a new, temporary **symmetric key**. Then, they switch to the much faster **symmetric encryption** to handle the confidential bulk data transfer.

#### Foundational Primitives & Their Roles

These aren't confidentiality methods on their own, but they are essential for building a secure system.

* **KDF (Key Derivation Function):** A **KDF** achieves confidentiality indirectly by making it difficult for an attacker to guess a key. It takes a weak input, like a password, and "stretches" it through a complex, slow process to produce a strong, cryptographic key. This protects the confidentiality of the data by making the key resistant to brute-force attacks.
* **Salt:** A random value added to a password before it's processed by a **KDF**. It's not about confidentiality, but it's a critical component for key security. It ensures that even if two users have the same password, they'll have different keys, preventing attackers from using pre-computed tables to guess them.
* **PRF (Pseudorandom Function):** A function that acts as a core component of a **KDF**. It takes a key and an input and produces an output that appears random. This contributes to the confidentiality of the final key by making it unpredictable. An **OPRF** is a special type of PRF that contributes to confidentiality by allowing a client to get a pseudorandom output from a server without the server ever seeing the client's input.
* **HMAC (Hash-based Message Authentication Code):** **HMAC** is not a confidentiality tool. Its purpose is **integrity** and **authenticity**. It's used in conjunction with encryption to ensure the encrypted message hasn't been tampered with in transit.

#### Use Cases & Applications

* **Zcash:** Achieves confidentiality by using **Zero-Knowledge Proofs (ZKP)**. Instead of encrypting the entire blockchain, it uses a **zk-SNARK** to create a proof that a transaction is valid without revealing the confidential details of the sender, recipient, or amount.
* **Monero:** Achieves confidentiality and privacy through **RingCT** and **Ring Signatures**. **RingCT** cryptographically hides the transaction amount, and **Ring Signatures** hide the sender within a group of possible signers, contributing to both confidentiality and anonymity.
* **Homomorphic Encryption (HE):** This allows a cloud provider to perform computations on your confidential data (**Data at Rest** or **Data in Transit**) without ever needing to see the plaintext. The data remains encrypted throughout the entire process, providing a new level of confidentiality in cloud computing and machine learning.
* **EHRs (Electronic Health Records):** In this use case, confidentiality is a requirement for both **Data at Rest** (when medical records are stored) and **Data in Transit** (when they are transferred). This is achieved through strong encryption protocols and access controls.

## Challenges/Issues
1. Insider Threats, cyberattacks(brute force attacks,  
2. Human error, technical failure  
3. Weak Security measures  
4. Legal and regulatory requirements

![anonymity](https://github.com/uv-goswami/Cryptography/blob/main/Diagrams/Anonymity.png)

# 🕵️‍♂️ Anonymity

**Anonymity** is the state of being unidentifiable within a group of users. Unlike confidentiality, which hides the content of a message, anonymity focuses on hiding the identity of the sender, the recipient, or both. An anonymous communication ensures that observers cannot link a message to a specific person.

---

## 🔐 Key Features

- **Sender and Receiver Anonymity**  
  Identities of both parties are hidden from observers.

- **Unlinkability**  
  Multiple messages or actions cannot be linked to the same individual.

- **Unobservability**  
  Third parties cannot detect whether communication is taking place.

---

## 🛠️ Common Techniques

| Technique             | Description                                             | Example Use Case              |
|-----------------------|---------------------------------------------------------|-------------------------------|
| **Mixnets**           | Shuffle and encrypt messages to obscure sender links    | Anonymous email systems       |
| **Onion Routing**     | Multi-layer encryption through relays                   | Tor network                   |
| **Ring Signatures**   | Group signs a message; actual signer remains hidden     | Monero cryptocurrency         |
| **Zero-Knowledge Proofs** | Prove a statement without revealing other info     | Privacy-preserving access     |

---

## 📦 Applications

- **E-Voting**  
  Cast votes anonymously while ensuring vote count integrity.

- **Cryptocurrency**  
  Coins like Monero and Zcash hide sender and receiver identities.

- **Anonymous Messaging**  
  Tools like TorChat enable private communication.

- **Access Control**  
  Prove eligibility (e.g., age, membership) without revealing identity.

---

## ⚠️ Limitations

- **Performance Overhead**  
  Extra encryption and routing can slow down communication.

- **Metadata Leakage**  
  Timing, frequency, and volume of messages may still be exposed.

- **De-anonymization Risks**  
  Advanced attackers may correlate data to reveal identities.

---

## 🔄 Methods and Protocols

### 1. 🧪 Mixing Protocols

Mixing protocols break the link between transaction inputs and outputs.

- **CoinJoin**  
  Multiple users contribute to a single transaction; outputs are mixed.

- **CoinSwap**  
  Trustless exchange protocol that swaps coins between users.

- **CoinShuffle**  
  Decentralized mixing protocol without a central server.

- **Mixer / Tumbler**  
  Service that redistributes unlinked coins to obscure origins.

---

### 2. ✍️ Specialized Signatures

Advanced cryptographic signatures that provide sender anonymity.

- **Ring Signature**  
  Any member of a ring can sign; actual signer remains hidden.

- **RingCT (Ring Confidential Transactions)**  
  Combines Ring Signatures with confidential amounts.

- **Blind Signature**  
  Signer signs a message without seeing its content.

- **Identity Mixer (Idemix)**  
  Anonymous credentials using ZKPs and selective disclosure.

---

### 3. 🧠 Zero-Knowledge Proofs (ZKP)

Prove knowledge of a fact without revealing the fact itself.

- **Zcash**  
  Uses zk-SNARKs for shielded transactions hiding sender, receiver, and amount.

---

## 🔗 Relation to Other Concepts

- **Privacy**  
  Anonymity is a subset of privacy focused on identity concealment.

- **Digital Signature**  
  Ring and blind signatures extend basic authenticity to anonymity.

- **Zero-Knowledge Proofs**  
  Used for both confidentiality and anonymity (e.g., Zcash).

---

![intigrity](https://github.com/uv-goswami/Cryptography/blob/main/Diagrams/Intigrity.png)


# 🛡️ Integrity

Integrity is a core principle in cryptography that ensures data has not been altered or tampered with.  
Unlike confidentiality, which keeps data secret, integrity guarantees that the data is authentic and trustworthy.

> 📦 Analogy: A tamper-proof seal—it doesn’t hide the contents, but proves they haven’t been changed.

---

## 🔐 Features

- **Data Immutability**: Changes to data are detectable.  
- **Data Authenticity**: Verifies origin from a trusted source.  
- **Non-repudiation**: Sender cannot credibly deny having sent the message.

---

## 🛠️ Techniques

| Method              | Description                                                                 | Example Use Case               |
|---------------------|-----------------------------------------------------------------------------|--------------------------------|
| **Hashing**          | Produces a fixed-size digest; any change alters the output                 | Password storage, file checksums |
| **HMAC**             | MAC using a hash function and shared key for integrity + authenticity      | Securing API communication     |
| **Digital Signature**| Signs a hash using a private key; verifiable with a public key             | Software signing, secure email |

---

## 📦 Applications

- **Secure Communication**: TLS/SSL use MACs and digital signatures to ensure authenticity and integrity.  
- **Software Distribution**: Digital signatures verify origin and tamper-resistance of downloaded programs.  
- **Password Storage**: Hashes are stored and compared during login to verify credentials.  
- **Data Integrity**: Detect unauthorized changes in files, databases, or logs.

---

## ⚠️ Limitations

- **No Confidentiality**: Integrity mechanisms don’t hide data.  
- **Key Management Dependency**: Relies on secure private keys and trusted PKI systems.

---

## 🔄 Protocol-Level Implementation

### 🔍 Hashing

- One-way function producing a message digest.  
- Algorithms like `SHA-256`, `SHA-3` are sensitive to input changes.

```text
Input → Hash Function → Digest
```

### 🔐 Message Authentication Codes (MACs)

- Combines integrity and authenticity using a shared secret.  
- HMAC is a widely used variant.

```text
MAC = HMAC(Key, Message)
Verify: MAC' == MAC_received
```

### ✍️ Digital Signatures

- Sender signs a hash using their private key.  
- Receiver verifies using the sender’s public key.  
- Enables integrity, authenticity, and non-repudiation.

```text
Signature = Sign(PrivateKey, Hash(Message))
Verify(Signature, PublicKey) → Valid?
```

- **PKI**: Manages public keys and certificates.  
- **PGP**: Uses digital signatures for secure email and file integrity.

---

## 🔗 Related Concepts

| Concept           | Role in Integrity Context                                      |
|-------------------|---------------------------------------------------------------|
| **Confidentiality** | Separate but often paired; encryption ≠ integrity            |
| **Authenticity**    | Achieved via MACs and digital signatures                     |
| **PKI**             | Trust framework for verifying public keys                    |
| **TLS/SSL**         | Use MACs and signatures for secure, verifiable communication |

![signature](https://github.com/uv-goswami/Cryptography/blob/main/Diagrams/Digital_signature.png)
# ✍️ Cryptographic Signatures

Cryptographic signatures are foundational primitives in security protocols. They ensure authenticity, integrity, and non-repudiation of digital messages and transactions. This document outlines various signature types, their schemes, properties, infrastructure, and applications.

## 🌐 Overview

```
Signatures
├── Digital Signatures
├── Threshold Signatures
├── Advanced Signatures
└── Post-Quantum Signatures
```

---

## 🔐 Digital Signatures

Digital signatures bind a message to a sender using asymmetric cryptography. They are widely used in secure communication, software distribution, and identity verification.

### 🔧 Schemes

- **RSA**: Based on integer factorization; widely used in PKI and TLS.
- **DSA**: Uses discrete logarithms; standardized for government use.
- **ECDSA**: Elliptic curve variant of DSA; efficient and secure for constrained devices.
- **EdDSA**: Modern, deterministic signature scheme using Edwards curves; used in Signal, OpenSSH.

### 🧩 Properties

- **Authenticity**: Verifies the origin of the message.
- **Integrity**: Ensures the message has not been altered.
- **Non-repudiation**: Prevents the sender from denying authorship.

### 🏗️ Infrastructure

- **PKI (Public Key Infrastructure)**: Manages public keys and certificates.
- **Public Key**: Used for verification.
- **Private Key**: Used for signing.

### 📦 Applications

- TLS/SSL
- Software Signing
- Email Security (S/MIME, PGP)

---

## 🧮 Threshold Signatures

Threshold signatures allow a subset of parties (t-of-n) to collaboratively generate a valid signature without revealing individual keys.

### 🔑 Key Generation

- **Distributed Keygen**: Joint key generation without a trusted dealer.
- **Shamir Secret Sharing**: Splits a secret into shares; any t shares can reconstruct it.

### ✍️ Signing

- **t-of-n Parties**: Only t participants are needed to produce a valid signature.
- **MPC-Based**: Uses secure multi-party computation to generate signatures.

### ✅ Verification

- **Single Verifier**: Signature appears as if generated by a single entity.
- **Aggregated Signature**: Combines multiple partial signatures into one.

### 📦 Applications

- Blockchain Consensus (e.g., Algorand, Dfinity)
- Secure MPC
- Custodial Wallets (multi-sig)

---

## 🧠 Advanced Signatures

These schemes extend traditional signatures with privacy, anonymity, or efficiency enhancements.

### 🕵️ Ring Signatures

- **Property**: Anonymity—signer is hidden among a group.
- **Application**: Monero (private transactions)

### 👥 Group Signatures

- **Property**: Traceability and revocation—group manager can reveal signer.
- **Application**: Anonymous authentication in voting, corporate access

### 🙈 Blind Signatures

- **Property**: Privacy—signer cannot see the message being signed.
- **Application**: E-Cash, anonymous credentials

### ⚡ Aggregate Signatures

- **Property**: Efficiency—multiple signatures compressed into one.
- **Application**: BLS (used in Ethereum 2.0, threshold schemes)

---

## 🧪 Post-Quantum Signatures

Designed to resist attacks from quantum computers. These schemes are part of NIST’s post-quantum cryptography standardization.

### 🔐 Categories

- **Lattice-Based**: Based on hard lattice problems (e.g., Dilithium, Falcon)
- **Hash-Based**: Uses Merkle trees and hash functions (e.g., SPHINCS+)
- **Multivariate**: Based on solving multivariate polynomial equations

### 📦 Applications

- Quantum-Safe Messaging
- Firmware Signing
- Blockchain Identity Layers

---

## 🔗 Interconnections

| Signature Type       | Linked Concepts                          | Shared Features                         |
|----------------------|-------------------------------------------|------------------------------------------|
| Digital Signatures   | PKI, TLS, Email Security                 | Authenticity, Integrity, Non-repudiation |
| Threshold Signatures | MPC, Blockchain, Custody                | Distributed Trust, Aggregation           |
| Advanced Signatures  | Privacy Coins, Anonymous Auth           | Anonymity, Revocation, Efficiency        |
| Post-Quantum         | Quantum-Safe Protocols, NIST Standards  | Long-Term Security, Future-Proofing      |

---
