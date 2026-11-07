# Caesar Cipher Brute-Force Decryptor

A Python-based cryptanalysis utility designed to decrypt rotational substitution ciphers (Caesar Cipher) using an automated brute-force attack combined with Indonesian linguistic frequency heuristics.

## Overview

The Caesar cipher is an elementary substitution cipher where each letter in the plaintext is shifted by a fixed number of positions down the alphabet. This utility systematically evaluates all 25 possible shift keys, scoring the resulting plaintexts against an Indonesian dictionary vocabulary list to identify the most probable decrypted message without requiring the encryption key.

## Mathematical Formulation

For an English alphabet consisting of 26 characters ($A = \{0, 1, \dots, 25\}$), the decryption function for ciphertext character $c$ and shift key $k \in [1, 25]$ is defined as:

$$D_k(c) = (c - k) \pmod{26}$$

The algorithm computes $D_k(c)$ across all $k \in [1, 25]$ and calculates a fitness score:

$$\text{Score}(k) = \sum_{w \in W} \mathbb{I}(w \subseteq \text{Plaintext}_k)$$

where $W$ is the set of high-frequency Indonesian linguistic tokens.

## Features

- Automated Shift Detection: Analyzes candidate plaintexts and selects the shift with the highest vocabulary match score.
- Fallback Exhaustive Mode: If no dictionary words are detected, all 25 permutations are printed systematically for manual inspection.
- Case and Character Preservation: Maintains uppercase and lowercase casing while preserving numbers, spaces, and punctuation symbols.
- Zero External Dependencies: Implemented strictly using the Python Standard Library.

## Project Structure

```
CaesarChiperDecrypt/
├── BruteForceCaesarChiper.py   # Core decryption and heuristic evaluation script
└── README.md                   # Technical documentation
```

## Requirements

- Python 3.8 or higher
- Standard terminal or command prompt

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/ANTARTICA1/CaesarChiperDecrypt.git
   cd CaesarChiperDecrypt
   ```

2. Execute the script:
   ```bash
   python BruteForceCaesarChiper.py
   ```

3. Provide the encrypted text when prompted:
   ```text
   Masukkan teks terenkripsi: khoor
   ```

4. The program will output the identified optimal shift key along with the decrypted plaintext, or provide a complete table of all 25 shift variants.

## Author

Anak Agung Ngurah Krisna Artha Wibawa ([ANTARTICA1](https://github.com/ANTARTICA1))

## License

This project is licensed under the MIT License.