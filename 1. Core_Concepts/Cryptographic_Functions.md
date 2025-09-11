# 🧱 Key Derivation, Integrity, and Pseudorandomness

**Cryptographic primitives** like **PRF**, **HMAC**, **KDF**, and **MAC** are essential tools used to achieve **message integrity**, **key derivation**, and **secure authentication**. They don't encrypt data directly but act as *enablers* of secure systems by supporting confidentiality, authentication, and randomness.

---

## 🔐 Key Features

* **Integrity**
  Ensures that data has not been tampered with during transmission or storage.

* **Authentication**
  Verifies that a message was sent by a legitimate party using a shared or private key.

* **Pseudorandomness**
  Outputs appear random but are generated deterministically from secret keys.

* **Key Stretching / Derivation**
  Converts weak, short inputs (like passwords) into strong cryptographic keys.

---

## 🛠️ Core Primitives

| Primitive                               | Description                                              | Role                                |
| --------------------------------------- | -------------------------------------------------------- | ----------------------------------- |
| **PRF** *(Pseudorandom Function)*       | Deterministic function with random-looking output        | Used in KDFs, MACs, and TLS         |
| **HMAC** *(Hash-based MAC)*             | Combines a cryptographic hash (e.g., SHA-256) with a key | Provides integrity + authentication |
| **KDF** *(Key Derivation Function)*     | Derives strong keys from passwords or shared secrets     | Used in TLS, disk encryption        |
| **MAC** *(Message Authentication Code)* | Generic term for verifying message authenticity          | Includes HMAC, CMAC, etc.           |

---

## 📦 Applications

* **API Authentication**
  HMAC ensures only valid clients can send requests (e.g., AWS SigV4).

* **Password Hashing & Storage**
  KDFs like PBKDF2 or Argon2 protect against brute-force attacks.

* **Secure Messaging**
  MACs verify that messages haven’t been tampered with (e.g., Signal protocol).

* **TLS & VPNs**
  HMACs validate session messages; KDFs derive multiple keys from a single shared secret.

* **Blockchain Wallets**
  KDFs are used to derive private keys from passphrases.

---

## ⚠️ Limitations

* **Not for Confidentiality**
  These primitives don't encrypt data — they verify or derive.

* **Depends on Hash Strength**
  Weak hashes (like MD5 or SHA1) break the security of HMAC/KDF.

* **Brute-Force Risks**
  Without proper salting and iteration, KDFs can be brute-forced.

* **Implementation Bugs**
  Side-channel attacks (like timing attacks) may expose secrets if not mitigated.

---

## 🔄 Methods and Protocols

### 1. 🔁 Message Authentication

Used to **ensure message integrity** and **authenticate senders**.

* **HMAC**
  Combines a key with a hash (e.g., HMAC-SHA256) — used in TLS, APIs, JWTs.

* **CMAC**
  Uses block ciphers (like AES) instead of hashes for authentication.

---

### 2. 🔑 Key Derivation

Used to **derive secure encryption keys** from low-entropy secrets.

* **PBKDF2**
  Widely used password-based key derivation function with configurable iterations.

* **HKDF**
  Key derivation based on HMAC; used in TLS 1.3, QUIC.

* **Argon2**
  Memory-hard KDF designed for password hashing (resistant to GPUs/ASICs).

---

### 3. 🧠 Pseudorandom Functions

Secure building blocks used across cryptographic protocols.

* **PRFs**
  Used internally in KDFs, MACs, and TLS handshakes for key expansion.

* **OPRF (Oblivious PRF)**
  Allows client to compute PRF output without revealing its input to the server.

---

## 🔗 Relation to Other Concepts

* **Confidentiality**
  KDFs support encryption by securely generating symmetric keys.

* **Authentication**
  HMAC and MACs validate message sources.

* **TLS / VPNs / Secure Channels**
  Combine all three: key derivation, message integrity, and encryption.

* **ZKP / MPC**
  Often rely on commitments or pseudorandomness internally, built on PRFs.

---
