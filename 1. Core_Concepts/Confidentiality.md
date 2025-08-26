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
