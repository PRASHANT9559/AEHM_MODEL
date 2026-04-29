# Cryptography — Complete Specification

## Overview

This document provides comprehensive coverage of cryptographic attacks, implementations, and CTF-oriented cryptography challenges for the AEHM dataset.

**Target examples:** 3M
**Primary focus:** Classical attacks, modern crypto attacks, CTF crypto

---

## Table of Contents

1. [Classical Cryptography](#1-classical-cryptography)
2. [Modern Cryptographic Attacks](#2-modern-cryptographic-attacks)
3. [CTF Cryptography](#3-ctf-cryptography)
4. [Cryptographic Implementations](#4-cryptographic-implementations)
5. [Post-Quantum Cryptography](#5-post-quantum-cryptography)

---

## 1. Classical Cryptography

### 1.1 Substitution Ciphers
- Caesar cipher — frequency analysis
- ROT13 — simple shift
- Atbash cipher — alphabet reversal
- Affine cipher — linear transformation
- Vigenère cipher — Kasiski examination
- Beaufort cipher — variant of Vigenère
- Autokey cipher — self-keying
- Running key cipher — book cipher
- Gronsfeld cipher — numeric key
- Porta cipher — digraphic substitution

### 1.2 Transposition Ciphers
- Rail fence cipher — zigzag pattern
- Columnar transposition — keyword-based
- Route cipher — path-based
- Scytale cipher — Spartan method
- Myszkowski transposition — periodic key
- Double transposition — double columnar
- Grille cipher — grid-based
- Permutation cipher — block-based
- Fragmented transposition
- Complex transposition

### 1.3 Polyalphabetic Ciphers
- Vigenère cipher — full analysis
- Beaufort cipher — reciprocal
- Variant Beaufort — autokey variant
- Gronsfeld cipher — numeric
- Running key cipher — plaintext key
- Autokey cipher — self-keying
- Chaocipher — complex polyalphabetic
- Enigma machine — rotor-based
- Lorenz cipher — stream cipher
- SIGABA — rotor machine

### 1.4 Classical Analysis Techniques
- Frequency analysis — letter frequency
- Index of coincidence — polyalphabetic detection
- Kasiski examination — key length
- Friedman test — key length estimation
- Known plaintext attacks
- Chosen plaintext attacks
- Ciphertext-only attacks
- Brute force attacks
- Dictionary attacks
- Pattern analysis

---

## 2. Modern Cryptographic Attacks

### 2.1 Block Cipher Attacks
- ECB mode — block pattern attack with images
- CBC bit flipping attack — full example with steps
- CBC padding oracle attack — PKCS#7 full exploitation
- CBC-MAC forgery
- CTR mode attacks
- CFB mode attacks
- OFB mode attacks
- Block cipher collision attacks
- Block cipher related-key attacks
- Block cipher slide attacks

### 2.2 Stream Cipher Attacks
- RC4 attacks — bias in keystream
- RC4 nonce reuse
- RC4 key scheduling attacks
- ChaCha20 attacks
- Salsa20 attacks
- Stream cipher keystream reuse
- Stream cipher key recovery
- Stream cipher state recovery
- Stream cipher distinguishing attacks
- Stream cipher forgery attacks

### 2.3 Hash Function Attacks
- Length extension attack — SHA1/SHA256/MD5
- Hash collision — MD5, SHA1 real examples
- Birthday attack — collision finding
- Multicollision attack
- Second preimage attack
- Preimage attack
- Length extension countermeasures
- Hash function construction
- Merkle-Damgård construction
- Sponge construction

### 2.4 Protocol Attacks
- BEAST attack — TLS 1.0
- POODLE attack — SSLv3
- CRIME attack — compression + encryption
- BREACH attack — HTTP compression
- Lucky 13 attack — CBC timing
- RC4 bias attacks
- Sweet32 attack — 64-bit block ciphers
- DROWN attack — SSLv2
- Logjam attack — Diffie-Hellman
- FREAK attack — export-grade RSA

### 2.5 Public Key Attacks
- Bleichenbacher attack — RSA PKCS#1 v1.5
- Timing attack — non-constant-time comparison
- Padding oracle — RSA
- Coppersmith's attack — small roots
- Wiener's attack — small private exponent
- Boneh-Durfee attack — small private exponent
- Hastad's broadcast attack — same message
- Related message attack
- Common modulus attack
- Lattice attacks on RSA

### 2.6 Elliptic Curve Attacks
- Invalid curve attack
- Small subgroup attack
- Twist attack
- Pollard's rho — discrete logarithm
- Baby-step giant-step — discrete logarithm
- Pohlig-Hellman — discrete logarithm
- MOV attack — elliptic curve
- Smart's attack — anomalous curves
- Side-channel attacks
- Fault attacks
- Implementation attacks

### 2.7 Side-Channel Attacks
- Timing attacks
- Power analysis
- Electromagnetic analysis
- Acoustic cryptanalysis
- Cache timing attacks
- Differential power analysis
- Simple power analysis
- Template attacks
- Correlation power analysis
- Fault injection attacks

### 2.8 Implementation Attacks
- Reused nonces in AES-GCM — key recovery
- Weak RSA — small e, small d, common modulus
- ECDSA nonce reuse — private key recovery (k reuse)
- DSA nonce reuse — private key recovery
- RSA CRT fault attacks
- AES cache attacks
- Constant-time implementation issues
- Branch prediction attacks
- Speculative execution attacks
- Microarchitectural attacks

---

## 3. CTF Cryptography

### 3.1 RSA Challenges
- RSA factoring — small primes, Fermat factorization
- RSA small exponent attacks
- RSA common modulus attacks
- RSA broadcast attacks
- RSA padding oracle attacks
- RSA timing attacks
- RSA CRT attacks
- RSA partial key exposure
- RSA related key attacks
- RSA implementation attacks

### 3.2 Elliptic Curve Challenges
- Elliptic curve discrete logarithm
- Invalid curve attack
- Small subgroup attack
- Twist attack
- Smart's attack
- MOV attack
- Point compression attacks
- Curve parameter attacks
- Scalar multiplication attacks
- Implementation attacks

### 3.3 Symmetric Cipher Challenges
- AES key schedule reversal
- AES known-plaintext attacks
- AES chosen-plaintext attacks
- AES side-channel attacks
- AES implementation attacks
- DES key schedule reversal
- DES brute force
- 3DES meet-in-the-middle
- Block cipher mode attacks
- Stream cipher attacks

### 3.4 Hash Challenges
- Hash collision finding
- Hash length extension
- Hash preimage attacks
- Hash second preimage attacks
- Hash construction attacks
- Merkle-Damgård attacks
- Sponge construction attacks
- Hash function analysis
- Hash function design
- Hash function implementation

### 3.5 Encoding vs Encryption
- Base64 — encoding, not encryption
- Hex — encoding, not encryption
- Rot13 — encoding, not encryption
- Morse code — encoding, not encryption
- URL encoding — encoding, not encryption
- HTML encoding — encoding, not encryption
- Unicode encoding — encoding, not encryption
- Punycode — encoding, not encryption
- Quoted-printable — encoding, not encryption
- UUencoding — encoding, not encryption

### 3.6 Custom Cryptography
- Custom PRNG analysis and prediction
- Custom stream cipher analysis
- Custom block cipher analysis
- Custom hash function analysis
- Custom MAC function analysis
- Custom key derivation function
- Custom encryption scheme
- Custom signature scheme
- Custom protocol analysis
- Custom implementation analysis

### 3.7 One-Time Pad
- One-time pad misuse
- One-time pad key reuse
- One-time pad key prediction
- One-time pad key recovery
- One-time pad implementation attacks
- One-time pad stream cipher confusion
- One-time pad XOR analysis
- One-time pad frequency analysis
- One-time pad known-plaintext attacks
- One-time pad chosen-plaintext attacks

### 3.8 LFSR-Based Ciphers
- LFSR analysis
- LFSR state recovery
- LFSR polynomial reconstruction
- LFSR clock control attacks
- LFSR combination attacks
- LFSR correlation attacks
- LFSR algebraic attacks
- LFSR fast correlation attacks
- LFSR distinguishing attacks
- LFSR implementation attacks

---

## 4. Cryptographic Implementations

### 4.1 Symmetric Key Algorithms
- AES implementation
- DES implementation
- 3DES implementation
- Blowfish implementation
- Twofish implementation
- Serpent implementation
- Camellia implementation
- CAST-128 implementation
- IDEA implementation
- RC5 implementation

### 4.2 Asymmetric Key Algorithms
- RSA implementation
- DSA implementation
- ECDSA implementation
- EdDSA implementation
- ElGamal implementation
- Diffie-Hellman implementation
- Elliptic Curve Diffie-Hellman
- Paillier encryption
- Rabin encryption
- NTRU encryption

### 4.3 Hash Functions
- MD5 implementation
- SHA-1 implementation
- SHA-256 implementation
- SHA-512 implementation
- SHA-3 implementation
- BLAKE2 implementation
- RIPEMD-160 implementation
- Whirlpool implementation
- Tiger implementation
- HMAC implementation

### 4.4 Key Derivation Functions
- PBKDF2 implementation
- bcrypt implementation
- scrypt implementation
- Argon2 implementation
- HKDF implementation
- TLS PRF implementation
- SSH KDF implementation
- IPsec KDF implementation
- WPA KDF implementation
- Custom KDF implementation

### 4.5 Random Number Generators
- /dev/random
- /dev/urandom
- CryptGenRandom
- getrandom
- Yarrow
- Fortuna
- ChaCha20 RNG
- AES-CTR DRBG
- Hash DRBG
- HMAC DRBG

---

## 5. Post-Quantum Cryptography

### 5.1 Lattice-Based Cryptography
- LWE-based encryption
- LWE-based signatures
- Ring-LWE cryptography
- Module-LWE cryptography
- NTRU encryption
- NTRU signatures
- Lattice-based key exchange
- Lattice-based KEM
- Lattice-based signatures
- Lattice-based FHE

### 5.2 Code-Based Cryptography
- McEliece encryption
- Niederreiter encryption
- Code-based signatures
- QC-MDPC
- ROLLO
- RQC
- BIKE
- Classic McEliece
- Syndrome decoding
- Goppa codes

### 5.3 Multivariate Cryptography
- Rainbow signatures
- GeMSS signatures
- LUOV signatures
- MQDSS signatures
- Multivariate encryption
- Oil and Vinegar
- HFE
- Hidden Field Equations
- Multivariate KEM
- Multivariate signatures

### 5.4 Hash-Based Cryptography
- Merkle signature scheme
- XMSS
- LMS
- SPHINCS+
- SPHINCS+
- Hash-based signatures
- One-time signatures
- Few-time signatures
- Stateful hash signatures
- Stateless hash signatures

### 5.5 Isogeny-Based Cryptography
- SIKE
- CSIDH
- SQISign
- SIDH
- Supersingular isogeny
- Elliptic curve isogeny
- Isogeny-based KEM
- Isogeny-based signatures
- Isogeny-based key exchange

### 5.6 Other Post-Quantum Approaches
- Symmetric key quantum resistance
- Sponge-based quantum resistance
- Large key sizes
- Quantum-resistant protocols
- Hybrid cryptography
- Transition strategies
- Migration strategies
- Implementation challenges
- Performance considerations
- Standardization efforts

---

*End of Cryptography Specification*
