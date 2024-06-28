# 🛄 Protocols
## 📬 Application Layer Protocols

### 1. HTTP (HyperText Transfer Protocol)
- Used for data transfer on the World Wide Web.
- Underlying protocol that defines how messages are formatted and transmitted.
- HTTPS is the secure version of HTTP that uses SSL/TLS to encrypt communication.

### 2. FTP (File Transfer Protocol)
- Used for transferring files between a client and a server on the network.
- Supports user authentication with password.

### 3. SMTP (Simple Mail Transfer Protocol)
- Standard protocol for sending e-mails over the Internet.
- Usually used in combination with POP3 or IMAP.

v 4. POP3 (Post Office Protocol version 3)
- Used by email clients to retrieve emails from an email server.
- Emails are usually downloaded and deleted from the server.

### 5. IMAP (Internet Message Access Protocol)
- Allows e-mail clients to access and manipulate e-mail messages as if they were on the e-mail server.
- Supports online and offline operations, synchronization.

### 6. DNS (Domain Name System)
- Used to resolve host names to IP addresses (Translates human-friendly domain names into numerical IP addresses).
- Essential for the functioning of the Internet.
- Supports DNSSEC.

### 7. DHCP (Dynamic Host Configuration Protocol)
- Automatically assigns IP addresses and other network settings to devices on a network.
- Facilitates the administration of IP addresses in large networks.
- Supports DHCPv6 and DHCPv4.

### 8. SNMP (Simple Network Management Protocol)
- Used to collect information from devices on a network, such as routers and switches, for management and monitoring purposes.

### 9. Telnet
- Allows communication with another (remote) host via command terminal.
- Considered insecure due to lack of encryption; preferable to use SSH.

### 10. SSH (Secure Shell)
- Used for remote login and command execution.
- Supports password authentication
- Protocol for secure network operations via command terminal, replacing Telnet.
- It provides a secure channel over an unsecured network.

### 11. RTP (Real-time Transport Protocol)
- Used for audio and video streaming.

### 12. SIP (Session Initiation Protocol)
- Used for signaling and controlling multimedia communications, such as voice and video calls over IP.

### 13. XMPP (Extensible Messaging and Presence Protocol)
- XML-based protocol for instant messaging and the presence of information.

### 14. LDAP (Lightweight Directory Access Protocol)
- Used to access and maintain distributed directory services.
- Supports Active Directory and Open Directory.

---
---

## 4️⃣ IPV4
Connectionless network protocol based on packet switching.

It operates on a least-effort delivery model, in which it does not guarantee delivery, nor does it guarantee the correct sequence or avoid duplicate delivery.
It uses a **32-bit** address space, which is enough for around 4.3 billion addresses.

An IPv4 address consists of four octets, represented in dotted decimal format, such as `192.168.1.1`.

The first bits of each octet determine the type of address, such as class **A**, class **B**, class **C** or class **D** (class **E** is reserved).

#### Class A
The first bits of the first octet are 0 (zero), and the last three octets are used to address the hosts.

#### Class B
The first two bits of the first octet are 10 (ten), and the last two octets are used to address the networks, and the last two octets are used to address the hosts.

#### Class C
The first three bits of the first octet are 110 (sixteen), and the last octet is used to address the networks, and the last two octets are used to address the hosts.

#### Class D
The first four bits of the first octet are all 1 (one), and are used to address multicast groups.

#### _Class E_
_The first four bits of the first octet are all 1 (one), and are reserved for future use._


## 6️⃣ IPV6
Connectionless network protocol based on packet switching.

It operates on a best-effort delivery model, in which it does not guarantee delivery, nor does it guarantee the correct sequence or avoid duplicate delivery.

It uses a **128-bit** address space, which is sufficient to provide a unique address for every device on Earth.

An IPv6 address consists of 128 bits, represented in hexadecimal format as `2001:0db8:0000:0000:0000:ff00:0042:8001`.

IPv6 addresses are divided into two main fields: the **network prefix** and the **node identifier**. 
The network prefix identifies the network address and the host address to which the device belongs, and the node identifier identifies the device within the network.

> Netmasks are not used in IPv6.

### Simplifying the IPV6 address
The IPV6 addresses can be simplified. 
For example:

`2001:0db8:85a3:0000:0000:8a2e:0370:7334`

Can be simplified to:

`2001:db8:85a3:0:0:8a2e:370:7334`

In this case, the leading zeros in each numeric block have been omitted to make the address shorter and more readable. This simplification is allowed and does not affect the interpretation of the address.



