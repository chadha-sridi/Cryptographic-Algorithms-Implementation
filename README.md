# Cryptographic Algorithms Implementation

This repository contains Python implementations of three cryptographic algorithms: RSA, ElGamal, and Paillier. Each algorithm utilizes the GMP library for efficient arithmetic operations.

## Algorithms Included

1. **RSA (Rivest-Shamir-Adleman)**
   - RSA is a widely-used asymmetric encryption algorithm.
   - Implementation includes functions for key generation, encryption, decryption, and decryption with Chinese Remainder Theorem (CRT).
   - The GMP library is used for efficient large integer arithmetic.

2. **ElGamal**
   - ElGamal is an asymmetric key encryption algorithm based on the Diffie-Hellman key exchange.
   - Implementation includes functions for key generation, encryption, and decryption.
   - The GMP library is used for efficient large integer arithmetic.

3. **Paillier**
   - Paillier is an asymmetric encryption algorithm with homomorphic properties.
   - Implementation includes functions for key generation, encryption, decryption, and decryption with Chinese Remainder Theorem (CRT).
   - The GMP library is used for efficient large integer arithmetic.

## Usage

1. **RSA**
   - Execute `rsa.py`.
   - Functions available:
     - `get_rsa_keys(size)`: Generates public and private keys with specified bit length.
     - `rsa_encrypt(message, pub_key)`: Encrypts plaintext using public key.
     - `rsa_decrypt(ciphertext, priv_key, pub_key)`: Decrypts ciphertext using private key.
     - `rsa_decrypt_crt(ciphertext, priv_key, pub_key)`: Decrypts ciphertext using Chinese Remainder Theorem.

2. **ElGamal**
   - Execute `elgamal.py`.
   - Functions available:
     - `get_elgamal_keys(size)`: Generates public and private keys with specified bit length.
     - `elgamal_encrypt(message, pub_key)`: Encrypts plaintext using public key.
     - `elgamal_decrypt(ciphertext, K, priv_key, pub_key)`: Decrypts ciphertext using private key.

3. **Paillier**
   - Execute `paillier.py`.
   - Functions available:
     - `get_paillier_keys(size)`: Generates public and private keys with specified bit length.
     - `paillier_encrypt(message, pub_key)`: Encrypts plaintext using public key.
     - `paillier_decrypt(ciphertext, priv_key, pub_key)`: Decrypts ciphertext using private key.
     - `paillier_decrypt_CRT(ciphertext, priv_key, pub_key)`: Decrypts ciphertext using Chinese Remainder Theorem.

## Mathematical Formulas

1. **RSA**
   - Key Generation:
     - Choose two distinct prime numbers, p and q.
     - Compute n = p * q and φ(n) = (p-1)(q-1).
     - Select e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1.
     - Compute d such that (d * e) mod φ(n) = 1.
     - Public key: (n, e), Private key: (n, d).
   - Encryption: c = m^e mod n
   - Decryption: m = c^d mod n
   - CRT Decryption: m = (m_p * q_inv * p + m_q * p_inv * q) mod n, where m_p = c^d mod p, m_q = c^d mod q, q_inv is the modular inverse of q mod p, and p_inv is the modular inverse of p mod q.

2. **ElGamal**
   - Key Generation:
     - Select a large prime number p.
     - Choose an integer g such that g is a primitive root modulo p.
     - Choose a private key x, 1 < x < p-1.
     - Compute y = g^x mod p.
     - Public key: (p, g, y), Private key: x.
   - Encryption: Choose a random integer k, 1 < k < p-1.
     - Compute c1 = g^k mod p, c2 = (y^k * m) mod p.
   - Decryption: m = (c2 * (c1^(-x))) mod p.

3. **Paillier**
   - Key Generation:
     - Choose two large prime numbers p and q.
     - Compute n = p * q.
     - Select a random integer g such that gcd((g-1), n^2) = 1.
     - Public key: (n, g), Private key: (λ, μ), where λ = lcm(p-1, q-1) and μ = L(g^λ mod n^2)^(-1) mod n, where L(x) = (x-1) / n.
   - Encryption: Choose a plaintext m, 0 <= m < n.
     - Choose a random integer r, 0 <= r < n.
     - Compute ciphertext: c = (g^m * r^n) mod n^2.
   - Decryption: Compute plaintext: m = L(c^λ mod n^2) * μ mod n.

## Requirements

- Python 3.x
- GMP library (install using `pip install gmpy2`)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

