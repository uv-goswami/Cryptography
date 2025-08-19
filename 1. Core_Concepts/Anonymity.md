#Anonymity
-Anonymity means keeping the identity of the sender, receiver, or participant hidden.
-It makes sure people know something happened, but don't know who did it.

features
  -Sender and Receiver Anonymity: No one knows who sent or received the message
  -Unlinkability: Messages can't be linked to the same person.
  -Unobservability: Outsiders can't tell if communication happened.

Common Techniques:
  -Mixnets: Shuffle and encyprt messages. 
  -Onion Routing: Layers of encryption through multiple relays(used in TOR)
  -Ring Signature: A group signs, but the real signer stays hidden(used in Monero)
  -Zero-Knowledge Proofs: Prove something without revealing your identity or data.

  Application: 
    -e-voting: Vote Secretly, but count is verifiable.
    -Cryptocurrency: Moner & Zcash hide sender/receiver.
    -Anonymous messaging: TorChat.
    Access Control: Prove you'r eligible without revealing who you are.

  Limitations
    -Slower Performance (due to extra encryption & routing)
    -Metadata can still leak(timing,frequency)
    Advanced attackers can sometimes de-anonymize.
