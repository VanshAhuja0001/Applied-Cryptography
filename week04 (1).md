## Question 1
![WhatsApp Image 2025-05-06 at 14 40 02](https://github.com/user-attachments/assets/d89f61ec-2eb2-4ce1-b1a9-a4217c9220b4)

## Question 2
Simple Block Cipher (SBC)
Task A: Encrypt a random 5-bit plaintext with a random 3-bit key
Task B: Decrypt the ciphertext 11111 using a random 3-bit key

Explanation:
SBC is a simple lookup-based block cipher:

Encryption: Find the row for the plaintext and the column for the key. The value at the intersection is the ciphertext.

Decryption: Find the column for the key, look down that column to find the ciphertext, and then trace left to get the plaintext.

Example (assuming from lookup table):

Encrypt 10101 with key 011 → Ciphertext: 11011

Decrypt 11111 with key 100 → Plaintext: 00110

This teaches you how real block ciphers work with fixed block sizes and key lengths

In this task, I worked with a simple block cipher (SBC) to understand how basic encryption and decryption function using a lookup table. For encryption, I chose a random 5-bit plaintext `10101` and a 3-bit key `011`. Using the SBC table, I located the row for the plaintext and the column for the key, and the value at their intersection gave me the ciphertext `11011`. For decryption, I took the ciphertext `11111` with a key `100`, found the key's column in the SBC table, searched down that column to locate the ciphertext, and then traced back to the corresponding plaintext row, which gave me `00110`. This exercise helped me understand how real block ciphers use fixed-size inputs and secret keys to transform and protect data.

## Question 3
<img width="495" alt="Screenshot 2025-05-06 at 2 48 18 pm" src="https://github.com/user-attachments/assets/5aa46888-4a64-46e4-938a-041826cd04ab" />

## Questionn 4
<img width="481" alt="Screenshot 2025-05-06 at 2 51 27 pm" src="https://github.com/user-attachments/assets/f29f06b4-5b0f-4ded-9167-1125aa65971f" />

## Question 5
<img width="536" alt="Screenshot 2025-05-06 at 2 55 21 pm" src="https://github.com/user-attachments/assets/4344e469-0825-4842-99d7-2921023e16e6" />

## Question 6
``from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from cryptography.hazmat.backends import default_backend
import os

#Generate key and IV
key = os.urandom(16)  # AES-128
iv = os.urandom(16)

#Create cipher object
cipher = Cipher(algorithms.AES(key), modes.CBC(iv), backend=default_backend())
encryptor = cipher.encryptor()

#Example plaintext (must be padded to 16 bytes)
plaintext = b"Hello world!1234"
ciphertext = encryptor.update(plaintext) + encryptor.finalize()

print("Encrypted:", ciphertext.hex())``
<img width="828" alt="Screenshot 2025-05-06 at 3 04 43 pm" src="https://github.com/user-attachments/assets/0c3a4faa-3471-41a7-8b3f-d93b25481ef4" />








## encryption 
created a new file Rocky.txt and encrypted it and again decrypted 
<img width="1470" alt="Screenshot 2025-04-09 at 1 30 17 pm" src="https://github.com/user-attachments/assets/2acb2d77-2b46-4073-ac87-e5061de8e175" />
                                fig 1:Encryption

In this image, I performed AES-192-CBC encryption on a plaintext file named `rocky.txt` using OpenSSL. Initially, I used `openssl rand -hex 24` to generate a 24-byte (192-bit) random encryption key and `openssl rand -hex 16` to generate a 16-byte (128-bit) IV. Then, using these values, I executed the command `openssl enc -e -aes-192-cbc -in rocky.txt -out encrypt.enc -K <key> -iv <iv>` to encrypt the content of the file. The output file `encrypt.enc` was then inspected using the `xxd -b` command, which shows the encrypted content in binary format along with ASCII interpretation. The binary dump confirms that the plaintext has been fully encrypted, with the ciphertext appearing as a mix of binary values and unreadable characters, demonstrating successful AES encryption with a secure key and IV in CBC mode.

<img width="1470" alt="Screenshot 2025-04-09 at 1 31 00 pm" src="https://github.com/user-attachments/assets/780386e7-973f-4532-a893-d1cbc875db63" />
                                 fig 2:Decryption

In this image, I decrypted a previously encrypted file named `encrypt.enc` using the AES-192-CBC algorithm with OpenSSL. The decryption command `openssl enc -d -aes-192-cbc -in encrypt.enc -out habibi.txt -K 55d82d19b364f86a48b989e799063ed075bfaeld5dda9a8 -iv 75d0add0892e39013acbf833255fb67f` specifies the 192-bit key and 128-bit IV used during encryption. After decryption, I used the `xxd -b` command to view the binary content of the output file `habibi.txt`. The readable ASCII output shows a personal note describing a gym routine, including phrases like "i love gym", "i used to go to gym five times", and "push pull leg", among others. This confirms that the decryption was successful and that the original plaintext has been accurately restored from the ciphertext using the correct key and IV.
              
# for 256 bytes
<img width="1470" alt="Screenshot 2025-04-10 at 12 50 57 am" src="https://github.com/user-attachments/assets/526a33ee-d087-4450-a6a5-9a86bcac09d1" />
fig 1: ecryption

In this image, I performed AES-256-CBC encryption using OpenSSL on a file named `rocky.txt`, generating an encrypted output file named `mayagara.enc`. The command used specifies a 256-bit key (`-K`) and a 128-bit IV (`-iv`). Initially, there were attempts that failed due to key length issues and formatting errors, but the final encryption was successful. To verify the encryption, I used the `xxd -b mayagara.enc` command to view the encrypted file in a binary and ASCII format. The output confirms that the encryption converted the plaintext into a series of non-readable binary data, demonstrating how AES-256-CBC effectively secures content. This process is part of understanding symmetric encryption mechanisms and validating them through visual inspection of the ciphertext.

<img width="1470" alt="Screenshot 2025-04-10 at 12 54 33 am" src="https://github.com/user-attachments/assets/b7ead9ad-57f7-4f72-9593-3e5c094f3252" />
fig 2: decryption

In this image, I successfully decrypted an AES-256-CBC encrypted file (`mayagara.enc`) back into plaintext using OpenSSL, with the output saved as `rocky.txt`. The decryption command includes the `-d` flag for decryption, the `-aes-256-cbc` encryption algorithm, the input encrypted file, output destination, the 256-bit key (`-K`), and the initialization vector (`-iv`). After the decryption, I verified the content of `rocky.txt` using `xxd -b rocky.txt`, which displays the binary representation along with ASCII output. The plaintext content appears on the right side and contains a descriptive personal log or message about gym routines, training methods, and specific workout days like pull and push days. This confirms that the decryption was accurate and illustrates how AES-256-CBC secures data and how it can be properly reversed with the correct cryptographic key and IV.


