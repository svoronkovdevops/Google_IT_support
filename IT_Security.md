## Content

[Understanding Security Threats](#understanding-security-threats)

[Cryptology](#cryptology)

[AAA Security](#aaa-security)

[Securing Your Networks](#securing-your-networks)

[Defense in Depth](#defense-in-depth)

[Content](#content)

[Courses list](README.md#contents)


# Understanding Security Threats

## Malicious Software

### The CIA Triad

#### CIA
- **C**onfidentiality
- **I**ntegrity
- **A**vailability

Every aspect of security revolves around these three principles.

- **Confidentiality** means keeping things hidden
- **Integrity** means keeping our data accurate and untampered with
- **Availability** means the information we have is readily accessible to those people who should have it


### Essential Security Terms

- **Risk:** The possibility of suffering a loss in the event of an attack on the system.
- **Vulnerability:** A flaw in the system that could be exploited to compromise the system.
- **0-day vulnerability (zero day):** A vulnerability that is not known to the software developer or vendor, but is known to an attacker.
- **Exploit:** Software that is used to take advantage of a security bug or vulnerability.
- **Threat:** The possibility of danger that could exploit a vulnerability.
- **Hacker:** Someone who attempts to break into or exploit a system.
  - *Black hat hackers* try to get into systems to do something malicious;
  - *White hat hackers* attempt to find weaknesses in a system to fix them before someone can do something malicious.
- **Attack:** An actual attempt at causing harm to a system.


### Malicious Software

**Malware** is a type of malicious software that can be used to obtain your sensitive information, or delete or modify files.

#### The most common malware
- Viruses
- Worms
- Adware
  - Software that displays advertisements and collects data
- Spyware
  - A type of malware that's meant to spy on you
  - A *keylogger* is a common type of spyware that's used to record every keystroke you make
- Trojans
  - Malware that disguises itself as one thing but does something else
- Rootkits
  - A collection of software or tools that an Admin would use
- Backdoors
  - A way to get into a system if the other methods to get in the system aren't allowed
  - Most commonly installed after an attacker has gained access to your system and wants to maintain access
- Botnets
  - Designed to utilize the power of the Internet-connected machines to perform some distributed function
  - Compromised machines are known as *bots*
  - A collection of one or more of these machines is called a *botnet*
- Ransomware
  - A type of attack that holds your data or system hostage until you pay some sort of ransom
- Logic bomb
  - A type of malware that's intentionally installed; after a certain event or time has triggered, it will run the program.


## Network Attacks

### Network Attacks

#### DNS Cache Poisoning attack
- Works by tricking a DNS server into accepting a fake DNS record that will point you to a compromised DNS server
- It then feeds you fake DNS addresses when you try to access legitimate websites
- DNS cache poisoning can spread to other networks, too, if the servers are getting their DNS information from a compromised server

#### Man-in-the-middle attack
- An attack that places the attacker in the middle of two hosts that think they're communicating directly with each other
- A common MitM attack is a *session hijacking* (or a *cookie hijacking*)
- Another MitM method is a **rogue access point** attack;
  - An access point that is installed on the network without the network administrator's knowledge
- A final MtM method is called an *evil twin* 
  - The premise of an evil twin attack is for you to connect to a network that is identical to yours (controlled by the attacker)


### Denial-of-Service

A **Denial-of-service (DOS) attack** is an attack that tries to prevent access to a service for legitimate users by overwhelming the network or server.

A **distributed denial-of-service attack (DDoS)** is a DoS attack using multiple systems.

The **ping of death (POD)** works by sending a malformed ping to a computer; the ping would be larger than what the IP was made to handle, so it results in a buffer overflow, causing the system to crash and potentially allow for execution of malicious code.

**Ping flood** sends a ton of ping packets to a system -- ICMP echo requests; if the computer can't keep up with the echo replies, it could be overwhelmed and taken down.

**SYN flood** (half-open attacks) the server is bombarded with SYN packets, not replying to SYN-ACK packets; thus the connection stays open and takes up the server's resources, not allowing other users to connect to the server.


## Other Attacks

### Client-Side Attacks

**Injection attacks** 
- Can be mitigated with good software development principles, like validating input and sanitizing data

**Cross-site scripting (XSS) attacks** are a type of injection attack where the attacker can insert malicious code and target the user of the service.
- XSS attacks are a common method to achieve a session hijacking.

**SQL injection attack** targets the entire website, if the website is using a SQL database.
- Attackers can potentially run SQL commands that allow them to delete website data, copy it, and run other malicious commands.


### Password Attacks

**Password attacks** use software like password-crackers that try and guess your password.

A common password attack is a **brute force attack**, which just continuously tries different combinations of characters and letters until it gets access.

Another type of password attack is a **dictionary attack**, which tries out words that are commonly used in passwords.

Good passwords are at least 8 characters, and a mix of capital, lower-case, alphanumeric, and symbolic characters.


### Deceptive Attacks

**Social engineering** is an attack method that relies heavily on interactions with humans instead of computers.

A **phishing attack** usually occurs when a malicious email is sent to a victim disguised as something legitimate.

**Spear phishing** specifically targets an individual or group.

**Spoofing** is when a source masquerades around as something else.

**Baiting** is used to entice a victim to do something through physical contact.

**Tailgating** is gaining access into a restricted area or building, by following a real employee in.

[Content](#content)

--------------------------------------------------------------------------------------------Cryptology-----------------------------------------------------------------------------------------------------

# Cryptology

## Symmetric Encryption

### Cryptography

**Encryption** is the act of taking a message -- called *plaintext* -- and applying an operation to it -- called a *cipher* -- so that you receive a garbled, unreadable message as the output, called *ciphertext*.

The reverse process is called **decryption**.

A cipher is made of two components:
1. The **encryption algorithm**
  - The underlying logic or process that's used to convert the plaintext into ciphertext
2. The key
  - The key introduces something unique into your cipher; without the key, anyone using the same algorithm would be able to decode your message, and the secrecy would be lost.

**Security through obscurity:** If no one knows what algorithm or general security practice we're using, we're safer from attackers.

#### Kerchoff's principle

**Cryptosystem:** A collection of algorithms for key generation and encryption and decryption operations that comprise a cryptographic service should remain secure -- even if everything about the system is known, except the key.

This means that even if your enemy knows the exact encryption algorithm you use to secure your data, they're still unable to recover the plaintext from an intercepted ciphertext.

This principle is also known as *Shannon's maxim*, or *"The enemy knows the system."*

The system should remain secure even if your adversary knows exactly what kind of encryption systems you're employing, as long as *your keys remain secure*.

#### Cryptology

- The practice of coding and hiding messages from third parties is called **cryptography**
- The *study* of this practice is referred to as **cryptology**
- The opposite -- looking for hidden messages, or trying to decipher coded messages -- is known as **cryptanalysis**

**Frequency analysis** is the practice of studying the frequency with which letters appear in a ciphertext.

**Steganography** is the practice of hiding information from observers, but not encoding it.
- Archaic forms of stenography included invisible ink
- Modern steganographic techniques include embedding messages and even files into other files (like videos or images)
  - Fed into stenographic software, it would extract a hidden message within the image file.


### Symmetric Cryptography

**Symmetric-key algorithms** use the same key to encrypt and decrypt messages.

A **substitution cipher** is an encryption mechanism that replaces parts of your plaintext with ciphertext.

**Caesar cipher** is a well-known substitution cipher, which is a substitution alphabet.

**ROT13** where the alphabet is rotated 13 places; is actually a Caesar cipher using a key of 13.

**Block ciphers:** The cipher takes data in, places it into a bucket or block of data that's a fixed size, then encodes that entire block as one unit. (If the data to be encrypted isn't big enough to fill the block, the extra space will be padded to ensure the plaintext fits into the blocks evenly.)


**Stream ciphers:** Takes a stream of input and encrypts the stream one character or one digit at a time, outputting one encrypted character or digit at a time. (Meaning there is a 1:1 relationship to data in and data out.)

- Generally speaking, stream ciphers are faster; but can be less secure than block ciphers if the key isn't handled carefully and/or reused.
- To avoid key re-use, **initialization vector (IV)** is used
  - That's a bit of random data that's integrated into the encryption key and the resulting combined key is then used to encrypt the data.
  - The idea is if you have one shared master key, then generate a one-time encryption key
  - In order for the encrypted message to be decoded, the IV must be sent in plaintext along with the encryption message.


### Symmetric Encryption Algorithms

[ notes ]


## Public Key or Asymmetric Encryption

### Asymmetric Cryptography

The strength of the asymmetric encryption system comes from the computational difficulty of figuring out the corresponding private key, given a public key.

The three concepts that an asymmetric cryptosystem grants us are:
1. Confidentiality
  - Granted through the encryption/decryption mechanism
2. Authenticity
  - Granted through the digital signature mechanism
3. Non-repudiation
  - The author of the message isn't able to dispute the origin of the message

#### Symmetric vs Asymmetric Encryption
- Symmetric encryption algorithms are faster, more efficient at encrypting large amounts of data
- Asymmetric encryption works very well in untrusted environments; but it's computationally more expensive and complex
- Combined, asymmetric encryption can be used to keep a shared secret secure in transit; and after receiving the secret, using a symmetric encryption cipher to send data quickly and efficiently.

#### MACs

**Message Authentication Codes:** A bit of information that allows authentication of a received message, ensuring that the message came from the alleged sender and not a third party.

This is different from digital signatures, in that *the secret key that's used to generate the MAC is the same one that's used to verify it*.

**HMAC:** Keyed-hash authentication code. HMAC uses a cryptographic hash function along with a secret key to generate a MAC.

The MAC is sent alongside the message that's being checked; the MAC is verified by the receiver by performing the same operation on the received message, then comparing the computed MAC with the one received with the message. If they match, the message is authenticated.

**Cipher-Based Message Authentication Codes (CMACS):** Similar to HMACs, but instead of using a hashing function, a symmetric cipher with a shared key is used to encrypt the message, and the resulting output is used as the MAC.

**Cipher block chaining message authentication codes (CBC-MAC):** A CMAC example that's slightly different, building MACs using block ciphers. It encrypts using a block cipher in CBC mode, an operating mode for block ciphers that incorporates a previously encrypted block cipher text into the next block's plain text. So it builds a chain of encrypted blocks that requires the full, unmodified chain to decrypt.


### Asymmetric Encryption Algorithms

RSA

DSA

DH

Elliptic curve cryptography (ECC)
- The benefit of elliptic curve-based encryption is that it's able to achieve security similar to traditional public key systems with smaller key sizes.
- A 256-bit elliptic curve key would be comparable to a 3,072-bit RSA key.
- ECDH and ECDSA
- The NSA uses 384-bit EC keys to protect up to "top secret" data.


## Hashing

### Hashing

**Hashing (or a hash function)** is a type of function or operation that takes in an arbitrary data input and maps it to an output of fixed size, called a hash or digest.

You feed in any amount of data into a hash function and the resulting output will always be the same size; but the output should be *unique to the input*, such that two different inputs should never yield the same output.

Hashing can also be used to identify duplicate data sets in databases or archives to speed up searching of tables or to remove duplicate data to save space.

Cryptographic hash functions are used for various applications like:
- Authentication
- Message integrity
- Fingerprinting
- Data corruption deletion
- Digital signatures

*Cryptographic hashing is distinctly different from encryption because cryptographic hash functions should be one directional.*
- You can't take the hash output and recover the plain text

The ideal cryptographic hash function should be deterministic, meaning that the same input value should always return the same hash value.

- The function should not allow for **hash collisions** -- two different inputs mapping to the same output.

Cryptographic hash functions are very similar to symmetric key block ciphers in that they operate on blocks of data -- in fact, many popular hash functions are actually based on modified block ciphers.

`md5sum`


### Hashing Algorithms

- **MD5** is popular and wildly-used, designed in the early 1990s as a cryptographic hashing function
  - It operates on 512-bit blocks, and generates 128-bit hash digests
  - Towards 1996, MD5's flaws became more apparent, as it is vulnerable to hash collisions
  - This led to professionals recommending the adoption of...
- **SHA1** is part of the Secure Hash Algorithm suite of functions, designed by the NSA, published in 1995
  - It operates on 512-bit blocks, and generates 160-bit hash digests
  - SHA1 is used in protocols such as TLS/SSL, PGP SSH, and IPsec
  - SHA1 is also used in version control systems like Git
    - Git uses hashes to identify revisions and ensure data integrity by detecting corruption or tampering
  - SHA1 is being phased out for SHA2 and SHA3

Message Integrity Check (MIC) is a hash digest of the message in question, not unlike a checksum. It doesn't use secret keys (which means the 

#### MIC
- A **Message Integrity Check (MIC)** is essentially a hash digest of a message in question, much like a checksum to ensure that the contents of the message weren't modified in transit. 
- But unlike a MAC, it doesn't use secret keys -- there's nothing stopping an attacker from altering the message, recomputing the checksum, and modifying the MIC attached to the message.
- MICs protect against accidental corruption or loss, but not against malicious action or tampering.


### Hashing Algorithms (continued)

A successful brute force attack, against even the most secure system imaginable, is a function of attacker time and resources.

#### Rainbow Tables
- A **rainbow table** is a pre-computed table of all possible password values and their corresponding hashes. 
- The idea behind rainbow table attacks is to trade computational power for disk space by pre-computing the hashes and storing them in a table
- The idea behind these types of attacks is to trade computational power for disk space, by pre-computing the hashes and storing them in a table.
- An attacker can determine what the corresponding password is for a given hash by just looking up the hash in their rainbow table.
- This is unlike a brute force attack, where the hash is computed for each guess attempt.
- You can protect against rainbow table attacks with salts.

#### Salts
- A **Password salt** is additional randomized data that's added into the hashing function to generate a hash that's unique to the password and salt combination.
- This makes it so that an attacker would have to compute a rainbow table for each possible salt value
- If a large salt is used, the computational and storage requirements to generate useful rainbow tables becomes almost unfeasible.
- Early Unix systems used a 12-bit salt, which amounts to a total of 4,096 possible salts;
  - Modern systems like Linux, BSD, and Solaris use a 128-bit salt
  - 128-bit salt makes it so that rainbow table attacks aren't possible in any realistic timeframe.


## Cryptography Applications

### Public Key Infrastructure

- **Public Key Infrastructure (PKI)** is a system that defines the creation, storage, and distribution of digital certificates.
  - A *digital certificate* is a file that proves an entity owns a certain public key.
  - A certificate contains information about the public key, the entity it belongs to, and a digital signature from another party that has verified this information.
- The entity that's responsible for storing, issuing, and signing certificates is referred to as **Certificate authority (CA)**.
- There's also a **Registration authority (RA)** who's responsible for verifying the identities of any entities requesting certificates to be signed and stored with the CA.

A central repository is needed to securely store and index keys; and a certificate management system of some sort makes managing access to stored certificates and issuance of certificates easier.

- SSL/TLS server certificate
- Self-signed certificate
- SSL/TLS client certificate
  - Optional and less commonly seen than server certificates
  - These are certificates that are bound to clients and are used to authenticate the client to the server, allowing access control to an SSL/TLS service.
- Code signing certificates are used for signing executable programs
  - This allows users of these signed applications to verify the signatures and ensure that the application was not tampered with

#### Certificate authority trust
- Begins with the Root Certificate Authority
  - There are no higher authorities than them, so they self-sign on their behalf
- 
- A certificate that has no authority as a CA is referred to an **end-entity** or **leaf certificate**.
  - Named because it's the fringe, like a leaf on a tree, as opposed to the root of the tree.

#### X.509
- The **X.509 standard** is what defines the format of digital certificates.
- The fields defined in an X.509 certificate are:
  - Version: What version of the X.509 standard the certificate adheres to
  - Serial number: A unique identifier for the certificate assigned by the CA, which allows the CA to manage and identify individual certificates
  - Certificate signature algorithm: Indicates what public key algorithm is used for the public key and what hashing algorithm is used to sign the certificate
  - Issuer name: Information about the authority that signed the certificate
  - Validity: This contains two subfields -- "Not Before" and "Not After" -- which define the dates when the certificate is valid for
  - Subject: Information about the entity the certificate was issued to
  - Subject Public Key Info: Two subfields define the algorithm of the public key, along with the public key itself
  - Certificate Signature Algorithm: Same as the Subject Public Key Info field; these two fields must match
  - Certificate Signature Value: The digital signature data itself

Fingerprints are hash digests of the whole certificate; they're not actual fields in the certificate, but are computed by clients when validating or inspecting certificates.

#### Web of Trust
= An alternative to the centralized PKI model of establishing trust and binding identities
- A Web of Trust is where individuals -- instead of certificate authorities -- sign other individuals' public keys
- Usually, people interested in establishing web of trusts will organize *key signing parties* where participants perform the same verification and signing.


### Cryptography in Action

TLS grants us 3 things:

- handshake

The session key is the shared symmetric encryption key used in TLS sessions to encrypt data being sent back and forth. Since this key is derived from the public-private key, if the private key is compromised, there's potential for an attacker to decode all previously transmitted messages that were encoded using keys derived from this private key.

Forward secrecy

- Secure Shell (SSH)
- Pretty Good Privacy (PGP)
  - PGP is very secure, with no known mechanisms to break the encryption, and is comparable to military-grade encryption.


### Securing Network Traffic

- If you want to protect data in transit, but the application/channel doesn't utilize encryption, the solution is a VPN.
- A **Virtual private network (VPN)** is a mechanism

OpenVPN authentication methods support pre-shared secrets, certificate-based, and username/passwords.


### Cryptographic Hardware

- **Trusted Platform Module (TPM)**
  - A hardware device that's typically integrated into a computer
  - A dedicated crypto-processor
  - Has a unique, secret RSA key burned into the hardware
  - TMP offers:
    - Secure generation of keys
    - Random number generation
    - Remote attestation
      - The idea of a system authenticating its software and hardware configuration to a remote system.
    - Data binding and sealing
      - This involves using the secret key to derive a unique key, that's then used for encryption of data.
      - This basically binds encrypted data to the TPM; the system the TPM is installed in sends only the keys stored in hardware in the TPM will be able to decrypt the data.

- TPM is a standard with several revisions
- The most secure implementation of TPM is the *discrete chip*, as these incorporate physical tampering resistance to prevent physical attacks on the chip.
- **Secure element:** A tamper-resistant chip often embedded in the microprocessor, or integrated into the mainboard of a mobile device. It supplies secure storage of cryptographic keys and provides a secure environment for applications.

- Trusted Execution Environment (TEE)

- Full Disk Encryption (FDE)
  - Options include:
    - PGP (a commercial product)
    - Bitlocker (from Microsoft; integrates well with TPMs)
    - Filevault 2 (from Apple)
    - dm-crypt (open source for Linux)

- Random vs Pseudo-Random
- **Entropy Pool:** A source of random data to help seed random number generators.

[Content](#content)
----------------------------------------------------------------------------------------------------------------------AAA Security-----------------------------------------------------------------


# AAA Security

## Authentication

### Authentication Best Practices

- **Identification** is the idea of describing an entity uniquely.
- **Authentication** is the process of proving you are who you claim to be.
- **Authorization** pertains to the resources an identity has access to.

In the security world, these two concepts are distinguished from each other by the terms **"authn" (authentication)** and **"authz" (authorization)**.

Security should be thought of as *risk mitigation*.

A good password policy system would enforce *length requirements,* *character complexity*, and the *absence of dictionary words*.


### Multi-factor Authentication

- Username/password is often referred to as *single-factor authentication*.
- **Multi-factor authentication** is a system where users are authenticated by presenting multiple pieces of information or objects.
  1. Something you know
    - Password/PIN
  2. Something you have
    - ATM / Bank card
  3. Something you are
    - Biometric data

One-time password (OTP)
- RSA SecureID time-based token (TOTP) random seed generates an OTP

- Physical tokens
- Short-lived token
  - Commonly generated by physical tokens
- Time-based token (TOTP)
  - Operates by having a secret seed or randomly-generated value on the token that's registered with the authentication server.
- Counter-based tokens
  - More secure than time-based tokens for two reasons:
    1. The attacker would need to recover the seed value and the counter value
    2. The counter value is also incrementing when it's being used -- so a cloned token would only be useful for a short period of time before the counter value changes too much and the cloned token becomes unsynchronized from the real token and the server.

#### U2F
- **Universal 2nd Factor (U2F)** developed by Google, Yubico, and NXP Semiconductors. 
- It incorporates a challenge-response mechanism, along with public key cryptography to implement a more secure and more convenient second-factor authentication solution. 
- U2F tokens are referred to as *security keys* and are available from a range of manufacturers.
- U2F authentication support is built into Chrome and Opera browsers, with native Firefox support on the way.

#### Biometric Authentication

**Biometric authentication** is the process of using unique physiological characteristics of an individual to identify them.

Biometric data should never be stored directly. (It should be run through a hashing algorithm, and the hash is what's stored, not the data.)

**Windows Hello**


### Certificates

Recall that certificates are public keys that are signed by a certificate authority (CA) as a sign of trust.

- In addition to TLS server certificates, there can also be client certificates.
  - These operate very similarly to server certificates but are presented by clients, and allow servers to authenticate and verify clients.
  - It's not uncommon for VPN systems or enterprise WiFi setups to use client certificates for authentication.
- To issue client certificates, an organization must set up and maintain CA infrastructure to issue and sign certificates.
  - Part of authentication also involves the client authenticating the server, providing mutual authentication.
  - This is good, since the client can verify it's talking to the real server, and not an imposter.

Certificates have two dates that need to be verified:
  1. Not valid before;
  2. Not valid after


### LDAP

- Recall that **Lightweight Directory Access Protocol (LDAP)** is an open, industry-standard protocol for accessing and maintaining directory services.
  - Directory services, in this context, refers to something similar to a phone or email directory.
  - It's most commonly used as a backend for the authentication of accounts.
- LDAP uses a tree structure called a **Data Information Tree**, meaning objects will have one parent, and can have one or more children that belong to the parent object.
  - Recall these parents are known as **organizational units (OUs)**
  - Since it's possible for entries in the directory to share attributes, there must be a unique identifier for each entry -- we call this **Distinguished Name (DN)**.
  - *You can think of a DN as a full path to a file, as opposed to a file name.*
    - *Multiple files can have the same file name; but the fully qualified path would describe one unique file.*

#### Common LDAP server operations
- Bind
  - How clients authenticate to the server
- StartTLS
  - Permits a client to communicate using LDAP v3 over TLS
- Search
  - For performing look-ups and retrieval of records
- Add/delete/modify
  - Various operations to write data to the directory
- Unbind
  - Closes the connection to the LDAP server


### RADIUS

- **Remote Authentication Dial-In User Service (RADIUS)** is a protocol that provides AAA services for users on a network.
- A common protocol, used to manage access to internal networks, WiFi networks, email services, and VPN services.
- Originally used for remote dial-up users, it evolved to carry numerous standard authentication protocols like **Extensible Authentication Protocol (EAP)**.
- RADIUS servers can verify user authentication info stored in a flat file, or can ping into external sources like SQL databases, LDAP, Kerberos, or Active Directory.
- A RADIUS server replies with one of three messages:
  1. Access reject
  2. Access challenge
  3. Access accept
- Clients don't actually interact with the RADIUS server directly -- they relay authentications via the Network Access Server.


### Kerberos

- **Kerberos** is a network authentication protocol that uses "tickets" to allow entities to prove their identity over potentially insecure channels to provide mutual authentication.
- It uses symmetric encryption
- Supports AES encryption and implements checksums for confidentiality
- Windows domains from Windows 2000 onward use Kerberos
- "Tickets" are a token to prove your identity

#### How the Kerberos protocol operates

[ notes ]


### TACACS+

- **Terminal Access Controller Access-Control System Plus (TACACS+)** is a Cisco-developed AAA protocol released as an open standard in 1993.
- TACACS+ is primarily used for device administration, authentication, authorization, and accounting.
  - As opposed to RADIUS, *which is mostly used for network access AAA*.
- TACACS+ is mainly used as an authentication system for network infrastructure devices -- which tend to be high-value targets for attackers.


### Single Sign-On

- **Single sign-on (SSO)** is an authentication concept that allows users to authenticate once to be granted access to a lot of different services and applications.
  - SSO is accomplished by authenticating to a central authorization server, like an LDAP server. 
  - This then provides a cookie -- or token -- that can be used to get access to applications configured to use SSO.
- Kerberos is a good example of an SSO authentication service.
- Another example of an SSO system is the OpenID decentralized authentication system.

An attacker that compromises an account has a lot more access under an SSO scheme.


## Authorization

### Authorization and Access Control Methods

Recall that **authorization** pertains to describing what the user account has access to, or doesn't have access to.

One very popular open standard for authorization and access delegation is **OAauth**, used by companies like Google, Facebook, and Microsoft.


### Access Control

- **OAuth** is an open standard that allows users to grant third-party websites and applications access to their information without sharing account credentials.
- It's a form of access delegation, as it's delegated to a third-party.

- It starts by prompting the user to confirm that they agree to the third-party access to their account
- Once confirmed, the identity provider will supply the third-party with a token
- This token can be used by the third-party to access data or services offered by the identity provider directly on behalf of the user.

OAuth is commonly used to grant access to third-party applications, to APIs offered by large Internet companies like Google, Microsoft, and Facebook.

OAuth permissions can be used in phishing-style attacks to gain access to accounts, *without requiring credentials* to be compromised.

OAuth is specifically an authorization system; and OpenID is an authentication system. 

- RADIUS also allows you to authorize network access.
- You may want to permit some users to have WiFi and VPN access, while others may not need this
- When they authenticate to the RADIUS server, if the authentication succeeds, the RADIUS server returns configuration information to the network access server.


### Access Control List

- An **access control list (ACL)** is a way of defining permissions or authorizations for objects.
- The most common example is file system permissions.
  - A file system would have an ACL -- which is a table or database -- with a list of entries specifying access rights for individuals or groups for various objects on the file system (like folders, files, or programs)
- These individual access permissions per object are called *access control entries*, and they make up the ACL.
- Network ACLs are used for restricting and controlling access to hoster services running on hosts within your network.


## Accounting

### Tracking Usage and Access

- **Accounting** means keeping records of what resources and services your users accessed, or what they did when they were using your systems.
- A critical component of this is **auditing**, which involves reviewing these records to ensure that nothing is out of the ordinary.
- TACACS+ is a device access AAA system that manages who has access to your network devices and what they do on them.


[Content](#content)

----------------------------------------------------------------------------------------------Securing Your Networks-----------------------------------------------------------------------------------

# Securing Your Networks

## Secure Network Architecture

### Network Hardening Best Practices

**Network hardening** is the process of securing a network by reducing its potential vulnerabilities through configuration changes and taking specific steps.

**Implicit deny** is a network security concept where anything not explicitly permitted or allowed should be denied.



**Analyzing logs** is the practice of collecting logs from different network (and sometimes, client) devices on your network, then performing an automated analysis on them.

You'd want to analyze things like firewall logs, authentication server logs, and application logs.

- **Logs analysis systems** are configured using user-defined rules to match interesting or atypical log entries.
- **Normalizing log data** is an important step, since logs from different devices and systems may not be formatted in a common way.
- You might need to convert log components into a common format to make analysis easier for analysts, and rule-based detection systems, this also makes correlation analysis easier.
- **Correlation analysis** is the process of taking log data from different systems and matching events and matching events across the systems.
- A **post-fail analysis** investigates how a compromise happened after the breach is detected.

**Splunk** is a popular and powerful logs analysis system, offering flexible and extensible log aggregation and search system. It can grab logs data from a wide variety of systems, and in large amounts of formats. It can also be configured to generate alerts, and allows for powerful visualization of activity based on logged data.

**Flood guards** provide protection against DoS or Denial of Service attacks.

*fail2ban* is a popular open source flood guard tool.

**Network separation** or **network segmentation** is a good infosec principle, permitting more flexible management of the network and providing security benefits.  This is the concept of using VLANs to create virtual networks for different device classes/types. It's like creating dedicated virtual networks for your employees to use, and also having separate networks for your printers to connect to. The idea is that printers won't need access to the same network resources that employees do.


### Network Hardware Hardening

Recall that **DHCP** is the protocol where devices on a network are assigned critical configuration information for communicating on the network.

A **rogue DHCP server attack** is when an attacker deploys a server on your network, able to hand out DHCP leases with whatever information they want -- including setting a gateway address or DHCP server that's actually a machine within their control. This gives them access to your traffic and opens the door for future attacks.

#### DHCP snooping
- **DHCP snooping** is an enterprise switch-level feature that protects against rogue DHCP server attacks.
  - It monitors DHCP traffic being sent across it
  - It also tracks IP assignments and maps them to hosts connected to switch ports, building a map of assigned IP addresses to physical switch ports.
  - This info can also protect against IP spoofing and RP poisoning attacks.
- DHCP snooping makes you designate either a trusted DHCP server IP, or enable DHCP snooping trust on the uplinked port.
  - Thus any DHCOP responses coming from either an untrusted IP address or from a downlinked switch port would be detected as untrusted, and discarded by the switch.


#### Dynamic ARP inspection
- Recall that ARP allows for man-in-the-middle attacks because of the unauthenticated nature of ARP, allowing attackers to forge an RP response, advertising its MAC address as the physical address matching a victim's IP address.
  - This is called a *gratuitous ARP response*.
- **Dynamic ARP inspection (DAI)** is another enterprise switch-level feature that prevents this attack.
  - It requires use of DHCP snooping to establish a trusted binding of IP addresses to switch ports.
  - DAI will detect forged gratuitous ARP packets and drop them;
  - It does this because it has a table from DHCP snooping that has the authoritative IP address assignments per port.
  - DAI also enforces rate limiting of ARP packets per port, to prevent ARP scanning.

#### IP Source Guard
- To prevent IP spoofing attacks, **IP Source Guard (IPSG)** can be enabled on enterprise switches along with DHCP snooping.
- IPSG works by using the DHCP snooping table to dynamically create ACLs for each switchboard.
  - It drops packets that don't match the IP address for the port based on the DHCP snooping table.

#### 802.1X
- This is the IEEE standard for encapsulating **Extensible Authentication Protocol (EAP)** traffic over the 802 networks.
- This is also called **EAP over LAN**, or **EAPOL**.
- It was originally designed for Ethernet; but support was added for other network types like WiFi and fiber networks.
- **EAP-TLS** is one of the more common and secure EAP methods.

##### EAP-TLS
- When a client wants to authenticate to a network using 802.1X, there are 3 parties involved:
  1. The client device (what we call the *supplicant*)
    - Also refers to software running on the client machine that handles authentication, like the open source Linux utility `wpa_supplicant`
  2. The authenticator
  3. The authentication server

- The supplicant communicates with the authenticator, which is a gatekeeper for the network.
  - Usually an enterprise switch or access point, requiring clients to successfully authenticate to the network before they're allowed to communicate with the network.
  - The authenticator doesn't actually authenticate -- it sends the request to the authentication server.
- The authentication server -- usually a RADIUS server -- is where the actual credential verification and authentication occurs.
- **EAP-TLS** is an authentication type supported by EAP that uses TLS to provide mutual authentication of both the client and the authenticating server.
  - It's considered one of the more secure configurations for wireless security.
  - Most EAP-TLS implementations require client-side certificates.
  - Authentication can be certificate-based; or a client can use a certificate in conjunction with a username, password, or even a second factor of authentication (like a OTP).
- A more secure configuration for EAP-TLS would be to bind the client-side certificates to the client platforms using TPMs.
  - This would prevent theft of the certificates from client machines.
  - Combined with FDE, even theft of a computer would prevent compromise of the network.


### Network Software Hardening

- Network software hardening includes things like firewalls, proxies, and VPNs
  - A host-based firewall can protect other hosts from being compromised by corrupt devices on the internal network -- this is something a network-based firewall may not be able to help defend against.
- VPNs are good for providing secure access to internal resources for mobile or roaming users.
  - Recall that VPNs are commonly used to provide **secure remote access**, and **link two networks** securely.
- Proxies provide secure remote access without using a VPN; and are useful to protect client devices and their traffic.
  - A proxy server can allow web traffic to be proxied through a server that we control for many purposes.
- A reverse proxy can be configured to allow secure remote access to web-based services without requiring a VPN.


## Wireless Security

### WEP Encryption and Why You Shouldn't Use It

- Never send plaintext and ciphertext together.


### Let's Get Rid of WEP! WPA/WPA2

- Recall that **WiFi Protected Access (WPA)** was designed as a short-term replacement that would be compatible with older WEP-enabled hardware with a simple firmware update.
- **Temporal Key Integrity Protocol (TKIP)** was a new security protocol introduced to address shortcomings of WEP security. It offered 3 new feaures:
  1. More secure key derivation method
  2. Sequence counter was implemented
  3. A 64-bit message integrity check
- Under WPA, the **pre-shared key** is the WiFi password you share with people when they come over and want to use your wireless network.
  - This is not directly used to encrypt traffic -- it's a factor to derive the encryption key.
  - The passphrase is fed into the **Password-Based Key Derivation Function 2 (PBKDF2)** along with the WiFi network's SSID as a salt.

WPA2 improved WPA security by implementing **Counter Mode CBC-MAC Protocol (CCMP)**
- WPA2 is the best wireless network security available
- Pre-shared key requirements are the same

#### The Four-Way Handshake

The process that authenticates clients to the network.

1. The AP sends a nonce to the client
2. The client sends a nonce to the AP
3. The AP sends the GTK
4. The client responds with an ACK

- **Pairwise Transient Key (PTK)** is generated by:
  - PMK
  - AP nonce
  - Client nonce
  - AP MAC address
  - Client MAC address

- **Groupwise Transient Key (GTK)**
  - Updated and shared between all clients

- WPA/WPA2 also introduce an 802.1X authentication, usually called WPA2-Enterprise.
- Non-802.1X configurations are called either WPA2-Personal, or WPA2-PSK (since they use a pre-shared key to authenticate clients).

- **WiFi Protected Setup (WPS)**
  - Supports PIN entry authentication
  - NFC or USB
  - Push-button authentication
- The PIN authentication mode where the AP has a PIN hard-coded into the firmware is vulnerable to an online brut force attack.
- The PIN is 8 digits long; but the 8th digit is a checksum computed from the first 7 digits.


### Wireless Hardening

In an ideal world, we'd all be protecting our wireless networks with **802.1X with EAP-TLS**.

If 802.1X is too complicated for a company, the next best alternative would be **WPA2 with AES/CCMP mode**.

A long and complex passphrase that wouldn't be found in a dictionary would increase the amount of time and resources an attacker would need to break the passphrase.

If your company values security over convenience, you should make sure that WPS isn't enabled on your APs.


## Network Monitoring

### Sniffing the Network

- **Packet sniffing (packet capture)** is the process of intercepting network packets in their entirety for analysis.
- **Promiscuous Mode** is a type of computer networking operational mode in which all network data packets can be accessed and viewed by all network adapters operating in this mode.
  - If the packets aren't going to be sent to your interface in the first place, Promiscuous Mode won't help you see them.
- **Port mirroring** allows the switch to take all packets from a specified port, port range, or entire VLAN and mirror the packets to a specified switch port.
- **Monitor mode** allows us to scan across channels to see all wireless traffic being sent by APs and clients.

If a wireless network is encrypted, you can still capture the packets; but you won't be able to decode the traffic payloads without knowing the password for the wireless network.


### Wireshark and tcpdump

**tcpdump** is a super popular, lightweight, command-line based utility that you can use to capture and analyze packets.

**Wireshark** is also a packet capture and analysis tool, way more powerful when it comes to application and packet analysis (compared to tcpdump).

Traffic analysis is an important part of network security -- being able to capture and inspect those packets is important to understanding what type of traffic is flowing on our networks that we'd like to protect.


### Intrusion Detection / Prevention System

- **Intrusion Detection and Prevention Systems (IDS/IPS)** operate by monitoring network traffic and analyzing it.
- These look for matching behavior or characteristics that would indicate malicious traffic.
- IDS is only a detection system -- it won't take action to block or prevent an attack when one is detected.
  - It will only log an alert.
- But an IPS system can adjust firewall rules on the fly, to block or drop the malicious traffic when it's detected.
- IDS/IPS can be either host-based or network-based.

- A **Network Intrusion Detection System (NIDS)** detection system would be deployed somewhere on a network where it can *monitor traffic* for a network segment or subnet.
- NIDS are similar to firewalls
  - But firewalls prevent intrusion by potentially malicious traffic coming from outside the network (enforcing ACLs in between);
  - Whereas NIDS systems are meant to detect and alert potential malicious activity coming from within the network.
- A NIDS device is a passive observer, unlike a NIPS.

- **Port mirroring functionality** (found in many enterprise switches) is a good way to get access to network traffic.
  - It allows all packets on a port, port range, or entire VLAN to be mirrored to another port -- where a NIDS host would be connected.

A NIDS host must have at least two network interfaces:
1. For monitoring and analysis;
2. One for connecting to our network, for management and administrative purposes.

Placement of a **Network Intrusion Prevention System (NIP)S** would differ from a NIDS system.
- A NIPS must be placed in-line with the traffic being monitored -- meaning the traffic must pass through the NIPS device.

[Content](#content)

--------------------------------------------------------------------------------------Defense in Depth------------------------------------------------------------------------------------------

# Defense in Depth

**Defense in depth** is the concept of having multiple, overlapping systems of defense to protect IT systems.


## System Hardening

### Disabling Unnecessary Components

- An **attack vector** is a method or mechanism by which an attacker or malware gains access to a network or system.
  - Some attack vectors are email attachments, network protocols/services, network interfaces, and user input.
- An **attack surface** is the sum of all the different attack vectors in a given system.
  - The combination of all possible ways an attacker could interact with our system, regardless of known vulnerabilities.
- Ergo, keep attack surfaces as small as possible.
- The less complex something is, the less likely there will be undetected flaws.
- Telnet access for a managed switch has no business being enabled in a real-world environment.


### Host-Based Firewall

- **Host-based firewalls** protect individual hosts from being compromised when they're used in untrusted, potentially malicious environments.
- A host-based firewall plays a big part in reducing what's accessible to an outside attacker.
- **Bastion hosts/networks** are specifically hardened and minimized to reduce what's permitted to run on them.
  - They are exposed to the Internet; but they can be used like gateways or access portals into sensitive services like core authentication servers and domain controllers.
  - This would let you implement more secure authentication mechanisms and ACLs on the Bastion hosts without making it inconvenient for your entire company.

It's good practice to keep the network that VPN clients connect to separate using both subnetting and VLANs -- this gives you more flexibility to enforce security on these VPN clients. It also lets you build additional layers of defense.

Keep in mind that if the users of the system have administrator rights, then they have the ability to *change firewall rules and configurations*. If management tools allow it, you should also prevent the disabling of the host-based firewall.


### Logging and Auditing

- A **Security Information and Event Management System (SIEMS)** is like a centralized log server; it helps make sense of all the data.
- **Normalization** is the process of taking log data in different formats and converting it into a standardized format that's consistent with a defined log structure.
- A centralized log server helps secure the system from attack.

When looking at log data, pay attention to patterns and connections between traffic.

Once logs are centralized and standardized, you can write automated alerting based on *rules*.

Your log storage needs will vary based on the amount of systems being logged, the amount of detailed logs, and the rate at which logs are created.

Examples of logging servers and SIEMS solutions include rsyslog (open source), Splunk Enterprise Security, IBM Security Qradar, and RSA Security Analytics.


### Antimalware Protection

Lots of unprotected systems would be compromised *in a matter of minutes* if directly connected to the Internet without any safeguards or protections in place.

#### Antivirus
**Antivirus software** is signature-based; it has a database of signatures that identify known malware like the unique file hash of a malicious binary, or the file associated with an infection.

Antivirus software will monitor and analyze things, like new files being created or being modified on the system, in order to watch for any behavior that matches a known malware signature.

There are two problems with antivirus software:
1. They depend on signatures distributed by the antivirus software vendor;
2. They depend on the antivirus vendor discovering new malware and writing new signatures for newly-discovered threats.

- Why are antivirus programs still recommended as a core piece of security design?
  - *It protects against the most common attacks out there on the Internet.*
- An antivirus removes the background noise of the everyday Internet attacks; and lets you focus on the more important targeted or specific threats.

- Antivirus operates on a blacklist model.
- **Binary whitelisting software** operates off a whitelist model.
  - It uses a list of known good and trusted software, and only things on the list are permitted to run.
  - It will trust software using several mechanisms:
    - A unique cryptographic hash of binaries
    - A software-signing certificate


### Disk Encryption

**Full-disk encryption (FDE)** works by automatically converting data on a hard drive into a form that cannot be understood by anyone who doesn't have the key to "undo" the conversation.

- Without knowing the encryption password/key, the data on the hard drive is just meaningless gibberish.
- File encryption secures the data; but full-disk encryption secures the operating system, system files (PW Swap, etc), and the data.
- All FDE setups have an unencrypted partition on the disk, which holds critical boot files like the kernel and bootloader.
  - These files are vulnerable to an attacker with physical access, even in an FDE device.

**Secure Boot Protocol** is part of the UEFI specification.
- It uses public key cryptography to secure encrypted elements of the boot process, by integrating code signing and verification of the boot files.
- The *platform key* configures the secure boot, and is the public key corresponding to the private key used to sign the boot files.
  - This platform key is written to firmware, and is used at boot time to verify the signature of the boot files.
  - Only files correctly signed and trusted will be allowed to execute.

FDE tools include:
- Bit Locker (Microsoft)
- FileVault 2 (Apple)
- dm-crypt (Linux)
- TrueCrypt, VeraCrypt, PGP

In FDE, the master decryption is actually used to derive a user key; this way, the credentials can be changed without actually altering the master key.

- When you implement a full disk encryption solution at scale, it's super important to think about how to handle cases where passwords are forgotten.
  - This is why many enterprise solutions have a key escrow feature.
  - **Key escrow** allows the encryption key to be securely stored for later retrieval by an authorized party.

**Home directory** or **file-based encryption** only guarantees confidentiality and integrity of files protected by encryption.


## Application Hardening

### Software Patch Management

It's critical that you make sure that you install software updates and security patches in a timely way, in order to *defend your company's systems and networks*.

The best protection is to have a good system and policy in place for your company.

Management tools make this more approachable -- like SCCM (Microsoft) or puppet (Puppet Labs), which allow admins to get an overview of what software is installed across their system fleet.

Critical infrastructure devices should be approached carefully when you apply updates -- there's always the risk that a software update will introduce a new bug that might affect the functionality of the device.


### Application Policies

Policies define boundaries; and also educate users on how to use software more securely.

A common recommendation -- or even a requirement -- is to only support or require the latest version of a piece of software.

It's generally a good idea to disallow risky classes of software by policy. Things like file sharing software and piracy-relate software tend to be closely associated with malware infections.

Understand what your users need to do their jobs.

Browser extensions and add-ons also require their own policies.

Extensions that require full access to web sites visited can be risky, since the extension developer has the power to modify pages visited.


[Content](#content)




