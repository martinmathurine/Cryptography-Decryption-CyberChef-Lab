# Cryptography-Decryption-CyberChef-Lab

<h2>Introduction</h2>
This lab involved decrypting a base64-encoded binary file to recover its plaintext content. This write-up outlines the step-by-step process used to identify the encryption key, decrypt the data, and discusses relevant cryptographic principles and tooling.

Modern cryptography is built on five key principles of information assurance:
- Availability: Ensuring data is accessible to authorised users.
- Confidentiality: Ensuring only the intended recipient can view sensitive data.
- VIntegrityerifying data hasn’t been altered in transit.
- Verifying: data hasn’t been altered in transit.
- Non-repudiation: Providing proof of delivery and receipt.
- Authentication: Validating user identity before granting access. [2]

Cryptography secures data through encryption, transforming plaintext into ciphertext, and decryption, which restores it using a key. These processes protect both stored and transmitted data. Cryptanalysis refers to techniques for breaking encryption without knowing the algorithm or key. Together, cryptography and cryptanalysis form the broader field of cryptology. [1]

<h2>Summary</h2>
The purpose of this report is to draw on a variety of cryptographic concepts whilst appreciating and discussing the significance of some of the techniques used to decrypt the message’s ciphertext within the encrypted file.

<h2>Decryption Methodology</h2>
An unauthorised entity intercepting an encrypted message must deduce both the cipher used and the key applied—this complexity underpins the strength of encryption as a security control [3]. In this lab, it was determined that the file was Base64 encoded and encrypted using an 8-bit key.

<h3>Base64 Decoding:</h3>
Base64 is an encoding scheme that maps 6-bit input blocks to 8-bit ASCII characters [A-Za-z0-9+/], producing printable output [1]. In this lab, Base64 encoding was used to convert binary data into ASCII text, ensuring the ciphertext remains unintelligible while maintaining data integrity during transmission. The decoder rejects any characters outside the expected ASCII set, reinforcing reliability [4].

<h3>Comparison of Decryption Approaches:</h3>
Assuming English plaintext, one viable method is frequency analysis, which compares letter frequencies in the ciphertext against known English language statistics to infer the most likely plaintext characters [5]. This can be particularly useful for repeated characters or common bigrams. XOR analysis can also help identify likely key positions by comparing known plaintext patterns to cipher output [11].

Another strategy is a dictionary attack, where possible plaintext-ciphertext pairs are precomputed. This is effective against short key lengths, such as the 8-bit key used in this lab. A third method, brute force, involves systematically trying every possible key. While time-intensive, it is often successful for smaller key spaces, and may be combined with frequency or statistical analysis to improve efficiency.

<h3>Symmetric Encryption:</h3>
Symmetric encryption uses a single shared key to both encrypt and decrypt data [1]. In this lab, the encrypted file required the correct key to reveal the plaintext. Key components of a symmetric system include: the plaintext, encryption algorithm, secret key, ciphertext, and a corresponding decryption algorithm.

Well-known symmetric ciphers include:
- RC4: A simple stream cipher used in SSL/TLS, now deprecated due to vulnerabilities [8].
- DES: A 64-bit block cipher with a 56-bit key, broken in ~84 days in 1997 via brute force [7].
- AES: The modern standard, supporting 128-, 192-, and 256-bit keys with strong resistance to brute force [6][7].

<h3>Steps – How the Ciphertext was Decrypted:</h3>
Initial attempts involved manual analysis and use of online tools such as the dcode.fr frequency analyser [9]. Although this method offered theoretical value, results were inconsistent and did not yield intelligible output. The process of manually XORing outputs proved inefficient, leading to the adoption of a more effective decryption method.

<h3>Figure 1. – Frequency Analysis Method</h3>
<img src="https://github.com/martinmathurine/Cryptography-Decryption-CyberChef-Lab/assets/42855193/7855d3d5-1be8-4625-a75b-08ec43e27714" width="500">

After receiving the encrypted file, I identified a suitable decryption tool: CyberChef, an open-source platform developed by GCHQ and available via GitHub [10]. This tool offers a range of encoding and decoding operations ideal for cryptographic analysis.

<h3>Figure 2. – Encrypted Ciphertext</h3>
<img src="https://github.com/martinmathurine/Cryptography-Decryption-CyberChef-Lab/assets/42855193/7cd310d3-aaf9-4ab1-a56f-1bd4bb962bf2" width="500">

Using the CyberChef tool, the encrypted ciphertext (as shown in Figure 2) was inputted into the platform. Through a process of trial and error, the operations From Base64 followed by XOR Brute Force were applied. This produced a list of possible hexadecimal keys. By reviewing the outputs for human-readable text, the correct key—6e—was identified, as shown in Figure 3 [10].

<h3>Figure 3. – XOR Brute Forcing the Encrypted Ciphertext</h3>
<img src="https://github.com/martinmathurine/Cryptography-Decryption-CyberChef-Lab/assets/42855193/928a30a3-0d6d-4304-965a-c83f6fe53a4d" width="500">

Now in possession of the potential secret key (6e), I then replaced the ‘XOR brute force’ operation with an ‘XOR’ operation and equipped with ‘6e’ secret key then revealed the original plaintext in the ‘Output’ field as shown in Figure 4.

<h3>Figure 4. – Decrypted Original Plaintext Revealed</h3>
<img src="https://github.com/martinmathurine/Cryptography-Decryption-CyberChef-Lab/assets/42855193/c3d34e2b-1b0e-4b59-9845-6328b9ede674" width="500">

<h2>Results</h2>
<h3>Decoding:</h3>
Utilising ‘CyberChef’ with its vast set of operations led to me successfully achieve my expected outcome as illustrated in Figures 3 and 4. The end-result was computed fast as well as efficiently as opposed to attempting to solve this cryptographic puzzle manually via the use frequency analysis which did not go to plan. The decryption process with the correct operations in place took less than 1-minute to successfully decrypt the file and reveal the original plaintext message in the ASCII character set.

<h3>Key:</h3>
The discovered secret key through trial-and-error used for decrypting the message is, ‘6e’ as previously shown in Figure 3.

<h3>Recovery of Plaintext:</h3>
Figure 5. below shows the recovered original plaintext using the secret key, ‘6e’.

<h3>Figure 5. – Original Plaintext</h3>
<img src="https://github.com/martinmathurine/Cryptography-Decryption-CyberChef-Lab/assets/42855193/af89c125-7ed8-472d-9264-0b3f6b8a1e84" width="500">

<h3>The Original Plaintext As Shown in Figure 5.</h3>
“power. Those individual flowers which had the largest glands or nectaries, and which excreted most nectar, would be oftenest visited by insects, and would be oftenest crossed; and so in the long-run would gain the upper hand. Those flowers, also, which had their stamens and pistils placed, in relation to the size and habits of the particular insects which visited them, so as to favour in any degree the transportal of their pollen from flower to flower, would likewise be
favoured or selected. We might have taken the case of insects visiting flowers for the sake of collecting pollen instead of nectar; and as pollen is formed for the sole object of fertilisation, its destruction appears a simple loss to the plant; yet if a little pollen were carried, at first occasionally and then habitually, by the pollen-devouring insects from flower to flower, and a cross thus effected, although nine-tenths of the pollen were destroyed, it might still be a great gain to the plant; and th”

<h2>Concluding Reflections</h2>
Cryptography is essential for securing data across modern networks, especially with the rise of connected devices like IoT. As long as strong encryption and good security practices are followed, data can be effectively protected from cyber threats.

<h2>References</h2>

- [1] W. Stallings, Cryptography & Network Security GE, 7th ed. Essex: Harlow: Pearson Australia Pty Ltd, 2017, pp. 20, 86, 622-638.

- [2] K. Richards, "cryptography", techtarget.com, 2022. [Online]. Available: https://www.techtarget.com/searchsecurity/definition/cryptography. [Accessed: 01- Jul- 2022].

- [3] P. Loshin, "encryption", techtarget.com, 2022. [Online]. Available: https://www.techtarget.com/searchsecurity/definition/encryption. [Accessed: 01- Jul- 2022].

- [4] geeksforgeeks.org, "Basic Type Base64 Encoding and Decoding in Java", geeksforgeeks.org, 2022. [Online]. Available: https://www.geeksforgeeks.org/basic-type-base64-encoding-and-decoding-in-java/#:~:text=Base%2064%20is%20an%20encoding,(Base%2064%20format%20reference). [Accessed: 01- Jul- 2022].

- [5] S. Yambadwar, "What is RC4 Encryption?", GeeksForGeeks, 2021. [Online]. Available: https://www.geeksforgeeks.org/what-is-rc4-encryption/. [Accessed: 01- Jul- 2022].

- [6] TechTarget, "Block Cipher", TechTarget, 2021. [Online]. Available: https://www.techtarget.com/searchsecurity/definition/block-cipher. [Accessed: 01- Jul- 2022].

- [7] precisely.com, "AES vs. DES Encryption: Why Advanced Encryption Standard (AES) has replaced DES, 3DES and TDEA", precisely.com, 2022. [Online]. Available: https://www.precisely.com/blog/data-security/aes-vs-des-encryption-standard-3des-tdea. [Accessed: 01- Jul- 2022].

- [8] S. Yambadwar, "What is RC4 Encryption?", GeeksForGeeks, 2021. [Online]. Available: https://www.geeksforgeeks.org/what-is-rc4-encryption/. [Accessed: 01- Jul- 2022].

- [11] S. Singh, "Letter Frequencies", The BLACK Chamber, Not published. [Online]. Available: https://www.simonsingh.net/The_Black_Chamber/letterfrequencies.html. [Accessed: 04- Jan- 2022].

<h2>Software Used</h2>

- [9] dcode.fr, "XOR Decoder", dcode.fr, 2022. [Online]. Available: https://www.dcode.fr/xor-cipher. [Accessed: 01- Jul- 2022].
  
- [10] github.com/gchq, "CyberChef", https://github.com/gchq, 2022. [Online]. Available: https://gchq.github.io/CyberChef/. [Accessed: 01- Jul- 2022].
