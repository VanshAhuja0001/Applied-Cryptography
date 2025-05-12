## Question 1
![15](https://github.com/user-attachments/assets/2757ed83-13a1-4af3-8ed0-3972c9caeb3f)

## Calculation part
![calc](https://github.com/user-attachments/assets/10059aa1-5f6b-440e-b546-cab8c8e7a625)
![9](https://github.com/user-attachments/assets/fe25fbd2-69c3-4f7c-8f90-cffde4f5754e)
![15](https://github.com/user-attachments/assets/451f700b-3512-477a-bcb1-682044cc5b24)

## Question 2
## Public key and private secret Key
<img width="1470" alt="Screenshot 2025-04-23 at 4 18 03 pm" src="https://github.com/user-attachments/assets/2c407a00-bd49-4fa8-a276-ff3f5ea578a6" />
<img width="1470" alt="Screenshot 2025-04-23 at 4 18 54 pm" src="https://github.com/user-attachments/assets/2c47c271-6107-4bbe-ae86-d00ae9e97ea1" />

<img width="1470" alt="Screenshot 2025-04-23 at 4 19 43 pm" src="https://github.com/user-attachments/assets/4cc48dee-0d3b-4999-b7f0-7bfa9d86cd91" />

<img width="1470" alt="Screenshot 2025-04-23 at 4 19 43 pm" src="https://github.com/user-attachments/assets/fa940340-7eb5-4de7-b21f-951590422591" />
<img width="1470" alt="Screenshot 2025-04-23 at 4 21 57 pm" src="https://github.com/user-attachments/assets/5a5230d5-100f-41ab-8b56-fcc5416abef9" />

In these screenshots, I am performing a successful Diffie-Hellman Key Exchange using OpenSSL between myself and Satya to establish a shared secret. First, I generated Diffie-Hellman parameters using `openssl genpkey` with a 2048-bit key size, creating a file called `dhparam.pem`. Using that, I generated private keys for both myself (`dhprivkey-rock.pem`) and Satya (`dhprivkey-satya.pem`). Next, I extracted the corresponding public keys (`dhpub-rock.pem` and `dhpub-satya.pem`) and verified them in DER format. Then, I used `openssl pkeyutl -derive` to generate the shared secret from my private key and Satya’s public key, saving the result into `rock-shared-secret.bin`. Similarly, I showed Satya’s side, deriving the same shared secret using her private key and my public key, saving it as `satya-shared-secret.bin`. The `xxd` hex dumps in the screenshots visually confirm both secrets match, proving the key exchange succeeded. This exchange demonstrates secure symmetric key generation over an insecure channel, critical in encrypted communication.

## Question 3
<img width="1233" alt="Screenshot 2025-05-06 at 4 39 16 pm" src="https://github.com/user-attachments/assets/2b9dfe54-4797-4209-86e0-7af3f0975071" />
This image shows a Man-in-the-Middle (MITM) attack on the Diffie-Hellman Key Exchange (DHKE) process between me (Rock) and my friend Satya. We were trying to establish a shared secret key using DHKE, where I selected \( p = 17 \), \( g = 6 \), and my public value \( P_U = 15 \). However, an attacker secretly intercepted our exchange. When I sent my public value to Satya, the attacker replaced it with their own fake key \( P_{UE1} \), and when Satya sent his public key, the attacker again intercepted and sent me another fake key \( P_{UE2} \). Because of this, I unknowingly created a shared key with the attacker instead of Satya using \( K_{AE} = P_{UE2}^{10} \mod 17 \), and Satya also ended up creating a different key with the attacker \( K_{BE} = P_{UE1}^{11} \mod 17 \). This attack worked because we didn’t authenticate each other’s public keys, allowing the attacker to sit in the middle, read or change any messages, and completely break the confidentiality of our communication.

