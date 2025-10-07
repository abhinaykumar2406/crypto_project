# crypto_project
ZKP-Based Two-Device Authentication System  This project implements a Zero-Knowledge Proof (ZKP) based authentication system using a trusted and an untrusted device. The system ensures secure login without sending passwords over the network.
Directory
cd zkp_project

Installation

Install OpenSSL development libraries:

sudo apt-get install libssl-dev


Compile the source files:

gcc -o server server.c -lssl -lcrypto
gcc -o trusted_device trusted_device.c -lssl -lcrypto
gcc -o untrusted_device untrusted_device.c -lssl -lcrypto

Usage
1. Start the Server
./server

2. Register a New Account (Trusted Device)
./trusted_device


Choose option 1: Register new account

Enter username and password

Keys will be generated and stored locally

3. Login Process
Trusted Device:
./trusted_device


Choose option 2: Login

Enter username and password

Note Token1 for the untrusted device

Untrusted Device:
./untrusted_device


Enter username and Token1

Server initiates halfway login

Back on Trusted Device:

Confirm the login request

Note Token2

Untrusted Device:

Enter Token2 to complete login



#Theory (Short Explanation)

This system uses Zero-Knowledge Proof (ZKP) to securely authenticate a user without exposing their password:

Trusted Device:

Stores secret derived from the password

Performs ZKP rounds and signs messages

Untrusted Device:

Requests login using Token1 from trusted device

Receives Token2 after trusted device confirms

Server:

Verifies ZKP proofs and token exchanges

Ensures the user’s password is never transmitted

Key Concepts:

Zero-Knowledge Proof (ZKP): Proves knowledge of a secret without revealing it

Token-based authentication: Two-step verification ensures both devices confirm login

RSA/ECDSA signatures: Prevent tampering of messages between devices

Notes

Trusted device must have local keys stored (device_keys.txt)

Tokens are time-sensitive; expire after a defined interval

All cryptographic operations use OpenSSL (BN and EVP APIs)
