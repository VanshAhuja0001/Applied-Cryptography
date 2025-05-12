# Here i chooose https-sandilands-tls12dh-selected.pcap from the repository.

## 2. Encrypted vs Unencrypted TLS Messages:
From the diagram:
**Unencrypted messages:**

Client Hello

Server Hello

Certificate

Server Key Exchange

Server Hello Done

Client Key Exchange

Change Cipher Spec


**Encrypted messages:**

Encrypted Handshake Message (both directions)

Application Data

Encrypted Alert

<img width="743" alt="1" src="https://github.com/user-attachments/assets/47e18079-a7f5-4b78-854b-521daea73768" />
This shows packet 8 from the TLS 1.2 DH handshake, specifically the Server Key Exchange message. It reveals the Diffie-Hellman parameters:
Prime p length is 256 bytes (2048 bits),
Generator g = 02,
The server’s public key,
Signature algorithm used is rsa_pkcs1_sha256, This confirms that normal (finite field) Diffie-Hellman is used (not ECDH) with a 2048-bit key

<img width="754" alt="2" src="https://github.com/user-attachments/assets/1f519057-dbf8-4257-b0cc-7acfecc93396" />
This is from the Client Hello message in packet 4, showing the supported DH and ECDH groups:
Groups like ffdhe2048, ffdhe3072, and ffdhe4096 indicate the client supports 2048–4096 bit DH keys.
Groups like secp256r1 and x25519 indicate ECDHE (Elliptic Curve DH) support as well.

<img width="742" alt="3" src="https://github.com/user-attachments/assets/75f6b325-eece-4623-acf1-c4cfb7fd8ece" />
This image shows Packet 8 from the Wireshark capture of a TLS 1.2 handshake using Diffie-Hellman (DH). Specifically, it contains the Server Key Exchange message, which includes crucial parameters for the DH key exchange:
TLS Version: TLS 1.2 (0x0303).
Handshake Type: Server Key Exchange (type 12), which is sent by the server to provide its DH public values and authenticate them.

Diffie-Hellman Server Params:

p Length: 256: This means the prime number p used in the DH algorithm is 256 bytes long (2048 bits), indicating a 2048-bit DH group, which is a standard secure size.

g: 02: This is the generator value g, a small number used in the modular exponentiation (commonly 2).

Public key length: 256: This is the DH public value sent by the server, also 2048 bits.

Signature Algorithm: rsa_pkcs1_sha256, which indicates the server signs the DH parameters using its RSA private key and SHA-256 hashing.

This signature is crucial—it proves the DH parameters actually came from the server, protecting against man-in-the-middle (MITM) attacks.

This message is not encrypted, as it must be readable by the client to complete the DH key exchange securely and verify the server’s identity.

<img width="959" alt="4" src="https://github.com/user-attachments/assets/9e9e7ec3-f1ad-4ce4-812f-8e7005407537" />
This image is a full view of a Wireshark packet capture (pcap) file named https-sandilands-tls12dh-selected.pcap, showcasing a TLS 1.2 handshake using traditional Diffie-Hellman (DH). Here's a breakdown of the important parts:

TCP Handshake (Packets 1–3):
The client (192.168.1.12) initiates a TCP connection to the server (103.3.63.107) using the typical 3-way handshake (SYN, SYN-ACK, ACK).

TLS Handshake (Packets 4–11):

Packet 4: Client Hello — the client proposes supported cipher suites and DH groups.

Packet 6: Server Hello, Certificate — server responds with its chosen cipher and its certificate.

Packet 8: Server Key Exchange, Server Hello Done — server provides DH parameters (p, g, and pubkey).

Packet 10: Client Key Exchange, Change Cipher Spec, and Finished — client sends its DH public key and begins encrypted communication.

Packet 11: New Session Ticket, Change Cipher Spec, Finished — server finalizes the handshake.

Encrypted Data Exchange (Packets 12–19):

These packets show encrypted application data going both ways (Client → Server and Server → Client).

Packet 19 is an Encrypted Alert, often used for signaling the end of the session.

TCP Session Teardown (Packets 20–23):
The session ends with a FIN-ACK exchange, properly closing the TCP connection.

<img width="766" alt="5" src="https://github.com/user-attachments/assets/79c6a6e3-356a-4686-89bd-93cda3def792" />
This screenshot shows Wireshark’s Packet 6 for a TLS 1.2 handshake, specifically analyzing the Server Hello message where the X.509 digital certificate is provided by the server. Inside the certificate:

Algorithm Used: RSA with SHA-256 (sha256WithRSAEncryption), indicating how the certificate was signed.

Subject Public Key Info: Reveals the server’s RSA public key, which includes:

Modulus (highlighted): The core of the RSA key—this is a 2048-bit number used in RSA encryption/decryption.

Public Exponent: 65537—a common, secure value. This RSA key will be used by the client to verify the server’s digital signature and possibly to encrypt the pre-master secret if not using (EC)DHE.

<img width="758" alt="6" src="https://github.com/user-attachments/assets/083c2ab2-bda4-424e-8ba7-a6fe0204417c" />
This is another view of Packet 6, showing additional expanded fields of the certificate chain in the TLS 1.2 Server Hello message. It includes:

Version: The certificate is version 3 (the most common).

Serial Number and signature algorithm match the previous image.

The subjectPublicKeyInfo block confirms the RSA algorithm is being used and again shows the modulus and public exponent (65537).

Additionally, the TLS segment data is shown at the bottom (in hex), which is the raw data carrying the certificate.



