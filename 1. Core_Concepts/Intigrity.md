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
