## GRIMM cryptography and privacy

GRIMM is powered by magic MimbleWimble protocol and based on Elliptical Cryptography, known as the Elliptic Curve Digital Signature 
Algorithm (ECDSA). GRIMM uses the secp256k1 elliptic curve, which is used in Bitcoin cryptography and is defined by standards for 
efficient cryptography. The most commonly used curves have an arbitrary structure, but secp256k1 was built not randomly, which allows 
it to calculate and be faster than other curves especially efficiently. Unlike the popular curves recommended by NIST (National Institute 
of Standards and Technology USA), secp256k1 were chosen in a predictable way, which significantly reduces the likelihood that the creator 
of such an elliptical curve inserted a secret passage for third parties into it. Why is it important?

In 2013, after the publication by Edward Snowden, the world learned that under the pressure of the NSA, NIST standardized the Dual_EC_DRBG 
pseudo-random number generator (based on EC) — one of the recommended for use in cryptographic products and implemented in such a form by 
dozens of vendors. Snowden’s documents directly indicate that the nonrandomness at Dual_EC_DRBG was introduced by the NSA to weaken the 
generator and, consequently, the subsequent easier cracking of ciphers. Theoretically, the standardization process at NIST is public. 
However, US laws oblige the Institute to use the assistance of the NSA — and at times this “help” into a dictate. After the scandal with 
Snowden, NIST officially advised against using Dual_EC_DRBG, but the scandal surrounding it gave rise to doubt the standards of elliptic 
curves published by NIST. Each cryptographic product that uses NIST EC guidelines has been exposed to the NSA. The sec256k1 elliptic curve 
was not included in the NIST recommendations and is a reliable basis not only for Bitcoin, but also for GRIMM and for many other 
cryptocurrencies. Bitcoin has the concept of a wallet, and in essence, its entire blockchain is a description of transactions between 
wallets and explicit emissions of new coins. When wallets make a transaction, they disclose to each other their public key, and the 
history of both past and future transactions of each other becomes visible to them. This is the global problem of this system — it is not 
confidential. There is no wallet concept in GRIMM. Instead of a wallet, in GRIMM there are unspent amounts (UTXO — Unspent Transaction 
Output) that belong to specific users. Most importantly, transactions are made between UTXOs, but not between wallets. A transaction in 
GRIMM is the conversion of one UTXOs to another.

Consider the scheme of how a confidential UTXO transaction occurs in GRIMM:

For example, user A owns UTXO in the form C1 = k1 * G + v1 * H and C2 = k2 * G + v2 * H, and he wants to transfer this to user B.
- • A informs B (via a secret channel) that he wants to transmit C1 and C2 to him, and divulges their contents.
- • B creates C3 = k3 * G + (v1 + v2) * H, where k3 is a randomly selected new blinding factor
- • B calculates k = k1 + k2-k3, where k3 total blinding factor
- • B calculates X = k * G the remainder (X), and creates a Schnorr signature for it
- • Transaction C1, C2 → C3 + bulletproofs for C3, X + signature is sent to the node.
- • The node checks that C1 + C2-C3 = X, that C3 has the correct bulletproof, and that X has the correct signature, which confirms that 
the point X does not contain a sum.

C — Pedersen commitments are based on the discrete logarithm problem; G and H are the generators of the elliptic curve group; v is the 
amount; k — secret random blinding key (blinding factor); Schnorr scheme is one of the most effective and theoretically based 
authentication schemes, which based on the difficulty of computing discrete logarithms; bulletproofs is an innovative protocol among 
its own kind and is part of a family of zero knowledge proof systems such as zk-SNARK and STARK.

It is important that the remainder can only be at the output of the transaction, but not at the input. This is what makes it asymmetric 
and irreversible. In the above example, we see that when combining transactions in the block, the remaining balances in UTXO are 
encoded using the Pedersen commitment and the blinding factor. Bulletproofs monitors the correct amount of coins in the output balance.
When forming the block itself, all transactions are sequentially written to the block, combining into one large transaction, which 
ultimately is a formed block. And in order for the history of these transactions to become inaccessible, all inputs / outputs are 
mixed / sorted, which erases their chronological order and simplifies their combination (CoinJoin method used).

An important point of confidentiality is IP anonymity. To achieve anonymity, the transaction to the node is sent not by the direct 
participant in the transaction, but by a random user. To do this, the finished transaction is first sent to a random user, with a 
randomly generated counter (time-to-live). Next user must also send it to another random user, while reducing the counter. And only 
at that moment when the counter will be zero, the transaction is sent to the node. Such a process is provided by the Dandelion ++ 
protocol presented by a team of developers from the University of Illinois at Chicago.

The secp256k1 elliptic curve, Pedersen’s commitment and Bulletproof, Schnorr’s signature and blinding factor, Dandelion ++ and CoinJoin 
— all these methods, cryptographic primitives and signatures work in a single bundle to ensure the highest level of confidentiality of 
the GRIMM and make it fungibility interchangeable, which is also an important property any cryptocurrency.
