# ⛏️ Information Gathering

## 💭 Passive Reconnaissance

In passive reconnaissance, you rely on publicly available knowledge. It is the knowledge that you can access from publicly available resources without directly engaging with the target.

### whois

It is a request and response protocol that follows the [RFC 3912](https://www.ietf.org/rfc/rfc3912.txt) specification. A **WHOIS** server listens on **TCP** port **43** for incoming requests. The domain registrar is responsible for maintaining the **WHOIS** records for the domain names it is leasing.

```shell
whois domain.com
```

### nslookup

Find the IP address of a domain name using `nslookup`, which stands for Name Server Look Up

| Query type | Result |
| --- | --- |
| A | IPv4 Addresses |
| AAAA | IPv6 Addresses |
| CNAME | Canonical Name |
| MX | Mail Servers |
| SOA | Start of Authority |
| TXT | TXT Records |

```shell
nslookup -type=MX domain.com 8.8.8.8
```

### dig

For more advanced DNS queries and additional functionality, you can use `dig`, the acronym for “Domain Information Groper”. You would use `dig DOMAIN_NAME TYPE`.

```shell
dig domain.com MX
```

## Online Tools:

- [DNSDumpster](https://dnsdumpster.com/)
- [Shodan.io](https://tryhackme.com/room/shodan)

## 🗯️ Active Reconnaissance

Active reconnaissance requires you to make some kind of contact with your target. This contact can be a phone call or a visit to the target company under some pretence to gather more information, usually as part of social engineering. Alternatively, it can be a direct connection to the target system, whether visiting their website or checking if their firewall has an SSH port open.

### DevTools

While browsing a web page, you can press `Ctrl+Shift+I` on a PC to open DevTools on the browser. For instance, you can view and even modify the JavaScript (JS) files, inspect the cookies set on your system and discover the folder structure of the site content.

**Wappalyzer** provides insights about the technologies used on the visited websites. Such extension is handy, primarily when you collect all this information while browsing the website like any other user.

### ping

The primary purpose of ping is to check whether you can reach the remote system and that the remote system can reach you back.

```shell
ping -c 10 MACHINE_IP
```

### traceroute

As the name suggests, the traceroute command *traces the route* taken by the packets from your system to another host. The purpose of a traceroute is to find the IP addresses of the routers or hops that a packet traverses as it goes from your system to a target host. This command also reveals the number of routers between the two systems. It is helpful as it indicates the number of hops (routers) between your system and the target host.

```shell
traceroute MACHINE_IP
```

### telnet

You can use Telnet to connect to any service and grab its banner. Using **telnet**, you can connect to any service running on TCP and even exchange a few messages unless it uses encryption.

```shell
telnet MACHINE_IP PORT
```

Let’s say we want to discover more information about a web server, listening on port 80. We connect to the server at port 80, and then we communicate using the HTTP protocol. You don’t need to dive into the HTTP protocol; you just need to issue `GET / HTTP/1.1`. To specify something other than the default index page, you can issue `GET /page.html HTTP/1.1`, which will request `page.html`.

### netcat

Netcat supports both TCP and UDP protocols. It can function as a client that connects to a listening port; alternatively, it can act as a server that listens on a port of your choice.

```shell
# Netcat as CLIENT
nc MACHINE_IP PORT
```

```shell
# Netcat as SERVER
nc -lvnp PORT_NUMBER
```

| option | meaning |
| --- | --- |
| -l | Listen mode |
| -p | Specify the Port number |
| -n | Numeric only; no resolution of hostnames via DNS |
| -v | Verbose output (optional, yet useful to discover any bugs) |
| -vv | Very Verbose (optional) |
| -k | Keep listening after client disconnects |

### nmap

Nmap can be accessed by typing `nmap` into the terminal command line, followed by some of the "switches" (command arguments which tell a program to do different things).

When port scanning with Nmap, there are three basic scan types. These are:

- TCP Connect Scans (`sT`)
- SYN "Half-open" Scans (`sS`)
- UDP Scans (`sU`)

SYN scans (`-sS`) are used to scan the TCP port-range of a target or targets; SYN scans are sometimes referred to as "*Half-open"* scans, or *"Stealth"* scans.

It's usually good practice to run an Nmap scan with `--top-ports <number>` enabled. For example, scanning with  `nmap -sU --top-ports 20 <target>`. Will scan the top 20 most commonly used UDP ports, resulting in a much more acceptable scan time.

To perform a ping sweep, we use the `-sn` switch in conjunction with IP ranges which can be specified with either a hypen (`-`) or CIDR notation. i.e. we could scan the `192.168.0.x` network using:

```shell
nmap -sn 192.168.0.1-254
# or
nmap -sn 192.168.0.0/24
```

The `-sn` switch tells Nmap not to scan any ports -- forcing it to rely primarily on ICMP echo packets (or ARP requests on a local network, if run with sudo or directly as the root user) to identify targets.

**nmap scripts**

The **N**map **S**cripting **E**ngine (NSE) is an incredibly powerful addition to Nmap, extending its functionality quite considerably. NSE Scripts are written in the *Lua* programming language, and can be used to do a variety of things: from scanning for vulnerabilities, to automating exploits for them.

There are many categories available. Some useful categories include:

- `safe`:- Won't affect the target
- `intrusive`:- Not safe: likely to affect the target
- `vuln`:- Scan for vulnerabilities
- `exploit`:- Attempt to exploit a vulnerability
- `auth`:- Attempt to bypass authentication for running services (e.g. Log into an FTP server anonymously)
- `brute`:- Attempt to bruteforce credentials for running services
- `discovery`:- Attempt to query running services for further information about the network (e.g. query an SNMP server).

A more exhaustive list can be found [here](https://nmap.org/book/nse-usage.html).

**Firewall Evasion with nmap**

`-Pn`, tells Nmap to not bother pinging the host before scanning it. This means that Nmap will always treat the target host(s) as being alive, effectively bypassing the ICMP block

The following switches are of particular note:

- `f`:- Used to fragment the packets (i.e. split them into smaller pieces) making it less likely that the packets will be detected by a firewall or IDS.
- An alternative to `f`, but providing more control over the size of the packets: `-mtu <number>`, accepts a maximum transmission unit size to use for the packets sent. This *must* be a multiple of 8.
- `-scan-delay <time>ms`:- used to add a delay between packets sent. This is very useful if the network is unstable, but also for evading any time-based firewall/IDS triggers which may be in place.
- `-badsum`:- this is used to generate in invalid checksum for packets. Any real TCP/IP stack would drop this packet, however, firewalls may potentially respond automatically, without bothering to check the checksum of the packet. As such, this switch can be used to determine the presence of a firewall/IDS.

**nmap examples:**

Perform an Xmas scan on the first 999 ports of the target:

```shell
nmap -p1-999 -sX IP_NUMBER -vv
```

Perform a TCP SYN scan on the first 5000 ports of the target

```shell
nmap -p1-5000 -sS 10.10.147.47 -vv -Pn
```