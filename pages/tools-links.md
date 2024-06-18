# 🛠️ Tools and Links

List of tools used in information security and useful links.

# 🔎 Information gathering

### Google dorks

| Dork | Description | Example |
| --- | --- | --- |
| Site | Filter the results to a specific site | `site:www.elsfoo.com` |
| Filetype | Search all documents with the specific file extension | `filetype:pdf google` |
| Inurl | Find content present in a given URL | `inurl:/wp-admin` |
| Intitle | Search sites with the informed title | `intitle:Foo` |
| Intext | Looks for all sites that contains the word in the content | `intext:Foo` |
| Cache | Show the content of the cached page in google | `cache:www.elsfoo.com` |

More examples in: [Google Hacking Database](https://www.exploit-db.com/google-hacking-database)

### Leaked passwords database

- [LeakCheck](https://leakcheck.net/)
- [Dehashed](https://www.dehashed.com/)

Both sites are **paid**.

# 🗺️ Infra mapping

Details of CLI tools are in [Information Gathering](#information-gathering.md) page. Some useful sites or repositories are:

- [DNS Dumpster](https://dnsdumpster.com/)
- [Shodan](https://www.shodan.io/)
- [theHarvester](https://github.com/laramies/theHarvester)
- [Subfinder](https://github.com/projectdiscovery/subfinder)
- [httpx](https://github.com/projectdiscovery/httpx)

### Vulnerabilities scan

- [Nessus](https://pt-br.tenable.com/products/nessus)
- [ZAP](https://www.zaproxy.org/download/)

# 🌐 Web

- [Burp Suite](https://portswigger.net/burp)
- [OWASP](https://cheatsheetseries.owasp.org/index.html)
- [SSRFmap](https://github.com/swisskyrepo/SSRFmap)
- [Gopherus](https://github.com/tarunkant/Gopherus)
- [Top HackerOne Reports](https://github.com/reddelexc/hackerone-reports/blob/master/tops_by_bug_type/TOPSSRF.md)
- [XSS Game](https://xss-game.appspot.com/)

# 🔐 Password attacks

- [Hash Identifier](https://gitlab.com/kalilinux/packages/hash-identifier)

### Brute force tools

- [Hashcat](https://hashcat.net/hashcat/)
- [John the Ripper](https://github.com/openwall/john)
- [Aircrack](https://www.aircrack-ng.org/)

### Wordlists

- [WeakPass](https://weakpass.com/wordlist/1948)
- [Rockyou](https://github.com/brannondorsey/naivehashcat/releases/download/data/rockyou.txt)
- [Crunch](https://github.com/jim3ma/crunch)

# 📲 Android

### Decompilation

- [Apktool](https://apktool.org/)
- [Dex2Jar](https://github.com/pxb1988/dex2jar)
- [Java Decompiler](https://java-decompiler.github.io/)
- [Ghidra](https://www.ghidra-sre.org/)

### Others

- [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF)
- [ApkPure](https://apkpure.com/br/)
- [ApkMirror](https://www.apkmirror.com/)
- [Ovaa](https://github.com/oversecured/ovaa)

# 🧲 Exploit

- [Metasploit](https://www.metasploit.com/)
- [Darknet Diaries](https://darknetdiaries.com/episode/114/)
- [Metasploit Unleashed](https://www.offensive-security.com/metasploit-unleashed/)

# 📎 Windows and AD

### Enumeration

- [Kerbrute](https://github.com/ropnop/kerbrute)
- [Mitre](https://attack.mitre.org/techniques/T1557/)
- [ADExplorer](https://learn.microsoft.com/en-us/sysinternals/downloads/adexplorer)
- [LDAPdomaindump](https://github.com/dirkjanm/ldapdomaindump)
- [BloodHound](https://github.com/BloodHoundAD/BloodHound)
- [PowerView](https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1)

### Kerberoast

- [Kerberoast Mitre pt1](https://attack.mitre.org/techniques/T1558/003/)
- [Kerberoast Mitre pt2](https://attack.mitre.org/techniques/T1558/004/)
- [Invoke Kerberoast](https://github.com/EmpireProject/Empire/blob/master/data/module_source/credentials/Invoke-Kerberoast.ps1)
- [Impacket](https://github.com/fortra/impacket)

### Dump

- [Mitre](https://attack.mitre.org/techniques/T1003/)
- [Credential Access and Credential Dumping](https://www.ired.team/offensive-security/credential-access-and-credential-dumping)

### Lateral movement

- [Lateral Movement](https://www.ired.team/offensive-security/lateral-movement)

### C2 via DNS

- [dnscat2](https://github.com/iagox86/dnscat2)
- [dnscat2-powershell](https://github.com/lukebaggett/dnscat2-powershell)

# 🐧 Linux

### Enumeration

```shell
> id
> hostname
> uname -a
> /etc/issue
> /etc/passwd
> /etc/*-release
> dpkg -l
```

### Kernel

[CVEs](https://www.linuxkernelcves.com/cves)

### Sudo and SUID

```shell
> sudo -l
> rws-rwx-rwx #(SUID permission)
> find / -perm -u=s –type f 2>/dev/null
```

- [GTFobins](https://gtfobins.github.io/)

### Cron jobs

```shell
> cat /etc/crontab
```

### Path

```shell
> echo $PATH
> find / -writable 2>/dev/null
```