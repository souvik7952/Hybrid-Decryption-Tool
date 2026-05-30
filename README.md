# Hybrid-Decryption-Tool
Hybrid Decryption Tool securely decrypts hybrid-encrypted payloads using RSA-OAEP, PBKDF2 (SHA-256), and AES-256-CBC. It extracts Salt, IV, and Ciphertext from the encrypted packet, restores the AES key using an RSA private key, and decrypts data locally in the browser with no server communication.
