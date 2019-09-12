# Grimm Magic Paper
"MimbleWimble", we cast this spell so mote it be. GRIMM was born. 
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
## NO ONE WILL EVER KNOW
Den Novak & Andrew COP


## Table of contents

- Intro
- What we see
- [Cypherpunk's Manifesto](https://github.com/freenetcoder/Manifesto/blob/master/cypherpunk_manifesto.md)
- How it works
- Grimm Direction
- Grimm specifications
- [Grimm coins allocation](https://github.com/freenetcoder/Manifesto/blob/master/coins_allocation.md)
- Grimm tech
  - Protocol Mimblewimble
  - [Mimblewimble whitepaper](https://github.com/freenetcoder/Manifesto/blob/master/Mimblewimble_Whitepaper.md)
  - Cryptographic
  - Bulletproof
  - Dandelion ++
  - Grimm POW Algorithm (base on Equihash 150_5)
- API
  - [Wallet API documentation](https://github.com/freenetcoder/Manifesto/blob/master/api/wallet_api.md)
  - [Explorer API documentation](https://github.com/freenetcoder/Manifesto/blob/master/api/explorer_api.md)
  - [Mining API stratum](https://github.com/freenetcoder/Manifesto/blob/master/api/mining_api_stratum.md)
- Guides
  - [Cli Wallet User Guide](https://github.com/freenetcoder/Manifesto/blob/master/wallet_cli_commands.md)
  - [Node settings](https://github.com/freenetcoder/Manifesto/blob/master/node_mining_mode.md)
  - [Solo Mining Guide](https://github.com/freenetcoder/Manifesto/blob/master/solomining.md)
  - [Integration Grimm guide for exchanges/pools](https://github.com/freenetcoder/Manifesto/blob/master/integration/main.md)
- Resources

## Intro
Speaking at a decentralised Internet conference,  Edward Snowden has warned that Bitcoin’s public ledger is a
“long-lasting flaw” that has large implications for the overall privacy of the cryptocurrency.

Bitcoin is built on a piece of technology called the blockchain, which is a record of transactions that’s available
to view by anyone. It’s also decentralised, meaning that its data is held in multiple locations all around the world,
without being in the control of one single organisation.

The public ledger means that it’s actually possible for anyone to view the transactions (ammounts and addresses) that
are taking place, even if the blockchain doesn’t tell you who each of its digital wallets belongs to.

Knowledge of amounts and addresses means a different agencies could, track a Bitcoin transaction from these addresses,
and follow the transactions until they end up at an centralized exchange. It is also possible to track the IP addresses
of a Bitcoin transactions if an entity runs a large amount of relay nodes on the network.

Such organizations are paying close attention to addresses with transfers of large sums of funds. And therefore the public
ledger must hide real transaction amounts and addresses. Although there are Add-in methods of increasing the privacy of
transactions on the blockchain uses at privacy coins (Bitcoin forks) such as Zcash and Monero, we sees more promise in
cryptocurrencies built from the ground with default build-in privacy.

So in the Grimm blockchain, we use a different protocol than the bitcoin and its forks. The mimblewimble protocol. It's
idea was described in 2016 by a Tom Elvis Jedusor, pseudonymous developer in a Bitcoin developers’ channel. The idea
mimblewimble to significantly improve privacy and scalability of Bitcoin and other cryptocurrency networks by creating
an efficient, confidential Blockchain which ensures that transaction does not create surplus money and proof of Ownership
is established through private keys. Essentially, the protocol addresses gaps existing in almost all current Blockchain
implementations by building upon the twin concepts called "Confidential Transactions" and "Transaction Cut - Through".
To date, two projects supported the Mimblewimble and are developing this protocol in their projects. These are Beam and
Grin projects. Tom Jedusor's ideas fully reflect our vision for a dapps communication protocol in the near future.

## What we see.
We see existing conditions and systems of control, not governed by logic or reason but by greed, corporatism, subversion,
bureaucracy, censorship, and inefficiency.
We have a strong distrust for inherently flawed and corrupt systems. Our value transparency, free speech, privacy, and
real decentralization.

We designed Grimm so that it doesn’t depend on any one person. We don’t control it. Not financially. Not physically. How
can decentralized work if only founders or entities controls the system? They accumulate taxes, head the richest lists
in their projects, or play an unfair game with an unlimited extra coin emission. Grimm is a classic fork of Beam, open
source, without founders rewards, ico, premine and other commercial shit. Privacy and scalability - two most prominent
problems challenges bedeviling the existing Blockchain ecosystem today. So we chose the Mimblewimble protocol, which
has fully addressed these problems initially. We are not in favour of mix decentralized projects with a commercial
semblance of decentralization. Grimm's got a different, absolutely decentralized way.

Our main point: "Cryptocurrency is a way to convey value from one person to another without a third party". It's not a
commodity or a stock or a company, it is a method, a container, a protocol that people use to make purchases between
themselves. Centralized exchanges it's third party, that focused on personal gain. Full access to your money. Pressure
regulators. Hacking capability. Influence on the market. Artificial volatility. Manipulation. Listing. Delisting.
Relisting. Users don't know what they're buying. That's why Grimm supported decentralized exchanges.

Grimm is based on Baldwin and Clark’s concept of modularity: Breaking a technology or process into functionally relevant components facilitates innovation. Modularity (3dparty modules) is a technique used in software development. It breaks a complex technological project into a number of functionally relevant components — integrated in core where is called for, and individually designed where differentiation is needed.
In a Grimm structure,  modules, can easily be addaed or swapped out, upgraded, and adapted in different ways for different systems. Modularity makes it easier to the co-development of the project by our community members, who will proudly be known as "Grimmers".

## How it works

Grimm uses Bitcoin’s Unspent Transaction Output Model (UTXO). According to this model, there are three types of information that must be hidden in order to make a transaction confidential — sender information, recipient information, and transaction amount.
Mimblewimble protocol (used in GRIMM)itself achieves this goal using the following two encryption methods:
1. Confidential Transactions: This system was developed by Adam Beck and later continued by Gregory Maxwell. You can hide the values of transaction amounts using homomorphic encryption and blinding factor, where the former is an algorithm that splits the amount of transaction value into several parts, and the latter mixes transaction amounts with random numbers to additionally hide the values of the divided transaction amounts. In addition, in the MW transaction, the recipient receives a range of blinding factors sent by the sender to act as a private key, thus verifying ownership confirmation and completing the transaction.
2. CoinJoins: This cryptographic technology was also proposed by Gregory Maxwell. The method mixes the transaction pool in such a way that it is impossible to determine who sent the money to whom. In the Mimblewimble scheme, a data block will consist of number of inputs, outputs, and signature data. However, the block can still be validated by subtracting the total inputs from the total outputs to achieving a result of zero. This is a much more efficient system compared to the Bitcoin blockchain, where it is necessary to analyze the whole history of the block to be verified and considered valid. This method also offers significant space savings and offers the execution of multiple transactions at the same time.

But Mimblewimble alone does not counteract all types of blockchain analysis. If implemented naively, Mimblewimble leaves room for peer-to-peer network type analysis, which is very similar to traditional blockchain analysis. That’s why in addition to these MW methods, aggregated transactions as they spread across the network, are combined using Dandelion of peer-to-peer obfuscation technique in Grimm. During the Dandelion stem phase, before the TX’s are broadcast to the P2P layer, they are being combined together (CoinJoin). And an addition to this, Decoy Outputs are used, which are added if necessary. Grimm is fundamentally private. And it’s great! But you can ask — what about transparency? How I can prove a transaction to a third party? Grimm is optionally transparent. Payment Proof feature — a cryptographically secure way to prove that a certain transaction really occurred. You can copy payment proof code from your wallet and give it to someone to check (in another wallet) this transaction details (sender, receiver, amount).

GRIMM uses the secp256k1 elliptic curve, which is used in Bitcoin cryptography and is defined by standards for efficient cryptography. The most commonly used curves have an arbitrary structure, but secp256k1 was built not randomly, which allows it to calculate and be faster than other curves especially efficiently. Unlike the popular curves recommended by NIST (National Institute of Standards and Technology USA), secp256k1 were chosen in a predictable way, which significantly reduces the likelihood that the creator of such an elliptical curve inserted a secret passage for third parties into it. Why is it important?
In 2013, after the publication by Edward Snowden, the world learned that under the pressure of the NSA, NIST standardized the Dual_EC_DRBG pseudo-random number generator (based on EC) — one of the recommended for use in cryptographic products and implemented in such a form by dozens of vendors. Snowden’s documents directly indicate that the nonrandomness at Dual_EC_DRBG was introduced by the NSA to weaken the generator and, consequently, the subsequent easier cracking of ciphers. Theoretically, the standardization process at NIST is public. However, US laws oblige the Institute to use the assistance of the NSA — and at times this “help” into a dictate.
After the scandal with Snowden, NIST officially advised against using Dual_EC_DRBG, but the scandal surrounding it gave rise to doubt the standards of elliptic curves published by NIST. Each cryptographic product that uses NIST EC guidelines has been exposed to the NSA. The sec256k1 elliptic curve was not included in the NIST recommendations and is a reliable basis not only for Bitcoin, but also for GRIMM and for many other cryptocurrencies.
Bitcoin has the concept of a wallet, and in essence, its entire blockchain is a description of transactions between wallets and explicit emissions of new coins. When wallets make a transaction, they disclose to each other their public key, and the history of both past and future transactions of each other becomes visible to them. This is the global problem of this system — it is not confidential.
There is no wallet concept in GRIMM. Instead of a wallet, in GRIMM there are unspent amounts (UTXO — Unspent Transaction Output) that belong to specific users. Most importantly, transactions are made between UTXOs, but not between wallets. A transaction in GRIMM is the conversion of one UTXOs to another.

Consider the scheme of how a confidential UTXO transaction occurs in GRIMM:
For example, user A owns UTXO in the form C1 = k1 * G + v1 * H and C2 = k2 * G + v2 * H, and he wants to transfer this to user B.
• A informs B (via a secret channel) that he wants to transmit C1 and C2 to him, and divulges their contents.
• B creates C3 = k3 * G + (v1 + v2) * H, where k3 is a randomly selected new blinding factor
• B calculates k = k1 + k2-k3, where k3 total blinding factor
• B calculates X = k * G the remainder (X), and creates a Schnorr signature for it
• Transaction C1, C2 → C3 + bulletproofs for C3, X + signature is sent to the node.
• The node checks that C1 + C2-C3 = X, that C3 has the correct bulletproof, and that X has the correct signature, which confirms that the point X does not contain a sum.
C — Pedersen commitments are based on the discrete logarithm problem; G and H are the generators of the elliptic curve group; v is the amount; k — secret random blinding key (blinding factor); Schnorr scheme is one of the most effective and theoretically based authentication schemes, which based on the difficulty of computing discrete logarithms; bulletproofs is an innovative protocol among its own kind and is part of a family of zero knowledge proof systems such as zk-SNARK and STARK.
It is important that the remainder can only be at the output of the transaction, but not at the input. This is what makes it asymmetric and irreversible.
In the above example, we see that when combining transactions in the block, the remaining balances in UTXO are encoded using the Pedersen commitment and the blinding factor. Bulletproofs monitors the correct amount of coins in the output balance.
When forming the block itself, all transactions are sequentially written to the block, combining into one large transaction, which ultimately is a formed block. And in order for the history of these transactions to become inaccessible, all inputs / outputs are mixed / sorted, which erases their chronological order and simplifies their combination (CoinJoin method used).
An important point of confidentiality is IP anonymity. To achieve anonymity, the transaction to the node is sent not by the direct participant in the transaction, but by a random user. To do this, the finished transaction is first sent to a random user, with a randomly generated counter (time-to-live). Next user must also send it to another random user, while reducing the counter. And only at that moment when the counter will be zero, the transaction is sent to the node. Such a process is provided by the Dandelion ++ protocol presented by a team of developers from the University of Illinois at Chicago.
The sec256k1 elliptic curve, Pedersen’s commitment and Bulletproof, Schnorr’s signature and blinding factor, Dandelion ++ and CoinJoin — all these methods, cryptographic primitives and signatures work in a single bundle to ensure the highest level of confidentiality of the GRIMM and make it fungibility interchangeable, which is also an important property any cryptocurrency.

## Grimm direction

- ASIC resistance as core value
- FAIR, OPENSOURCE, Community driven coin
- Anonymous, instant mimblewimble p2p messages not stored in blockchain for secure information transfer
- p2pool for ultimate mining decentralization
- mobile wallets for on the go privacy protection
- blockchain services for easy blockchain interaction
- smart contracts for discovering new universes
- atomic swaps for decentralized crosschain exchanges
- private assetchains based on Grimm blockchain
- lightning network

## Grimm specifications

- Protocol / MimbleWimble
- Language / C++
- Consensus / PoW
- PoW Algorithm / spec. -GrimmPOW base Equihash 150_5
- Mining / Grimm wallet with built-in GPU and CPU mining (MacOS, Windows, Linux)
- Mining pools / [Official PPLNS pool](https://grimm.ravepool.com/)
- Mining pools / [Friend Sunpool PPLNT](https://grimm.sunpool.top/)
- External miners / Gminer for Nvidia & AMD (Grimm POW from [1.54 ver.](https://github.com/develsoftware/GMinerRelease/releases/tag/1.54)) / [MiniZ](https://miniz.ch/features/#mining-algorithm) for Nvidia
- Emission / Deflationary
- Block Reward / 100 GRIMM, Rewards halving after 1 year and then halvings every 4 years 33 times in total. All mining
- rewards go directly to the miners.
- Max Supply / 262.8M
- Governance / Community
- Blocktime / 60 sec
- Block size / 2 Mb
- Smallest unit / CENTUM (0.00000001 GRIMM)

## Grimm tech.

### MimbleWimble protocol

Mimblewimble is a blockchain protocol designed for confidential transactions. The essence is that a Pedersen Commitment to 0 can be viewed as an Elliptic Curve Digital Signature Algorithm (ECDSA) public key, and that for a valid confidential transaction, the difference between outputs, inputs and transaction fees must be 0. A prover constructing a confidential transaction can therefore sign the transaction with the difference of the outputs and inputs as the public key. This enables a greatly simplified blockchain in which all spent transactions can be pruned, and new nodes can efficiently validate the entire blockchain without downloading any old and spent transactions. The blockchain consists only of block-headers, remaining Unspent Transaction Outputs (UTXO) with their range proofs and an unprunable transaction kernel per transaction. Mimblewimble also allows transactions to be aggregated before being committed to the blockchain.
GRIMM supports setting an explicit incubation period on a UTXO, which limits its ability to be spent to a specific number of blocks after its creation. This is different to a timelock, which prevents a transaction from being added to a block before a certain time. GRIMM also supports the traditional timelock feature, but includes the ability to also specify an upper time limit, after which the transaction can no longer be included in a block. This feature means that a party can be sure that if a transaction is not included in a block on the main blockchain after a certain time, it will never appear.

Dandelion improves privacy by adding decoy transaction outputs at the stem phase. Each such output has a value of zero, but is indistinguishable from regular outputs. At a later stage (a randomly calculated number of blocks for each output), the UTXOs are added as inputs to new transactions, thus spending them and removing them from the blockchain.

In Grimm's Mimblewimble, as transactions are added, cut-through is performed, which eliminates all intermediary transaction commitments. However, the transaction kernels for every transaction are never removed. There are scheme to reuse these transaction kernels to validate subsequent transactions. In order to consume the existing kernels without compromising the transaction irreversibility principle, multiplier be applied to an old kernel by the same user who has visibility of the old kernel, and that this be used in a new transaction. In order to incentivize transactions to be built in this way.

When constructing a valid Mimblewimble transaction, the parties involved need to collaborate in order to choose blinding factors that balance. This interactive negotiation requires a number of steps and it implies that the parties need to be in communication to finalize the transaction. GRIMM use a Secure Bulletin Board System (SBBS) that is run on GRIMM full-nodes to allow for asynchronous negotiation of transactions.

Requiring the interactive participation of both parties in constructing a transaction can be a point of friction in using a Mimblewimble blockchain. In addition to the secure BBS communication channel, GRIMM also plans to support one-sided transactions where the payee in a transaction who expects to be paid a certain amount can construct their half of the transaction and send this half-constructed transaction to the payer.

Grimm make use of a number of Merkle tree structures to keep track of various aspects of the respective blockchains. Details of the exact trees and what they record are documented. GRIMM makes use of a Radix-Hash tree structure for some of its trees. This structure is a modified Merkle tree that is also a binary search tree. This provides a number of features that the standard Merkle trees do not have, and which GRIMM exploits in its implementation.

### Cryptographic

Cryptographic primitives based on the secp256k1 library (like bitcoin). Naturally it uses the same elliptic curve equation. The following primitives are used directly:

    secp256k1_gej - Basic curve point arithmetics: point addition, doubling, negation, import/export to a platform-ndependent format.
    secp256k1_scalar - Scalar arithmetics: addition, multiplication, inverse
    secp256k1_sha256_t - SHA-256 hash
    Cryptographic nonce generation (nonce_function_rfc6979).
    secp256k1_hmac_sha256_t - HMAC (message authentication)

The following cryptographic functions and schemes are built over them:

    Point multiplication (by a scalar).
        There are different multiplication modes and scenarios:
            Secure/Fast
            Point may be either known in advance (a.k.a. Generator, prepared for multiplication) or "casual".
            Aggregation: when many points are multiplied by scalars and summed - an appropriate effective algorithm is used.
        The reason that this functionality is implemented in Grimm and not taken directly from secp256k1 is the following:
            We'd like to have more low-level control of the primitives to implement advanced schemes
            We need more generators: Standard secp256k1 supports just two (G,H), whereas we need many more (131)
            No effective aggregation implementation
    Commitments (encoded amount with the blinding factor)
    Schnorr's signatures (including multi-sig)
    Bulletproofs (including multi-sig and batch verification)
    Secure communication channels
    Secure BBS messaging system

The Hash refers to the SHA-256 hash, unless otherwise specified. Used in various schemes. When hashing some data, it's fed in a way that is both platform-independent and unambiguous. This is achieved by the following specifications:

    1-byte data is fed as-is
    Boolean values are encoded as a single byte with value either 0 or 1.
    Strings are fed as-is, including the 0-terminator (to prevent ambiguity for consequent strings).
    Numerical types (fixed-point) are stored as a variable-length byte sequence, with a special terminator mark. This ensures platform independence (integers may have varying width across different platforms).
    Non-primitive types are converted into the platform-independent binary format for hashing.

The following objects are derived from hash (built over them)

Oracle

Oracle is used in non-interactive cryptographic proofs, it's supposed to produce cryptographic challenges in a deterministic way, based on the visible transcript to the moment.

In Grimm Oracle uses the Hash in a straightforward way. All the visible transcript is hashed. Once the challenge is needed - the hash value is finalized, the result is the challenge, and it's immediately re-fed to the Hash. So that the new challenge construction (if needed) is generated from the visible transcript, including the previous challenge.

If there are restrictions for the challenge (such as it should be non-overflowing, non-zero scalar, or a valid x-coordinate of a curve point) - the Finalize-Re-feed is called in a loop, until the satisfying challenge is produced (i.e. accept/reject strategy is used).

Nonce Generator

Also used in cryptographic proofs, but, unlike Oracle, the nonce generation involves secret data, and should not be possible to reconstruct by others.

In Grimm Nonce generator is a combination of an Oracle, and the nonce function initialized by the secret data. That is, the Oracle accounts for all the visible transcript. When a nonce is needed - first it's received from the Oracle, and then passed as an input to the nonce function (implemented in (secp256k1), which also uses the secret data.

The final nonce generation function implemented in secp256k1 actually a modified HMAC-SHA-256 scheme.
KDF - Key derivation function

All the private keys are generated via KDF. In Grimm it's implemented via the Nonce generator, which is initialized once by the master secret data. The requested key parameters (key index, type/subtype, etc.) are hashed and then the output is generated by the standard Nonce generator initialized with the master secret.
Schnorr's signature

Implemented according to the standard, the "long" version, compatible with batch verification. Consists of a pair [P,k], whereas P is an arbitrary EC point, and k is the blinded private key. Supports multisignature of course.

Specifically the scheme is the following. Given a message hash M, private key sk, public key pk = G * sk:

    Prover
        Generate a nonce nk = Nonce(sk, M), whereas Nonce() is the standard nonce generating function.
        Calculate: P = nk*G
        Expose to Oracle: P, M
        Get the challenge e from Oracle.
        Calculate k = - nk - e*sk
        Signature: [P, k]
    Verifier
        Expose to Oracle: P, M
        Get the challenge e from Oracle.
        Verify: k*G + e*Pk + P == 0

Binary platform-independent representation of the ECC primitives

The following are the primitives:

    ECC Scalar
        256-bits wide integer, representing the number in a big-endian format (via uintBig)
        Deserialization ensures the number is indeed a valid scalar, i.e. strictly less than modulo-prime, to prevent ambiguity
    ECC Point
        Represented as an X-coordinate, and a Y-parity flag (1 bit).
        The X-coordinate is serialized via uintBig (similar to scalar).
        To recover the Y-coordinate one must solve a quadratic equation, which, naturally has 2 solutions. This is where Y-parity flag is used.
        When serialized individually the data is padded to a byte boundary (means the Y-parity bit takes the whole byte). However in some complex data types those flags are merged and stored separately (Ex: Bulletproofs).


### Bulletproof

The Bulletproofs technology is a Non-interactive Zero-knowledge (NIZK) proof protocol for general Arithmetic Circuitsdef with very short proofs (Arguments of Knowledge Systemsdef) and without requiring a trusted setup. They rely on the Discrete Logarithmdef (DL) assumption and are made non-interactive using the Fiat-Shamir Heuristicdef. The name "Bulletproof" originated from a non-technical summary from one of the original authors of the scheme's properties: "Short like a bullet with bulletproof security assumptions".

Bulletproofs also implement a Multi-party Computation (MPC) protocol, whereby distributed proofs of multiple provers with secret committed values are aggregated into a single proof before the Fiat-Shamir challenge is calculated and sent to the verifier, thereby minimizing rounds of communication. Secret committed values will stay secret.

The essence of Bulletproofs is its inner-product algorithm originally presented by Groth and then further refined by Bootle et al. The latter development provided a proof (argument of knowledge) for two independent (not related) bindingdef vector Pedersen Commitmentsdef that satisfied the given inner-product relation. Bulletproofs build on these techniques, which yield communication-efficient, zero-knowledge proofs, but offer a further replacement for the inner product argument that reduces overall communication by a factor of three.

The basis of confidential transactions is to replace the input and output amounts with Pedersen Commitmentsdef. It is then publicly verifiable that the transactions balance (the sum of the committed inputs is greater than the sum of the committed outputs, and all outputs are positive), while keeping the specific committed amounts hidden. This makes it a zero-knowledge transaction. The transaction amounts must be encoded as integers mod q, which can overflow, but are prevented from doing so by making use of range proofs. This is where Bulletproofs come in. The essence of Bulletproofs is its ability to calculate proofs, including range proofs, from inner-products.

The prover must convince the verifier that commitment C(x,r)=xH+rG contains a number such that x∈[0,2n−1]. If a=(a1,...,an)∈0,1n is the vector containing the bits of x, the basic idea is to hide all the bits of the amount in a single vector Pedersen Commitment. It must then be proven that each bit satisfies ω(ω−1)=0, i.e. each ω is either 0 or 1, and that they sum to x. As part of the ensuing protocol, the verifier sends random linear combinations of constraints and challenges ∈Zp to the prover. The prover is then able to construct a vectorized inner product relation containing the elements of a, the constraints and challenges ∈Zp, and appropriate blinding vectors ∈Znp.

These inner product vectors have size n that would require many expensive exponentiations. The Pedersen Commitment scheme, shown in Figure 1, allows for a vector to be cut in half, and for the two halves to be compressed together, each time calculating a new set of Pedersen Commitment generators. Applying the same trick repeatedly, log2n times, produces a single value. This is applied to the inner product vectors; they are reduced interactively with a logarithmic number of rounds by the prover and verifier into a single multi-exponentiation of size 2n+2log2(n)+1. This single multi-exponentiation can then be calculated much faster than n separate ones. All of this is made non-interactive using the Fiat-Shamir Heuristicdef.

Bulletproofs only rely on the discrete logarithm assumption. In practice, this means that Bulletproofs are compatible with any secure elliptic curve, making them extremely versatile. The proof sizes are short; only [2log2(n)+9] elements are required for the range proofs and [log2(n)+13] elements for arithmetic circuit proofs, with n denoting the multiplicative complexity. Additionally, the logarithmic proof size enables the prover to aggregate multiple range proofs into a single short proof, as well as to aggregate multiple range proofs from different parties into one proof.

If all Bitcoin transactions were confidential, approximately 50 million UTXOs from approximately 22 million transactions would result in roughly 160GB range proof data, when using current/linear proof systems and assuming use of 52 bits to represent any value from 1 satoshi up to 21 million bitcoins. Aggregated Bulletproofs would reduce the data storage requirement to less than 17GB.
In Mimblewimble, the blockchain grows with the size of the UTXO set. Using Bulletproofs as a drop-in replacement for range proofs in confidential transactions, the size of the blockchain would only grow with the number of transactions that have unspent outputs. This is much smaller than the size of the UTXO set.

### Dandelion ++

Dandelion is a transaction broadcasting mechanism that reduces the risk of eavesdroppers linking transactions to the source IP. Moreover, it allows Grimm transactions to be aggregated (removing input-output pairs) before being broadasted to the entire network giving an additional privacy perk.

Mechanism
Dandelion transaction propagation proceeds in two phases: first the “stem” phase, and then “fluff” phase. During the stem phase, each node relays the transaction to a single peer. After a random number of hops along the stem, the transaction enters the fluff phase, which behaves just like ordinary flooding/diffusion. Even when an attacker can identify the location of the fluff phase, it is much more difficult to identify the source of the stem.

Illustration:

                                                   ┌-> F ...
                                           ┌-> D --┤
                                           |       └-> G ...
  A --[stem]--> B --[stem]--> C --[fluff]--┤
                                           |       ┌-> H ...
                                           └-> E --┤
                                                   └-> I ...
This mechanism also allows Grimm transactions to be aggregated during the stem phase and then broadcasted to all the nodes on the network. This result in transaction aggregation and possibly cut-through (thus removing spent outputs) giving a significant privacy gain similar to a non-interactive coinjoin with cut-through.

### Grimm POW Algorithm Equihash 150_5

What is Equihash?
Despite its name Equihash is no hash function in the narrow sense. Instead an Equihash solution is the solution to a mathematical problem. The problem can be formulated like follows.
Definition 1. Let n and k be the Equihash parameters and let work and nonce be given bitstreams. Then we define m := n/k+1  to be the collision length for n and k. Further let
B(k) := Blake2B (concat (work, nonce, l)) be  the output of the Blake2B hash function for l = 0 . . . 2^m+1/[512/n)] .
Finally compute s := [512/n] disjoint sections of length n bits out of each  B(l) and index them first in order of l and then in their local position within B(l).
Then a valid solution of the Equihash problem is a set of 2^k indexes such that
- all indexes are pairwise distinct,
- for any 1 ≤ i < k  the exclusive or (xor) of all elements referenced by an 2^i+1 elements index block is 0 on the first i · m bits ,
- the exclusive or of all elements indexed by the solution equals 0.
- the indexes are sorted in a way such that for two index blocks with 2^i indexes each the one with the lowest leading element leads first. E.g. I_2·j < I_2·j+1 for all 0 ≤ j ≤ 2^k−1.

Note that this is no full formal description but it will be enough to discuss the characteristics of Equihash. First of all we note that an Equihash problem instance may or may not have a solution. In fact there are on average approximately two solutions for each concrete problem instance. The proof for this is out of scope for this document.

Difficulty of an Equihash Problem

The algorithm behind the computation of an Equihash solution is the Wagner algorithm. The basic idea is to find pairs of bit streams matching on its lowest m bits. The XOR of each such pair will then give a bitstring that is shorter by m bits and is input to the next round. Iterating this process k-1 times will create bitstreams of length 2m that each have 2^k−1 full length ancestors. If two such elements match on the remaining 2m bits and its ancestors are pairwise distinct they will give raise to an Equihash solution.
The matching can be achieved by sorting the elements by their lowest bits in each of the overall k rounds. The complexity of sorting is quasi-linear in is the number of elements to be sorted, which equals 2^m+1 in the beginning. It can be shown that the expected number of pairs generated in each round is again 2^m+1 except for the last round where we only expect two outputs because we match elements on twice the number of bits.
The following table lists the number of elements to be generated for the most frequently used Equihash instances.

- MinexCoin	n=96/k=5/m=16/Elements 2^17/Memory use +-7Mb
- ZCash	n=200/k=9/m=20/Elements 2^21/Memory use +-200Mb
- AION n=2106/k=9/m=21/Elements 2^22/Memory use +-600Mb
- BitcoinZ n=144/k=5/m=24/Elements 2^25/Memory use +-1600Mb
- Zero n=192/k=7/m=24/Elements 2^25/Memory use +-3000Mb
- GRIMM n=150/k=5/m=25/Elements 2^26/Memory use +-3800Mb

We see that the memory use as well as the number of elements to be processed is dominated by the number of collision bits m, which is a better indicator for the algorithms complexity then the bitlength of the elements generated n. In the following section we will discuss the advantages FPGAs and ASICs have over GPUs when computing Equihash solutions and our proposal to reduce their efficiency margin.

Analysis of ASIC and FPGA advantages over GPUs for performing Equihash

Current ASIC implementations of the Equihash 200/9 algorithm make use of large amounts of on chip memory offering a low latency and high memory bandwidth. For example the Bitmain Z9 Mini features 144 Mbyte of on Chip memory which is close to the theoretic minimal memory for performing the algorithm on a CPU. Given the performance of the ASIC the used bandwidth exceeds 5 Tbytes per second.
In contrast an efficient GPU implementation will usually use a larger memory footprint because the off chip memory controllers benefit from read and write access that is at least 32bit, better 128 bit aligned. Off chip memory has a bandwidth ranging of about 256 Gbyte/s on medium range GPUs to trice the value on high end GPUs equipped with HBM2 memory.
Beside the advantages of high amount of on chip memory and better packed access patters an ASIC as well as an FPGA can trade time spend for parallelizeable compute operations by chip space and power consumption by assigning more circuits to the task. For Equihash the fraction offering most potential for this trade is the Blake2B algorithm.
A massively increased performance of the Blake2B algorithm may be beneficial to trade compute power against bandwidth like follows. In the first rounds of the Equihash matching phases less bits then required for performing the full algorithm can be stored and loaded. As soon as the abandoned bits get required for continuing with the algorithm the chip can recover them by computing the hashes again from the indexes carried to this round.
This approach is in particular efficient in the early rounds when the bandwidth required to transfer the indexes is low compared with the transfer of the original workload bits. Also in this early rounds less different blake2b passes have to be used to recover the concrete bits. For GPUs this approach is not an option, because adding blake2b computations increases duration instead of space of the algorithm. Also this operations consume too much time to be hidden when performing memory operations and they would increase power consumption as well.

Applicability towards Equihash 150/5

In the previous section we defined three potential benefits of ASICs compared to GPUs that are large on chip memory areas, a better packing and coalescing of off-chip memory operations and time-space algorithm trade-off.
Regarding the first issue we have strong confidence that a specialized chip for Equihash 150/5 will not take this exact approach due to its increased memory footprint. When completely computed the output of the first round is (26 + 150) * 2^26 bits and thus approx 1.4 Gbytes. We claim that with growing index tables of matched elements this is a sharp lower bound. This even applies when using the trick described in the time memory trade-off part of the previous section, because even the indexes written in the first 4 rounds compressed to 36 bits per matched element plus the required remaining bits for performing the final matching round requires at least this space.
In practice we even can estimate that the real memory consumption of an efficient implementation is at least twice the size, similar to the ZCash parameters.
Therefore a single chip ASIC holding enough memory to perform all operations at Tbytes per second bandwidth range would be of 10 to 20x the size of the chip to perform ZCashs Equihash 200/9 algorithm on the same manufacturing process. This would increase the cost for producing the chip dramatically because on the same production processes a higher yield can be expected and also larger chips are more costly.
Of cause this approach may and will get feasible in the future with advanced production methods and new technologies regarding fast on chip memory or staking chips with height bandwidth. Never the less the mentioned amount of memory is high enough that the time to market of such new inventions will be longer then our planned PoW review and adjustment period.
The second benefit is of architectural nature with ASICs as well as FPGAs being able to perform memory operations that use bitlength that are not a multiple of 32 more efficiently. Also adding more circuits in the imple- mentation to ensure a better memory coalescing when using external memory chips is exclusive to these chips, while a GPU can improve its memory access patterns only by using software solutions.
We therefore believe this benefit can not be mitigated directly by an algorithm change unless changing the parameters in a way that most memory operations are forced to be in ideal range for GPUs. This is out of scope for Equihash with nowadays capacities.
Anyways we claim that the total effect of this benefit is limited by the capacities of the external memory controller. For the already well tuned Equihash 144/5 parameters it is known that a single run requires approximately 5 Gbytes of memory bandwidth in total. Each run will produce 2 solutions on average. Modern implementations can run up to 60 solutions per second on an unmodified Nvidia GTX 1080. Therefore on this cards about 150 Gbytes/s of the total available 352 Gbyte/s are effectively used. So a specialized chip equipped with the same memory but more efficient memory access patterns may have a gain limited to a factor of about 2.5 if the algorithm behind is forced to write the same data.
This enforcement aligns with the potential space to memory and bandwidth trade-off discussed before. The BEAM & GRIMM project proposes an algorithm change that makes the trade-off more costly in terms of space requirement and power consumption of the resulting chip.
Note that specialized devices that are programmable as GPUs but are reduced to and specialized for the required operations to mine crypt-currencies and offer additional optimizations for memory access still may be able to perform the algorithm 2-3x faster then a GPU equipped with the same mem- ory and that at a potentially lower energy consumption. On the long term preventing such devices from mining the algorithm is not feasible. At the time of writing no such designs are publicly available nor is there a concrete announcement of such, so we assume that the desired head start for GPU mining is given.

GRIMM modification of Equihash 150/5
By the nature of the Equihash 150/5 algorithm it has a blocking rate of 3 in its Blake2b phase. This is that if the original algorithm is modified in a way that in later rounds the Blake2b algorithm has to be performed again, for each hash string we require 3x the computation amount of the initial calculation, because in the first round 3 hash strings of 150 bit length are generated in one computation.
This also applies to the verification of an Equihash 150/5 solution, but is no issue for the verification because the total number of Blake2b runs to verify one solution is 32 while the avergage number of runs for generating one solution exceeds 11184810 that is approx 2^26/32.


We propose to increase the blocking factor to 48 by the following scheme.

Algorithm 2 Let B(l) be the 512 bit string corresponding to the Blake2b hash for input index l and let B(l)_j be the j-th 32 bit component interpreted as 32 bit integer.  Then let B'(l) be the 512 bit string computed like follows:

- c ← 16 · [l/16]
- B'(l)	0 ← 0
- while c≤l do
- B'(l)_j ←	B'(l)_j + B(c)_j for all 0 ≤	j < 16
- c	← c + 1
- end while

Thus in order to compute the modified hash string B' it may be required to know all 15 other hashed in the same group of 16 hash elements. On a GPU this can be cheaply achieved by using the local memory on the device in the initial computation phase. Also on modern GPUs neighbored threads with index only varying on the lowest four bits run in lock steps, so the sharing over the local memory does not introduce new synchronization barriers.
Therefore for performing the algorithm the intended way the slow down by the extra computation of the sums will be negligible. On the other hand when it is intended to run Blake2b later again to recover bits from known indexes this is up to 16 times more costly then before and overall up to 48 times so costly then in the initial round with an average extra cost factor of 24.
By this approach we aim towards forcing the algorithm to follow the same algorithm implementation as done on GPUs or else to use more chipspace and drastically increased power consumption, because performing the Blake2b algorithm is the most power consuming component of Equihash.
Note that also the verification of solutions get more costly by an average factor of eight. But since only few solutions needs to be verified and due to the still high asymmetry of generation effort compared to verification effort the drawback is acceptable. Overall with this modification the verification of an Equihash 150/5 solution can be done at lower average cost as the verification of an Equihash 200/9 solution while the worst case costs are equal.


#### to be continued (Magic paper v.1.1 under development)

#### Resources

https://github.com/mimblewimble/docs/wiki/MimbleWimble-Origin

https://download.wpsoftware.net/bitcoin/wizardry/mimblewimble.pdf

https://github.com/mimblewimble/grin/blob/master/doc/intro.md

http://diyhpl.us/wiki/transcripts/sf-bitcoin-meetup/2016-11-21-mimblewimble/

https://tlu.tarilabs.com

https://github.com/BeamMW/beam/wiki/Beam-Equihash-specification
