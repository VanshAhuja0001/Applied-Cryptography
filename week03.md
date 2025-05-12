# WEEK 3 
# Encryption and Decryption
## Question 1

Attack with Known-Plaintext (KPA)
Prior to the attack, we know:

One or more plaintexts and the ciphertexts that go with them are available to the attacker.

An attacker might, for instance, intercept a message and deduce or know some aspects of it, such as email headers or standard greetings.

What is unknown:

The key for encryption.

The plaintexts that are encrypted are not at the attacker's discretion.

Objective:

To find the key or an algorithm to decrypt other ciphertexts, use the known plaintext-ciphertext combinations.

Real-world example:

During World War II, the Allies cracked codes by using well-known phrases like "Heil Hitler" to solve the German Enigma.

Attack by Chosen-Plaintext (CPA)
Prior to the attack, we know:

Using the encryption function, the attacker can select any plaintext and get their ciphertexts.

The encryption oracle is temporarily or indirectly accessible to the attacker (as in public-key systems).

What is unknown:

The key for encryption.

Random ciphertexts are still impossible for the attacker to decrypt.

Objective:

Discover ciphertext patterns that could give away the key or compromise the encryption, allowing the attacker to decipher subsequent communications.

Real-world example:

RSA was subject to adaptive chosen-plaintext attacks prior to the adoption of padding methods such as OAEP.

Attackers interacting with a password-encrypting login form.


Attack on Chosen-Ciphertext (CCA)
Prior to the attack, we know:

The decryption function (oracle access) allows the attacker to select any ciphertext and retrieve its plaintext.

Out of the three models, this one is the most potent.

What is unknown:

The key for encryption.

The target ciphertext that the attacker wishes to crack cannot be decrypted.

Objective:

Learn about the ciphertexts' structures and perhaps decrypt a target ciphertext by using the decryption oracle.

Real-world example:

The attacker delivers altered ciphertexts and observes server responses to deduce the plaintext in Bleichenbacher's attack against RSA (1998) using SSL.

Using symmetric encryption to mitigate Oracle attacks.

## Question 2:
Variable-Length Message Encryption:

Only fixed-size blocks can be encrypted using a block cypher alone. We can encrypt messages of any length using modes.

Offering Security Above and Beyond Simple Encryption:

Inappropriate modes could cause the ciphertext to display patterns from the plaintext, leaving it open to attack.

To increase the security of encryption, certain modes include elements like randomisation (IVs).

Control of Error Propagation:

Certain options make ensuring that the entire message is not tainted in the event of a transmission fault.

Maintaining Integrity and Confidentiality:

Certain modes, like GCM for authenticated encryption, provide authentication to identify tampering.

## Question 3:
Knowing the AES-128 Key Space
The key space of AES-128 has 2 128 potential keys. An average of half of these keys must be checked in a brute-force attack:

(2^128) / 2 = (2^127 ≈ 1.7 × (10^38) (testing keys)
2 2 128

= (2^127) ≈1.7×(10^38) (testing keys)
Approximately (10^15) (1 quadrillion) key guesses per second might be made by a typical high-performance machine nowadays, such as a supercomputer or specialised hardware.
It will take estimated of 5.4 billion years to break AES-128.

## Question 4: 
<img width="1470" alt="Screenshot 2025-04-02 at 2 06 42 pm" src="https://github.com/user-attachments/assets/63bf7503-3524-4404-ba1e-fb2b4b39de04" />

In this image, I performed DES encryption using OpenSSL on a file named `rock.txt` by first generating an 8-byte random key (`590d09ce1f8abce`) with `openssl rand -hex 8`, then successfully encrypting the file using the `openssl enc` command with the DES algorithm, manually specifying the key and an all-zero IV, and using the `-provider legacy` flag to enable legacy ciphers. After encryption, I listed the files to confirm `output.enc` was created and then used `xxd` to view the encrypted binary content in hexadecimal and ASCII format. This output illustrates how DES encrypts data into unreadable binary, highlighting that without the correct key, decryption would not be possible.

## Question 5 And Question 6
<img width="1470" alt="Screenshot 2025-04-02 at 4 41 03 pm" src="https://github.com/user-attachments/assets/b9e3f3cd-9d59-41e0-b089-9155fabac18a">

In this image, I performed AES-192-CBC encryption and decryption on a text file using OpenSSL. First, I generated a 24-byte random key and a 16-byte IV using `openssl rand -hex`. After encountering file read errors due to a misnamed input file (`Rock.txt` instead of `rock.txt`), I successfully encrypted the `rock.txt` file into `encrypt.enc` and verified its unreadable binary format using `xxd`. Then, I decrypted it with the same key and IV, outputting to `output.txt`. The decrypted file content, shown at the bottom, reads a plain English message: “hello everyone. welcome to my channel. Don’t forget to like, share and subscribe.” This demonstrates successful encryption and decryption using AES-192-CBC with OpenSSL.

## Question 7
<img width="1470" alt="Screenshot 2025-04-02 at 4 42 39 pm" src="https://github.com/user-attachments/assets/1316717e-1633-42cd-82f5-ab36ca7f6630" />

## Question 8
<img width="655" alt="Screenshot 2025-05-06 at 2 28 46 pm" src="https://github.com/user-attachments/assets/0d36e4d5-8bef-4aa3-a200-909dcd92f1af" />


In this image, I executed the `openssl speed -evp aes-128-cbc` command on my terminal to benchmark the performance of AES-128-CBC encryption. The test ran for approximately 3 seconds per block size and measured how many bytes per second could be processed using different block sizes (from 16 bytes up to 16384 bytes). The results show that encryption speed increased with larger block sizes, reaching up to around 1.77 million kilobytes per second for 16KB blocks. This benchmarking output demonstrates the efficiency of AES-128-CBC on the system and helps evaluate its throughput under various workloads.
