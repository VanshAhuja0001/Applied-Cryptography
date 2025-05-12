# Weekly class tutorial for week Five: 
This tutorial helps me work manually to generate a RSA key pair to understand the cryptographic process behind public-key encryption.

### Question 1
<img width="1470" alt="Screenshot 2025-04-09 at 2 07 24 pm" src="https://github.com/user-attachments/assets/0c45319d-3fdd-470a-9d40-fba8032a8653" />

Cipher text:
<img width="1470" alt="Screenshot 2025-04-09 at 3 30 35 pm" src="https://github.com/user-attachments/assets/e201d8e1-2fd6-48ea-902b-31a39a01fbea" />

These two images display the RSA key generation and encryption process carried out in a Windows command prompt using Python. In the first image, the user selects two prime numbers `p = 245` and `q = 200`, computes `n = p * q = 49000`, and finds φ(n) = 48556. The user attempts to find a public exponent `e` such that gcd(e, φ(n)) = 1, and selects `e = 9`. Then using the modular inverse function, the private key `d = 43161` is derived. Both the public key (e, n) and private key (d, n) are printed. In the second image, RSA encryption is performed for different plaintext messages `M = 111`, `222`, and `123`, calculating the ciphertext `C` using the formula `C = M^e mod n`. The ciphertexts are printed, and in the final part, sender and recipient variables are used to structure a formatted message displaying the ciphertext along with sender and receiver details, mimicking a secure message transfer using RSA encryption.

## Question 2
![week 4 2](https://github.com/user-attachments/assets/42ccf038-47b5-4559-88a7-21e1922bce4e)


## Question 3
<img width="1470" alt="Screenshot 2025-05-06 at 3 31 35 pm" src="https://github.com/user-attachments/assets/b80a292a-7761-4243-aac4-672154a94a71" />
<img width="1470" alt="Screenshot 2025-05-06 at 3 32 23 pm" src="https://github.com/user-attachments/assets/158a53ff-e50b-4c59-b74c-6ffbee989cd9" />
<img width="1470" alt="Screenshot 2025-05-06 at 3 35 19 pm" src="https://github.com/user-attachments/assets/d8cf5f6a-fb27-4436-b005-fa391b94f3f8" />
<img width="1470" alt="Screenshot 2025-05-06 at 3 35 31 pm" src="https://github.com/user-attachments/assets/79bc8081-99e5-4df4-96d0-bfc51c2f3242" />
<img width="1470" alt="Screenshot 2025-05-06 at 3 35 38 pm" src="https://github.com/user-attachments/assets/c2a4968a-2d6a-4277-87ed-51c62c6d9e37" />
<img width="1470" alt="Screenshot 2025-05-06 at 3 35 44 pm" src="https://github.com/user-attachments/assets/0f3e54bc-5603-43bb-b1e0-313e3a77ac54" />
These images showcase the full process of generating and inspecting an RSA private key using OpenSSL on a Linux terminal. The process begins with the `openssl genpkey` command, which generates a 3072-bit RSA private key saved as `rock-private.pem`. This key file is then viewed using `less`, displaying the base64-encoded content of the private key wrapped between `-----BEGIN PRIVATE KEY-----` and `-----END PRIVATE KEY-----`. Following that, the key is parsed using `openssl pkey -in rock-private.pem -text` to print its detailed components, including the modulus, public exponent (commonly 65537), private exponent, two large primes (`prime1` and `prime2`), and other components like `exponent1`, `exponent2`, and the `coefficient`, which are all part of the CRT (Chinese Remainder Theorem) optimization for faster RSA operations. This series of screenshots demonstrates not only key generation but also how OpenSSL transparently reveals the internal mathematical structure of RSA keys, which is crucial for understanding cryptographic systems. 

## Question 5
from cryptography.hazmat.primitives import serialization, hashes
from cryptography.hazmat.primitives.asymmetric import rsa, padding
from cryptography.exceptions import InvalidSignature

#Generate RSA key pair
print("Generating RSA key pair...")
private_key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048,
)
public_key = private_key.public_key()

#Save private key to PEM file
with open("private_key.pem", "wb") as f:
    f.write(private_key.private_bytes(
        encoding=serialization.Encoding.PEM,
        format=serialization.PrivateFormat.PKCS8,
        encryption_algorithm=serialization.NoEncryption()
    ))

#Save public key to PEM file
with open("public_key.pem", "wb") as f:
    f.write(public_key.public_bytes(
        encoding=serialization.Encoding.PEM,
        format=serialization.PublicFormat.SubjectPublicKeyInfo
    ))

print("Keys saved as private_key.pem and public_key.pem")

#Message to be encrypted and signed
message = b"Hello MayaGara. This message is encrypted and signed using RSA."

#Encrypt the message with the public key
print("Encrypting the message...")
ciphertext = public_key.encrypt(
    message,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

with open("ciphertext.bin", "wb") as f:
    f.write(ciphertext)

print("Encrypted message saved as ciphertext.bin")

#Decrypt the message with the private key
print("Decrypting the message...")
with open("ciphertext.bin", "rb") as f:
    encrypted_data = f.read()

decrypted = private_key.decrypt(
    encrypted_data,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)

print("Decrypted message:", decrypted.decode())

#Sign the message with the private key
print("Signing the message...")
signature = private_key.sign(
    message,
    padding.PSS(
        mgf=padding.MGF1(hashes.SHA256()),
        salt_length=padding.PSS.MAX_LENGTH
    ),
    hashes.SHA256()
)

with open("signature.bin", "wb") as f:
    f.write(signature)

print("Signature saved as signature.bin")

#Verify the signature with the public key
print("Verifying the signature...")
try:
    public_key.verify(
        signature,
        message,
        padding.PSS(
            mgf=padding.MGF1(hashes.SHA256()),
            salt_length=padding.PSS.MAX_LENGTH
        ),
        hashes.SHA256()
    )
    print("Signature is valid.")
except InvalidSignature:
    print("Signature is invalid.")
    
<img width="1470" alt="Screenshot 2025-05-06 at 4 13 25 pm" src="https://github.com/user-attachments/assets/9c2723a6-93bb-459f-8b5a-84ff4eccec49" />



