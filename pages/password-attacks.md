# Passord Attacks

Passwords, while fundamental to digital security, are also a primary target for cybercriminals. These attacks, often the first step in a larger breach, exploit vulnerabilities in password creation and management. Common techniques include brute-forcing, where attackers systematically try countless combinations, and dictionary attacks, which use lists of common words or phrases. Additionally, phishing scams manipulate users into revealing their credentials. To protect against these threats, individuals and organizations must prioritize strong, unique passwords, coupled with password managers and multi-factor authentication.


## Common Types of Password Attacks

- **Brute-force attacks**: These involve systematically trying every possible combination of characters to guess a password. While time-consuming, powerful computers can crack relatively short or simple passwords quickly.
- **Dictionary attacks**: Attackers use lists of common words, phrases, or names to guess passwords. This method is often more efficient than brute-forcing.
- **Rainbow table attacks**: Precomputed tables of encrypted passwords are used to quickly match passwords totheir corresponding hashes.
- **Phishing attacks**: Social engineering is used to trick users into revealing their passwords through fraudulent emails, websites, or messages.
- **Keylogging**: Malicious software records keystrokes to capture passwords as they are typed


## How to break root password on Linux

There are 2 ways to break root password on Linux. First, is `SINGLE MODE`, using **grub**, while second is `SHELL MODE`, mounting the disk partition.

### Single Mode
1. The first step is to restart the machine (or VM).
2. When GRUB appears, press any key so that you can select the kernel.
3. Select the kernel that contains the syllable `RO` (which appears at the end of the line), select it and press the `e` key.
4. On the next screen enter the same line at the end:
```shell
rw init=/bin/bash
```
5. After pressing enter, and you will be redirected to the previous screen, then press `b` key.
6. If you have done everything correctly, it will load some commands and the bash shell will appear as root on the command line. At this point you can simply change the root password by running the `passwd` command
```shell
passwd root
```
7. Now you can login with the new password.
