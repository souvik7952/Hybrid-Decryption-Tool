<h1>Hybrid Decryption Tool</h1>

<p>
Hybrid Decryption Tool is a secure browser-based utility designed to decrypt data protected using a hybrid cryptography architecture. The application combines RSA-OAEP asymmetric decryption, PBKDF2 key derivation with SHA-256, and AES-256-CBC symmetric decryption to securely restore encrypted payloads back to their original plaintext form.
</p>

<p>
The tool is specifically designed to process encrypted request packets containing a combined encrypted payload (part1) and an RSA-encrypted AES secret key (part2). All cryptographic operations are executed entirely within the browser using the Web Crypto API, ensuring that sensitive information, private keys, encrypted payloads, and decrypted data never leave the user's device.
</p>

<h2>Decryption Workflow</h2>

<ol>
<li>The user provides the encrypted <strong>part1</strong> value.</li>
<li>The user provides the encrypted <strong>part2</strong> value.</li>
<li>The user provides the RSA Private Key in PEM format.</li>
<li>The tool decrypts <strong>part2</strong> using RSA-OAEP with SHA-256 to recover the original AES Secret Key.</li>
<li>The first 32 hexadecimal characters of <strong>part1</strong> are extracted as the Salt.</li>
<li>The next 32 hexadecimal characters are extracted as the Initialization Vector (IV).</li>
<li>The remaining portion of <strong>part1</strong> is extracted as the Base64 encoded AES Ciphertext.</li>
<li>The recovered AES Secret Key and extracted Salt are processed using PBKDF2 with SHA-256 and 120,000 iterations to derive the strengthened AES-256 decryption key.</li>
<li>The Base64 Ciphertext is decoded.</li>
<li>The ciphertext is decrypted using AES-256-CBC with the derived key and extracted IV.</li>
<li>The original plaintext or JSON payload is restored and displayed to the user.</li>
</ol>

<h2>Supported Encrypted Packet Format</h2>

<pre>
{
  "part1": "Salt + IV + Base64CipherText",
  "part2": "RSAEncryptedAESKey"
}
</pre>

<p>
Where:
</p>

<ul>
<li><strong>Salt:</strong> First 32 hexadecimal characters of part1</li>
<li><strong>IV:</strong> Next 32 hexadecimal characters of part1</li>
<li><strong>Ciphertext:</strong> Remaining Base64 encoded encrypted payload</li>
<li><strong>part2:</strong> RSA-OAEP encrypted AES Secret Key</li>
</ul>

<h2>Features</h2>

<ul>
<li>Decrypt Hybrid Encrypted Payloads</li>
<li>RSA-OAEP SHA-256 Private Key Decryption</li>
<li>PBKDF2 Key Derivation with SHA-256</li>
<li>120,000 PBKDF2 Iterations</li>
<li>AES-256-CBC Payload Decryption</li>
<li>Automatic Salt Extraction</li>
<li>Automatic IV Extraction</li>
<li>Automatic Ciphertext Extraction</li>
<li>JSON Beautification Support</li>
<li>Plain Text Output Viewer</li>
<li>Copy Output Functionality</li>
<li>Download Decrypted Data</li>
<li>Advanced Debug Information Panel</li>
<li>Responsive Modern User Interface</li>
<li>Fully Offline Browser Operation</li>
<li>No Server Communication</li>
</ul>

<h2>Advanced Debug Information</h2>

<p>
The application includes an optional advanced diagnostics section that provides visibility into the internal decryption process. This section may display:
</p>

<ul>
<li>Extracted Salt</li>
<li>Extracted Initialization Vector (IV)</li>
<li>Extracted Ciphertext</li>
<li>RSA Decrypted AES Secret Key</li>
<li>PBKDF2 Derived Key Information</li>
<li>Decryption Status</li>
<li>Execution Time</li>
<li>Error Logs and Validation Details</li>
</ul>

<h2>Security Information</h2>

<p>
All decryption operations occur entirely within the user's browser. No encrypted data, decrypted content, private keys, salts, initialization vectors, or cryptographic materials are transmitted, stored, logged, or shared with any external system. The application is intended for authorized testing, debugging, troubleshooting, and secure data processing workflows.
</p>

<h2>Technical Specifications</h2>

<ul>
<li><strong>RSA Algorithm:</strong> RSA-OAEP</li>
<li><strong>RSA Hash:</strong> SHA-256</li>
<li><strong>Key Derivation Function:</strong> PBKDF2</li>
<li><strong>PBKDF2 Hash:</strong> SHA-256</li>
<li><strong>PBKDF2 Iterations:</strong> 120,000</li>
<li><strong>AES Algorithm:</strong> AES-256-CBC</li>
<li><strong>Salt Length:</strong> 16 Bytes (32 Hex Characters)</li>
<li><strong>IV Length:</strong> 16 Bytes (32 Hex Characters)</li>
<li><strong>Ciphertext Encoding:</strong> Base64</li>
<li><strong>Salt Encoding:</strong> Hexadecimal</li>
<li><strong>IV Encoding:</strong> Hexadecimal</li>
<li><strong>Execution Environment:</strong> Browser Only</li>
<li><strong>Crypto Engine:</strong> Web Crypto API</li>
</ul>

<h2>Privacy Notice</h2>

<p>
This tool is designed with privacy and security in mind. All cryptographic operations are performed locally on the user's device. No network requests are required for encryption or decryption, ensuring complete control over sensitive data and cryptographic keys.
</p>
