# Lab-Exercise---8---Implement-the-AES-Encryption-and-decryption
 
Aim:

To use Advanced Encryption Standard(AES) Algorithm for a practical application like URL Encryption.

Procedure:

AES is based on a design principle known as a substitution-permutation
AES does not use a Feistel network like DES, it uses variant of Rijndael
It has a fixed block size of 128 bits and a key size of 128, 192, or 256 bits.
AES operates on a 4 x 4 column-major order array of bytes termed the state.

Program:

```
import os
import base64
from cryptography.hazmat.primitives.ciphers.aead import AESGCM
def aes_encrypt(plaintext: str, key: bytes) -> str:
    nonce = os.urandom(12)  
    aesgcm = AESGCM(key)
    ciphertext = aesgcm.encrypt(nonce, plaintext.encode(), None)
    return base64.b64encode(nonce + ciphertext).decode()
def aes_decrypt(token: str, key: bytes) -> str:
    raw = base64.b64decode(token)
    nonce, ciphertext = raw[:12], raw[12:]
    aesgcm = AESGCM(key)
    return aesgcm.decrypt(nonce, ciphertext, None).decode()
key = AESGCM.generate_key(bit_length=256)
message = "Hello AES Encryption!"
print("Plain Text:", message)
encrypted = aes_encrypt(message, key)
print("Encrypted:", encrypted)
decrypted = aes_decrypt(encrypted, key)
print("Decrypted:", decrypted)
```

Output:

 <img width="2928" height="322" alt="output 08" src="https://github.com/user-attachments/assets/ed1ae952-7cd9-4f08-8431-2613acc88338" />

Result:

Thus,the advanced encryption standard(AES) Algorithm for a practical application like URL Encryption are executed successfully.
