
![Alt text for my diagram](path/to/your/diagram.svg)



## 📂 Structure

### 1) Core_Concepts.md
Foundational primitives and assumptions.
- Confidentiality, Integrity, Authenticity — security triad
- Confidentiality & Anonymity — secrecy vs unlinkability
- Digital Signatures — ECDSA, EdDSA (authenticity, non-repudiation)
- Threshold Signatures — split authority across parties
- PRF / MAC / KDF / HMAC — pseudorandomness, integrity, key derivation
- Random Oracle Model — idealized hash in proofs
- CRS (Common Reference String) — setup assumption in proofs
- Token Binding — bind authentication tokens to TLS sessions

---

### 2) Zero_Knowledge_Proofs.md
Prove correctness **without** revealing the secret.
- Interactive vs Non-Interactive (Fiat–Shamir)
- ZK-SNARKs — succinct proofs with trusted setup
- zk-STARKs — transparent, post-quantum friendly
- Bulletproofs — compact range proofs, no trusted setup
- ZKCP — zero-knowledge contingent payments
- ZK-Rollups — scalability with ZK aggregation
- ZKProofs community — standards & best practices

---

### 3) Advanced_Encryption.md
Encryption beyond the basics.
- Homomorphic Encryption — compute on ciphertexts
  - PHE (Partially Homomorphic)
  - SHE (Somewhat Homomorphic)
  - FHE (Fully Homomorphic)
- Functional Encryption — access-controlled decryption
- Attribute-Based Encryption (ABE) — policy-based access control

---

### 4) Privacy_in_Cryptocurrencies.md
Techniques for on-chain privacy.
- Mixers / Tumblers — obfuscate linkability
- CoinJoin / CoinShuffle / CoinSwap — transaction mixing
- Ring Signatures — anonymity sets
- RingCT (Confidential Transactions) — hide amounts
- Stealth Addresses — one-time addresses
- Monero — RingCT + stealth addresses
- Zcash — zk-SNARK-based privacy
- BOLT — privacy in Lightning channels
- PPC (Probabilistic Payment Channels) — efficient micropayments
- IOUs — off-chain payment instruments

---

### 5) Protocols_and_Practical_Applications.md
Where cryptography meets production systems.
- HTTPS / TLS / SSL — secure communications
- PSI (Private Set Intersection) — private overlap of sets
- PAKE (Password-Authenticated Key Exchange) — secure key exchange from passwords
- OPRF (Oblivious PRF) — blind PRF evaluations
- Issuer–Holder–Verifier model — digital identity basics
  - Claims — assertions by issuers
  - Selective Disclosure — reveal only what’s needed
- EHRs (Electronic Health Records) — privacy-preserving healthcare data

---

### 6) Advanced_Protocols_and_Models.md
Deeper tools for private computation.
- Secure Multi-Party Computation (MPC) — joint computation without sharing inputs
- Differential Privacy — formal privacy for statistics/ML
- Trusted Execution Environments (TEE) — enclaves (e.g., Intel SGX)
- Commitment Schemes — binding + hiding
- Oblivious Transfer (OT) — choose without revealing which
- Secure Channels — forward secrecy, deniability

---

### 7) Research_and_Emerging_Topics.md
What’s next in crypto & privacy.
- Post-Quantum Cryptography — lattice-/hash-based schemes
- Privacy-Preserving AI — federated learning with DP/MPC
- Blockchain Privacy beyond Money — smart contract confidentiality
- Confidential Computing — cloud + hardware security (Azure, GCP, Intel)
- Zero-Knowledge VMs — zkEVM, zkWASM
- Future Standards — NIST PQC, ZKProof standardization
