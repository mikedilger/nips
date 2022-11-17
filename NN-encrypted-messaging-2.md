NIP-NN
======

Improved Encrypted Direct Message
---------------------------------

`draft` `optional` `author:mikedilger`

NIP-04 defined a mechanism and event kind providing for encrypted direct messaging.

This NIP enhances the security of encrypted direct messaging by using a HMAC based key derivation function (HKDF) to derive the symmetric AES key. This provides a uniformly random AES key which enhances the security of the encryption.

This NIP proposes using HMAC-SHA256 with the shared secret salted with the random initialization vector to derive the AES-256-CBC key.

### pseudocode

```
shared_secret = ECDH(private_key, public_key)

IV = random_bytes()

aes_key = HMAC-SHA256( binary_concatenate(shared_secret, IV) )

ciphertext = AES-256-CBC(plaintext, aes_key, IV)
```
