# Crypto Final Project – Meet-in-the-Middle Attack, DES Modes, Secure Messaging Tool

## **Overview**

This project showcases a deep dive into applied cryptography using Python. It includes a complete implementation and analysis of:

- **Meet-in-the-Middle Attack** on 2-DES  
- **ECB vs CBC Encryption** on image data  
- **Secure Message Exchange** using RSA, DES, and Digital Signatures  
- **Implementation of Square and Multiply Algorithm** for modular exponentiation in RSA

---

## **Part 1: Meet-in-the-Middle (MITM) Attack on 2-DES**

### **Attack Summary**

2-DES applies DES encryption twice using keys `K1` and `K2`. MITM reduces the brute-force complexity from 2^112 to roughly 2^57 by matching intermediate encryption values.

**Key Templates:**

- `K1 = AB13**25F5231589`  
- `K2 = F52315**AB132525`  

256 possible values per unknown (** = 8 bits).

**Attack Steps:**

1. **Encrypt** known plaintext with all 256 K1 candidates.
2. **Decrypt** known ciphertext with all 256 K2 candidates.
3. **Compare** intermediate results to find matches.

### **Recovered Keys**

```text
Pair 1: K1 = AB138625F5231589, K2 = F5231567AB132525  
Pair 2: K1 = AB13AC25F5231589, K2 = F5231578AB132525  
Pair 3: K1 = AB13FE25F5231589, K2 = F52315ABAB132525  
Pair 4: K1 = AB13DF25F5231589, K2 = F52315CDAB132525  
````

### **Code Highlights**

MITM implementation includes:

* `mitm_attack_multiple_pairs()`
* `two_des_encrypt()` and `two_des_decrypt()`
* Custom DES rounds and permutation logic

All encryption steps follow the DES structure, including:

* Initial and Final Permutations
* 16 Feistel Rounds
* S-box substitution
* Round Key generation

---

## **Part 2: ECB vs CBC Mode on Image Encryption**

### **Key Concepts**

* **ECB** mode encrypts blocks independently. Patterns leak.
* **CBC** mode chains blocks using XOR and an IV. No visible patterns.

### **Testing Steps**

1. Load and flatten a grayscale image.
2. Encrypt using `encrypt_ecb()` and `encrypt_cbc()`.
3. Save encrypted images as `.jpg` using Pillow and numpy.

### **Observations**

* **ECB Encrypted Image**: Patterns are visible.
* **CBC Encrypted Image**: Appears completely random.

### **Code Snippet: ECB Mode**

```python
for i in range(0, len(image_data), block_size):
    block = image_data[i:i + block_size]
    encrypted_block = des_encrypt(block, key)
```

### **Why CBC is Superior**

* Introduces randomness via IV
* Obscures plaintext structure
* Chaining enhances tamper-resistance

---

## **Part 3: Secure Message Exchange (RSA + DES)**

### **What It Does**

* Uses **RSA** for secure DES key exchange
* Uses **DES (CBC)** for encrypting files and messages
* Implements **Digital Signature** for message authenticity

### **Key Features**

* **RSA Key Generation**
* **Shared DES Key Generation**
* **RSA Key Encryption/Decryption**
* **File and Message Encryption with DES**
* **Digital Signature Creation and Verification**

### **DES Key Example**

1110010111110111011010011101110111101010101000000110010000101100
```

### **Used Algorithms**

* **Square and Multiply** for fast RSA exponentiation
* **Miller-Rabin** test for primality
* **CTS Padding** for image encryption
* **SHA-1** for digital signature hashing

---

## **Part 4: Square and Multiply Algorithm**

### **Purpose**

Efficiently calculates modular exponentiation:

* `ciphertext = plaintext ^ e mod n`
* `decrypted = ciphertext ^ d mod n`

### **How It Works**

* Reads binary bits of exponent
* Squares for `0`, squares and multiplies for `1`
* Runs in `O(log b)` instead of `O(b)`

### **In This Project**

Used for:

* RSA Encryption: `square_and_multiply(shared_key_int, e, n)`
* RSA Decryption: `square_and_multiply(ciphertext, d, n)`

---

## **Screenshots**

* `CBC_crypto.jpg`
* `ECB_crypto.jpg`
* `CBC_topsecret.jpg`
* `ECB_topsecret.jpg`
* `CBC_images.jpg`
* `ECB_images.jpg`
* `CBC_TUX.jpg`
* `ECB_TUX.jpg`

---

## **Lessons Learned**

* Hands-on DES and RSA implementation deepened understanding of real-world cryptography.
* Found ECB's flaws and CBC's strength in visual encryption.
* Mastered Square and Multiply for performance-critical crypto.
* Learned how digital signatures and key exchange protocols interact.
* Gained insight into secure system design, modular structure, and cryptographic layering.

---

## **Technologies Used**

* Python 3
* Numpy, Pillow
* Custom DES Implementation
* Modular RSA Logic
* ECB and CBC encryption modes
* SHA-1 hashing

---

## **References**

* Crypto-it.net: MITM Attack
* Wikipedia: Block Cipher Modes
* GeeksforGeeks: DES, CBC, RSA
* PracticalNetworking.net: Square and Multiply
* RFC1423: DES-CBC
* Xilinx Docs: CBC Internals
* Stanford Crypto Notes

---

## **Author**

Farouq Hassan
HTU – Blockchain and Cybersecurity
Spring 2023–2024
Supervisor: Sami AlMashaqbeh
