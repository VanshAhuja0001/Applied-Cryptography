# Week 2 
## Question 1
<img width="1470" alt="Screenshot 2025-04-04 at 11 05 17 am" src="https://github.com/user-attachments/assets/d961c682-f159-448f-9db9-34230983b80c" />

## Question 2
<img width="1470" alt="Screenshot 2025-04-04 at 2 53 03 am" src="https://github.com/user-attachments/assets/db721837-81db-4da0-8538-7425c2258f5e" />
In this figure, I manually decrypted the ciphertext "pjhigpaxp" using the Caesar cipher with a shift (key) of 15. I first constructed a normal alphabet table indexed from 0 to 25 and then shifted it by 15 positions to get the cipher alphabet. By matching each cipher letter back to the corresponding normal letter, I derived the decrypted message "AUSTRALIA". This process visually demonstrates how character shifting works in Caesar cipher encryption and decryption.

## Question 3
<img width="1470" alt="Screenshot 2025-04-04 at 2 34 45 am" src="https://github.com/user-attachments/assets/3798e024-1506-42bb-8ae7-5c4d1ba66b49" />
This screenshot shows the result of using Python to perform a brute-force Caesar cipher decryption on the ciphertext. I looped through shift values from 0 to 15 and printed the output at each shift. The correct shift (key) was 15, which successfully revealed the original message "AUSTRALIA". This confirmed the manual decryption done earlier and demonstrated how scripting can automate and validate cipher cracking.

## Question 4
<img width="1470" alt="Screenshot 2025-04-02 at 5 24 26 pm" src="https://github.com/user-attachments/assets/f82d4c13-2b60-4032-a72b-0248b7a49aaa" />
In this output, I tested the Caesar cipher against a new ciphertext "Knupdrw" using the pycipher Python library. As I looped through all possible 25 shifts, the correct plaintext "BELGIUM" appeared when the shift was 8. This figure highlights how Caesar cipher brute-force attack is effective on short ciphertexts, especially when the expected output is a known word or country name.

## Question 7
<img width="186" alt="Screenshot 2025-04-04 at 11 53 08 am" src="https://github.com/user-attachments/assets/7d994bcb-cbab-493c-915e-70d2069dfeab" />

This image shows the Playfair cipher matrix built from the keyword "Program" and the ciphertext "rpopizuliz". The matrix is constructed by writing out the keyword (without repeating letters) and filling in the rest of the alphabet (excluding 'j') in row-major order. This table is the foundational structure needed for decrypting the Playfair cipher using digraph rules.


<img width="549" alt="Screenshot 2025-04-04 at 11 52 10 am" src="https://github.com/user-attachments/assets/aeba1fae-003f-4f26-b8dd-b09191996bcc" />

In this figure, I broke the ciphertext "rpopizuliz" into digraphs and applied the Playfair cipher decryption rules: same row, same column, or rectangle rule. Step-by-step, I decrypted each pair to get the final plaintext message "programming". The image illustrates the logical reasoning and matrix-based manipulation required to reverse the Playfair cipher.


## Question 8
<img width="1470" alt="Screenshot 2025-04-04 at 11 24 20 am" src="https://github.com/user-attachments/assets/56a0cc83-ce35-4b2b-b848-a0cd8029713a" />
This image explains how I decrypted the Rail Fence cipher text "irtngapconentehooisnapiaintecledlts" using a key of 3. I first placed the characters in a zigzag (rail) pattern across three rows, then rearranged them to restore the correct sequence. After reading row-by-row and reconstructing the message, the plaintext revealed was: "Interconnecting a point in space and time". The image clearly explains how zigzag placement and row-wise reading work in rail fence decryption.

## Question 9 
<img width="496" alt="Screenshot 2025-04-04 at 11 38 40 am" src="https://github.com/user-attachments/assets/bd772e34-d52a-446e-bcef-6fbf672640ee" />

This figure shows my decryption process of a Columnar Transposition Cipher with the ciphertext "cieaexshxettrbxass" using the key 164325. I first wrote the ciphertext into a 3-row table following the column order of the key, then rearranged the columns back to their original order (based on the numerical key). Finally, reading row-wise yielded the plaintext "Cease exit harass". This demonstrated the impact of column-wise permutation and restoration in transposition ciphers.

## Question 10
<img width="613" alt="Screenshot 2025-05-06 at 1 43 57 pm" src="https://github.com/user-attachments/assets/edee17a4-f7f5-43b9-b7e4-bae632c70599" />





[Return to contents](./README.md)


