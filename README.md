# Cryptography-Decryption-CyberChef-Lab

<h2>Introduction</h2>
The objective for this assignment is to successfully break an encrypted binary file that has been base64 encoded. In this report I will clearly explain the steps taken to decrypt the file as well as correctly identify the key in order to recover the plaintext. Additionally, I will also discuss cryptographic encryption/decryption concepts as well as the proper use of tools to break the code.

Modern cryptography uses five key principles for information assurance which are as follows; Availability – How sensitive data can be made available to end-users. Confidentiality – The intended recipient is the only person able to view the sensitive information. Integrity – To ensure data has not been modified in any way between transmission from the sender to the recipient. Non-repudiation – Proof of successfully transferring information from both the sender and the recipient. Authentication – Before accessing any personal information, procedures are in place to check that the user is valid. [2]

In cryptography, cryptographic techniques are employed in order to securely protect information and communication through the implementation of codes so that only the authorised party can successfully read the message. Cryptography is used to conceal stored information as well as during its transmission. In modern times, cryptography mostly implies scrambling plaintext into ciphertext in a process called, ‘enciphering’ or ‘encryption’, then vice-versa in a process called, ‘deciphering’ or ‘decryption’ which restores the plaintext using the key. Individuals who practice this field of study are known as cryptographers. This type of scheme is known as a ‘cryptographic system’ or a ‘cipher’. Techniques used for deciphering a message without any prior knowledge of the encryption algorithm used are known as the field of ‘cryptanalysis’. Cryptanalysis is defined simply as cracking/breaking the code. The areas of cryptography and cryptanalysis together are called cryptology. [1]

<h2>Summary</h2>
The purpose of this report is to draw on a variety of cryptographic concepts whilst appreciating and discussing the significance of some of the techniques used to decrypt the message’s ciphertext within the encrypted file.

<h2>Decryption Methodology</h2>
When an unauthorised entity intercepts an encrypted message, the unauthorised entity must make an educated guess of which cipher the sender used to encrypt the message as well as what key/s were used as variables. The time and difficulty of guessing this information are what make encryption such a valuable security tool. [3] In regards to this assignment, it was already ascertained that the file was Base64 encoded and has an 8-bit key.

<h3>Base64 Decoding:</h3>
Base64 is an encoding scheme which maps “6-bit blocks of input to 8-bit blocks of output, all of which are printable ASCII characters” [A-Za-z0-9+/]. Regarding this assignment, the Base64 algorithm used has converted the input stream to ASCII text ensuring a level of confidentiality making the ciphertext unintelligible. The converted data can now be easily transported over a computer network uncorrupted providing data integrity. [1] The decoder will inherently reject any character set outside of the ASCII character set. [4]

<h3>Comparison of Decryption Approaches:</h3>
Assuming the plaintext is in the English language, an approach is mounting a statistical attack on this cipher such as implementing the frequency analysis technique. This includes making use of the English letter frequency counts. By simply comparing the letter frequency with the plaintext alphabet’s letter frequency count which appears most commonly. If the ciphertext contains any repeated characters, then it can be surmised to represent one of these. [5] Tailoring the frequency analysis to the type of message which is being deciphered as well as identifying common pairs of letters focusing on repeated pairs of letters in the ciphertext will help in identifying the smallest pairs of words first. An XOR can be used to find an instance where the Nth character of the key. [11]

Another approach to decrypting the ciphertext would be to utilise the dictionary attack method. The steps to crack the code would involve the unauthorised entity painstakingly building a dictionary containing every possible encryption of the known-plaintext message which could be gathered. If the attacker finds multiple matches each can be tried to determine the correct key which is effective against small key lengths such as the 8-bit key in this assignment.

An approach used to extract the secret key from the ciphertext to reveal the plaintext within the encrypted message is to use brute force. From an educated guess, the brute force method simply tries every possible combination of keys one after another in an attempt to successfully reveal the once encrypted original plaintext. The brute force method is an ideal solution for decrypting simple or small problems. The brute force attack combines transposition and substitution utilising frequency analysis on the ciphertext to successfully decrypt the message. As a result, producing many possible keys. Depending on this key length, this decryption approach can take an immeasurable amount of time to break the code and reveal the plaintext successfully through trial-and-error.

<h3>Symmetric Encryption:</h3>
A symmetric encryption scheme is “used to conceal the contents of blocks or streams of data of any size, including messages, files, encryption keys, and passwords”. In terms of this assignment, a key will need to be successfully attained in order to reveal the plaintext concealed within the message. The symmetric cipher model is comprised of 5 main elements which are as follows; Plaintext – the original intelligible message inputted into the encryption algorithm. Encryption algorithm – a mathematical or logical formula used to encode the message. Secret key – A variable to make the ciphered message unique. Ciphertext – The scrambled message produced as the output containing a perceivably unintelligible message. Decryption algorithm – A reverse engineering of the encryption method used in conjunction with the secret key and the ciphertext to reveal the plaintext. [1] 

A stream cipher such as Rivest Cipher 4 (RC4) is a symmetric encryption method wildly deployed based on its simplicity and speed of operation using either 64-bit or 128-bit key sizes. However, multiple vulnerabilities have been discovered rendering RC4 insecure. Its use of application was for Secure Socket Layer (SSL) as well as Transport Layer Security (TLS) among others. [8]

A commonly used block cipher, Data Encryption Standard (DES), was intended to be replaced by AES in 1998 due to security vulnerabilities. DES encrypts blocks of 64-bits at a time and is deemed no longer effective due to its short 56-bit key size. In a 1997 contest, it took a cryptographer ~84 days to break an encrypted message using the basic brute force attack. DES has been replaced by encryption algorithms such as Advanced Encryption Standard (AES) and particularly AES-256 in modern times (first published in 1998). [7]

Another common type of symmetric encryption algorithm is AES which “uses a 128-bit block size and a 128-, 192- or 256-bit key size.” [6] AES-256 has the largest bit-size with a key length of 256-bits and is virtually resilient to the brute force method regarding modern computer hardware and software. Its implementations include wireless security, file encryption as well as encrypted web-based Internet browsing. [7]

<h3>Steps – How the Ciphertext was Decrypted:</h3>
At first, I attempted to manually break the encrypted message in combination with utilising an online frequency analysis tool published by dcode.fr. Using the frequency analysis method, the tool will attempt to decode the ciphertext. The results from my attempts proved to be fruitless in the decryption process to discover the secret key which I would then XOR the characters to reveal a possible plaintext character since the XOR encryption method is symmetrical to using the XOR encryption method using the ASCII table. However, this proved to be time consuming and not efficient. My results using this method produced humanly unintelligible plaintext and therefore I proceeded to seek another more efficient method to break the code of the encrypted message. [9]

<h3>Figure 1. – Frequency Analysis Method</h3>
<img src="https://github.com/martinmathurine/Cryptography-Decryption-CyberChef-Lab/assets/42855193/7855d3d5-1be8-4625-a75b-08ec43e27714" width="500">

After being given an encrypted file to break its code I found a decryption a tool named, ‘CyberChef’ published on GitHub’s platform by a member named, ‘GCHQ’. CyberChef was utilised to successfully break the code of the ciphertext, thus revealing the original plaintext. [10]

<h3>Figure 2. – Encrypted Ciphertext</h3>
<img src="https://github.com/martinmathurine/Cryptography-Decryption-CyberChef-Lab/assets/42855193/7cd310d3-aaf9-4ab1-a56f-1bd4bb962bf2" width="500">

Utilising a tool named, ‘CyberChef’ I entered the encrypted ciphertext into the ‘input’ field as previously seen in Figure 2. Through trial-and-error, the operations used to break the code were first to use the ‘From Base64’ operation in combination with the ‘XOR brute force’ operation. This process resulted in producing dozens of potentially possibly correct HEX secret keys. Using basic human intelligence, whilst making the way down the list of the outputted possible combinations of secret keys containing chunks of intelligible portions of the potentially original plaintext, I was able to discernibly find the correct secret key. [10] In this instance, the secret key containing a portion of the humanly intelligible text was the key, ‘6e’ as highlighted in Figure 3.

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

The Original Plaintext As Shown in Figure 5.<h3>
“power. Those individual flowers which had the largest glands or nectaries, and which excreted most nectar, would be oftenest visited by insects, and would be oftenest crossed; and so in the long-run would gain the upper hand. Those flowers, also, which had their stamens and pistils placed, in relation to the size and habits of the particular insects which visited them, so as to favour in any degree the transportal of their pollen from flower to flower, would likewise be
favoured or selected. We might have taken the case of insects visiting flowers for the sake of collecting pollen instead of nectar; and as pollen is formed for the sole object of fertilisation, its destruction appears a simple loss to the plant; yet if a little pollen were carried, at first occasionally and then habitually, by the pollen-devouring insects from flower to flower, and a cross thus effected, although nine-tenths of the pollen were destroyed, it might still be a great gain to the plant; and th”

<h2>Concluding Reflections</h2>
Over the past two millennia, applied cryptography was used mostly for securing data in transit such as the Caesar cipher through to modern times in the age of technology with its deployment in Transport Layer Security (TLS), file encryption in addition to end-to-end message encryption among other applications. In recent times, cryptography is a necessary tool used to provide information assurances for data on all layers of the OSI model as the data traverses through a computer network. Today, cryptography and its sufficient applications are essential in an ever-increasing amount of technology being used which needs to communicate with each other, especially with the current upward trend of Internet-of-Things (IoT) devices in an ever more progressively connected society. In turn, this calls for a need for improved data security assurances. In conclusion, although cyber-attackers can utilise a plethora of reverse-engineered data attack methods as long the best security practices are in place and implemented with sufficient encryption protocols and algorithms to secure data for individuals and entities the data can be strongly protected in the presence of malicious third-parties.

<h2>References</h2>
[1] W. Stallings, Cryptography & Network Security GE, 7th ed. Essex: Harlow: Pearson Australia Pty Ltd, 2017, pp. 20, 86, 622-638.

[2] K. Richards, "cryptography", techtarget.com, 2022. [Online]. Available: https://www.techtarget.com/searchsecurity/definition/cryptography. [Accessed: 01- Jul- 2022].

[3] P. Loshin, "encryption", techtarget.com, 2022. [Online]. Available: https://www.techtarget.com/searchsecurity/definition/encryption. [Accessed: 01- Jul- 2022].

[4] geeksforgeeks.org, "Basic Type Base64 Encoding and Decoding in Java", geeksforgeeks.org, 2022. [Online]. Available: https://www.geeksforgeeks.org/basic-type-base64-encoding-and-decoding-in-java/#:~:text=Base%2064%20is%20an%20encoding,(Base%2064%20format%20reference). [Accessed: 01- Jul- 2022].

[5] S. Yambadwar, "What is RC4 Encryption?", GeeksForGeeks, 2021. [Online]. Available: https://www.geeksforgeeks.org/what-is-rc4-encryption/. [Accessed: 01- Jul- 2022].

[6] TechTarget, "Block Cipher", TechTarget, 2021. [Online]. Available: https://www.techtarget.com/searchsecurity/definition/block-cipher. [Accessed: 01- Jul- 2022].

[7] precisely.com, "AES vs. DES Encryption: Why Advanced Encryption Standard (AES) has replaced DES, 3DES and TDEA", precisely.com, 2022. [Online]. Available: https://www.precisely.com/blog/data-security/aes-vs-des-encryption-standard-3des-tdea. [Accessed: 01- Jul- 2022].

[8] S. Yambadwar, "What is RC4 Encryption?", GeeksForGeeks, 2021. [Online]. Available: https://www.geeksforgeeks.org/what-is-rc4-encryption/. [Accessed: 01- Jul- 2022].

[11] S. Singh, "Letter Frequencies", The BLACK Chamber, Not published. [Online]. Available: https://www.simonsingh.net/The_Black_Chamber/letterfrequencies.html. [Accessed: 04- Jan- 2022].

<h2>Software Used</h2>
[9] dcode.fr, "XOR Decoder", dcode.fr, 2022. [Online]. Available: https://www.dcode.fr/xor-cipher. [Accessed: 01- Jul- 2022].

[10] github.com/gchq, "CyberChef", https://github.com/gchq, 2022. [Online]. Available: https://gchq.github.io/CyberChef/. [Accessed: 01- Jul- 2022].

