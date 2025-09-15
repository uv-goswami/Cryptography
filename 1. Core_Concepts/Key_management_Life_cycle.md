# Key
Cryptographic Key is a string of bits that is used to encrypt and decrypt data.
**Purpose**
* Encyprtion: Convert plaintext to unreadable ciphertext.
* Decryption: Convert ciphertext back to plaintext.
* Signing: Verify that the message came from trusted source and was not altered.
* Verification: Confirm the digital signature is Valid.


# Encryption
## Symmetric Encryption:
  - Uses a single, shared key for encryption and decryption.
  - Algorithms include AES, DES, RC4.
  - Pros:
    1. fast
    2. efficient
    3. Secure
  - Cons:
    1. Key Distribution is a problem
    2. Can't scale.
    3. If even one system is exposed, all communication is compromised.
  - Applications:
    1. Encrypted email and File Storage
    2. Full-disk encryption
    3. Data at rest protection in databases and cloud storage.

### Block Ciphers: 
  Block ciphers encrypt data in fixed size blocks(eg, 128 bits) by applying deterministic algorithm and secret key to each block independently. 

| Cipher | Description |
|--------|-------------|
| **AES (Advanced Encryption Standard)** | The most widely used block cipher today; known for strong security and efficiency; supports 128-, 192-, and 256-bit keys. |
| **DES (Data Encryption Standard)** | An older block cipher using 56-bit keys; considered insecure due to small key size and vulnerabilities. |
**Applications:** VPNs, disk encryption(eg, Bitlocker), TLS, secure messaging

### Stream Ciphers: 
  Stream Ciphers encrypt data one bit/byte at a time by combining with plaintext with a pseudorandom number. 
   Cipher | Description |
|--------|-------------|
| **ChaCha20** | A modern, fast, and secure stream cipher often used in TLS and mobile applications. It is designed to be efficient on software platforms. |
| **RC4** | Once widely used but now deprecated due to multiple security vulnerabilities. |

**Applications:** VPNs, disk encryption, TLS, secure messaging.

### Message Authentication Codes (MACs):
  MACs a cryptographic checksums generated from the message and secret key to verify data intigrity and authenticity.

  | MAC Type | Description |
|----------|-------------|
| **HMAC (Hash-based MAC)** | Combines a cryptographic hash function with a secret key; widely used in TLS, APIs, and digital signatures. |
| **CMAC (Cipher-based MAC)** | Uses block cipher algorithms (like AES) to generate authentication codes. |

Applications: Data integrity, API authentication, secure storage.

## Asymmetric Encryption:
  Uses a pair of keys, Public Key and Private Key, to encrypt and decrypt data.
  **Types of Keys**
    * Private Key: kept secret and is used for decryption or creating signatures/ signing a message.
    * Public key: shared openly and is used for encryption or verifying signatures.
  - Pros:
    1. No need to share the private key.
    2. Enables digital signatures.
  - Cons:
    1. Slower, Computationally heavy.
    2. Used for smaller data.
  - Applications:
    1. Secure Web Communtication(TLS/SSL)
    2. Email Signing
    3. Digital Signatures
    4. Blockchain: Bitcoin, Ethereum
    5. Secure Shell(SSH)
    6. Achieving Confidentiality, Digital Identity, Authentication, Intigrity
   
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

## Key Generation

Key Generation is the process of creating cryptographic keys using high-quality randomness and defined algorithms. These keys become the foundation for all encryption, signing, and authentication operations.

**Purpose**  
* Produce unpredictable keys that resist guessing and attacks  
* Ensure uniqueness so no two users share the same secret  
* Provide both symmetric and asymmetric key material as needed  

---

### Sources of Entropy

| Source            | Description                                                              |
|-------------------|--------------------------------------------------------------------------|
| TRNG (True RNG)   | Hardware-based randomness from physical phenomena (e.g., electronic noise) |
| PRNG (Pseudo RNG) | Software generator seeded by entropy to produce streams of random bits   |
| QRNG (Quantum RNG)| Quantum effects (e.g., photon behavior) supplying extremely high entropy |
| OS Facilities     | Built-in system calls (`/dev/random`, `getrandom()`, CryptGenRandom)     |

**Applications:**  
1. Seeding CSPRNGs for key material  
2. Generating nonces and salts in protocols  
3. Creating session keys in secure channels  

---

### Symmetric Key Generation

1. Gather sufficient entropy from TRNG or OS facilities.  
2. Seed a cryptographically secure PRNG (CSPRNG).  
3. Read N random bytes (e.g., 16 bytes for AES-128, 32 bytes for AES-256).  
4. Optionally wrap or encrypt the raw key (key-wrapping) before storage.  

| Algorithm  | Description                                  |
|------------|----------------------------------------------|
| AES Key    | Read 128/192/256 random bits directly       |
| ChaCha20   | Read 256 bits for ChaCha20 symmetric key    |

**Applications:**  
- Bulk data encryption (disk, database)  
- Securing communication sessions (TLS, VPN)  

---

### Asymmetric Key Generation

1. Collect high-quality entropy as above.  
2. Run the key algorithm:  
   - **RSA**: Pick two large random primes, compute n = p·q, derive e/d exponents.  
   - **ECC**: Choose a random integer d in [1, n–1], compute public point Q = d·G.  
3. Package keys in standard formats (PKCS#8, X.509, OpenSSH).  
4. Store private keys in secure vaults (HSM/TPM) and publish public keys or certificates.

| Algorithm     | Key Material Generated                       |
|---------------|-----------------------------------------------|
| RSA-2048      | 2048-bit modulus, public/private exponents   |
| ECDSA (P-256) | 256-bit private scalar and public point Q    |
| EdDSA (Ed25519)| 256-bit private scalar and public key bytes |

**Applications:**  
- Certificate issuance in PKI (HTTPS, email)  
- Digital signatures for code and documents  
- Identity management in SSH and blockchain  

---

### Key Formatting & Storage

- **Formats**:  
  - PKCS#8 for private keys, X.509 for public certs  
  - Raw byte blobs for hardware modules  
- **Storage**:  
  - Software vaults with encryption (e.g., AWS KMS, HashiCorp Vault)  
  - Hardware modules (TPM chips, HSM appliances)  
- **Post-Generation Cleanup**:  
  - Zero-ize memory buffers holding raw key bytes  
  - Securely wipe any temporary files

---

### Advantages & Disadvantages

- Advantages:  
  - High-quality randomness resists brute-force and prediction  
  - Standards-based algorithms ensure interoperability  
- Disadvantages:  
  - Hardware RNGs can be slow or fail without fallback  
  - Poor seeding leads to weak, repeatable keys  

---

### Implementation Tips & Prerequisites

- Always use vetted libraries (OpenSSL, libsodium, `cryptography`).  
- Ensure OS RNG is healthy (monitor entropy pools).  
- For sensitive keys, prefer hardware modules (TPM/HSM).  
- Follow compliance standards (FIPS 140-2/3, PCI-DSS) when required.  
- Rotate keys periodically and securely destroy old ones.  
---

![KG](https://github.com/uv-goswami/Cryptography/blob/88ca27e88372ff86bd61dcdbb245027ff2991852/Diagrams/KeyGeneration.drawio.svg)

----
  
      











# Key Life Cycle 
![KLC](https://github.com/uv-goswami/Cryptography/blob/289897c43e356e1038d2c73d58ed611b64de11a0/Diagrams/Key_Life_cycle.svg)
