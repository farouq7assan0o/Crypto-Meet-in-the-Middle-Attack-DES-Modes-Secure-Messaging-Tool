Here is a clear and professional version of your README for GitHub, aligned with your instructions:

---

# Crypto Final Project – Meet-in-the-Middle Attack, DES Modes, Secure Messaging Tool

## Overview

This Python-based cryptography project explores applied techniques in secure communications, encryption algorithms, and cryptanalysis. It includes implementations of:

* Meet-in-the-Middle attack on 2-DES
* Comparison of ECB and CBC encryption modes on images
* Secure message exchange using RSA, DES, and digital signatures
* Efficient RSA modular exponentiation with Square and Multiply

## Part 1: Meet-in-the-Middle (MITM) Attack on 2-DES

This section demonstrates how the MITM technique significantly reduces the effective keyspace in 2-DES from 2^112 to 2^57 using known plaintext-ciphertext pairs.

Keyspace structure:

* K1 = AB13\*\*25F5231589
* K2 = F52315\*\*AB132525

Process:

1. Encrypt known plaintext with all 256 possible K1 candidates
2. Decrypt known ciphertext with all 256 possible K2 candidates
3. Match intermediate states to identify valid key pairs

Recovered key pairs show the success of the attack.

Key methods:

* mitm\_attack\_multiple\_pairs()
* two\_des\_encrypt() and two\_des\_decrypt()
* Custom DES with Feistel rounds, S-boxes, and permutation logic

## Part 2: ECB vs CBC Mode on Image Encryption

The project compares visual security differences between ECB and CBC modes using encrypted grayscale images.

Steps:

* Load and flatten image
* Encrypt with DES in ECB and CBC modes
* Save results as encrypted image files

Findings:

* ECB mode reveals patterns
* CBC mode obscures all visual structure using IV chaining

This section emphasizes the importance of choosing proper encryption modes in data security.

## Part 3: Secure Message Exchange with RSA and DES

This module builds a secure messaging protocol using hybrid encryption.

Features:

* RSA key generation and management
* Secure DES key sharing via RSA
* DES CBC encryption for messages and files
* Digital signature using SHA-1 for authenticity and integrity

Algorithms used:

* Square and Multiply for efficient modular exponentiation
* Miller-Rabin for primality testing
* SHA-1 hashing for signatures

DES keys and encrypted content demonstrate working examples of secure communication.

## Part 4: Square and Multiply Algorithm

Implements fast modular exponentiation used in RSA operations.

Principles:

* Reads exponent in binary
* Squares if bit is 0, squares and multiplies if bit is 1
* Runs in logarithmic time relative to exponent length

Functions:

* square\_and\_multiply(plaintext, e, n) for encryption
* square\_and\_multiply(ciphertext, d, n) for decryption

## Screenshots

Demonstrates output of encrypted images:

* CBC\_crypto.jpg vs ECB\_crypto.jpg
* CBC\_TUX.jpg vs ECB\_TUX.jpg
* CBC\_images.jpg vs ECB\_images.jpg
* CBC\_topsecret.jpg vs ECB\_topsecret.jpg

## Lessons Learned

* Understood how 2-DES can be broken with meet-in-the-middle attacks
* Gained practical insight into the weaknesses of ECB mode
* Developed a secure communication tool using RSA and DES
* Learned digital signature verification processes
* Improved performance using Square and Multiply in cryptographic operations
* Applied layered cryptography concepts and modular design

## Technologies Used

* Python 3
* Numpy, Pillow
* Custom DES encryption
* RSA key generation and encryption
* ECB and CBC encryption modes
* SHA-1 hashing

## References

* Crypto-it.net: MITM Attack
* Wikipedia: Block Cipher Modes
* GeeksforGeeks: DES, CBC, RSA
* PracticalNetworking.net: Square and Multiply
* RFC1423: DES-CBC
* Xilinx Docs: CBC Internals
* Stanford Cryptography Notes

## Author

Farouq Hassan
HTU – Blockchain and Cybersecurity
Spring 2023–2024
Supervisor: Sami AlMashaqbeh

---

Let me know if you want a tailored summary of what you learned to include on your CV.
