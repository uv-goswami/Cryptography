![](https://github.com/uv-goswami/Cryptography/blob/main/Diagrams/cryptographic_primitives.png)
# 🔐 Cryptographic Primitives

Cryptographic primitives are the foundational building blocks of secure systems. They enable confidentiality, integrity, authentication, privacy, and randomness in digital protocols. This README outlines key primitives, grouped by category, with their schemes, properties, and applications.

---

## 🧱 Symmetric Primitives

Symmetric cryptography uses the same key for encryption and decryption. It's fast and efficient, ideal for bulk data encryption.

### 🔒 Block Ciphers

| Cipher | Description |
|--------|-------------|
| **AES** | Advanced Encryption Standard; widely used, secure, and efficient. |
| **DES** | Data Encryption Standard; legacy cipher, now considered insecure. |

**Applications**: VPNs, disk encryption, TLS, secure messaging.

### 🔁 Stream Ciphers

| Cipher     | Description |
|------------|-------------|
| **ChaCha20** | Modern, fast, secure stream cipher; used in TLS and mobile apps. |
| **RC4**      | Deprecated due to vulnerabilities; formerly used in SSL. |

**Applications**: Real-time encryption, low-latency communication.

### 🧾 Message Authentication Codes (MACs)

| MAC   | Description |
|-------|-------------|
| **HMAC** | Hash-based MAC; secure and widely used in APIs and TLS. |
| **CMAC** | Cipher-based MAC; uses block ciphers like AES. |

**Applications**: Data integrity, API authentication, secure storage.

---

## 🔑 Asymmetric Primitives

Asymmetric cryptography uses key pairs—public for encryption/verification, private for decryption/signing.

### 📬 Public Key Encryption

| Scheme   | Description |
|----------|-------------|
| **RSA**     | Based on integer factorization; used in PKI and TLS. |
| **ElGamal** | Based on discrete logarithms; supports homomorphic encryption. |

**Applications**: Secure messaging, key distribution, hybrid encryption.

### ✍️ Digital Signatures

| Scheme         | Description |
|----------------|-------------|
| **ECDSA**        | Elliptic Curve Digital Signature Algorithm; efficient and secure. |
| **EdDSA**        | Deterministic, fast, modern signature scheme. |
| **RSA Signature**| Signature variant of RSA; used in software signing and certificates. |

**Applications**: Authentication, document signing, blockchain.

### 🔄 Key Exchange

| Protocol         | Description |
|------------------|-------------|
| **Diffie-Hellman** | Classic key exchange using discrete logs. |
| **ECDH**           | Elliptic curve variant; faster and more secure. |

**Applications**: TLS handshake, secure messaging, VPNs.

---

## 🧮 Hash Functions

Hash functions map data to fixed-size outputs, ensuring integrity and supporting many cryptographic protocols.

### 🔧 Algorithms

| Hash     | Description |
|----------|-------------|
| **SHA-256** | Part of SHA-2 family; widely used in blockchain and TLS. |
| **SHA-3**   | Keccak-based; NIST standard alternative to SHA-2. |
| **BLAKE2**  | Fast, secure, and simpler than SHA; used in modern apps. |

### 📐 Properties

- **One-Way**: Cannot reverse the hash to get original input.
- **Collision Resistant**: Hard to find two inputs with same hash.
- **Fixed Output Size**: Output length is constant regardless of input.

**Applications**: Password hashing, digital signatures, data integrity.

---

## 🕵️ Zero-Knowledge Proofs

Allow a prover to convince a verifier of a statement’s truth without revealing the underlying data.

| Scheme       | Description |
|--------------|-------------|
| **ZK-SNARKs** | Succinct, non-interactive proofs; used in Zcash. |
| **ZK-STARKs** | Scalable, transparent proofs; post-quantum secure. |
| **Bulletproofs** | Efficient range proofs; used in confidential transactions. |

**Applications**: Privacy-preserving blockchain, identity verification, secure voting.

---

## 📦 Commitment Schemes

Allow committing to a value while keeping it hidden, with the ability to reveal later.

| Scheme                  | Description |
|-------------------------|-------------|
| **Pedersen Commitment** | Homomorphic and hiding; used in ZKPs and confidential transactions. |
| **Hash-Based Commitment** | Simple and efficient; uses hash functions to commit. |

**Applications**: Secure auctions, voting, ZK protocols.

---

## 🎲 Randomness Generators

Randomness is essential for key generation, nonce creation, and protocol security.

| Generator | Description |
|-----------|-------------|
| **CSPRNG** | Cryptographically Secure Pseudo-Random Number Generator; deterministic but secure. |
| **TRNG**   | True Random Number Generator; based on physical entropy. |

**Applications**: Key generation, nonce creation, secure initialization.

---

## 🔗 Interconnections

| Primitive Type         | Linked Concepts                     | Roles in Protocols                        |
|------------------------|--------------------------------------|-------------------------------------------|
| Symmetric Primitives   | MACs, Block/Stream Ciphers           | Confidentiality, Integrity                |
| Asymmetric Primitives  | PKI, Key Exchange, Signatures        | Authentication, Secure Communication      |
| Hash Functions         | MACs, Signatures, Commitments        | Integrity, One-Way Mapping                |
| Zero-Knowledge Proofs  | Commitments, Hashes                  | Privacy, Verifiability                    |
| Commitment Schemes     | ZKPs, Hashes                         | Binding and Hiding                        |
| Randomness Generators  | All Cryptographic Operations         | Unpredictability, Security Initialization |

---

## 📚 Further Reading

- [NIST Cryptographic Standards](https://csrc.nist.gov/publications)
- [ZK-STARKs Primer](https://starkware.co/stark/)
- [BLAKE2 Specification](https://blake2.net/)
- [Pedersen Commitments Explained](https://crypto.stackexchange.com/questions/50250)

