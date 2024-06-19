# 🔐 Web - Authentication

### What is authentication?

It’s the process to prove the identity of someone or something, by a password, fingerprint, token, etc.

## 🕵🏻‍♂️ Authentitcation Factors:

- **Knowledge Factor**: It’s something that you know. (*eg. password, security questions answers*)
- **Possession Factor**: It’s something that you have. (*eg. cellphone, physical token*)
- **Inherence Factor**: It’s what you are. (*eg. fingerprint, facial and retina recognition*)

### Vulnerabilities:

| Based in passwords | Based in MFA |
| --- | --- |
| User enumeration | Brute force in 2FA |
| Brute force | Token bypass |

Their impacts can be: 

- Access to confidential information.
- Acess to admin resources.
- Creation of new attack surfaces

## 1️⃣ Burp Suite: User Enumeration

1. On **Proxy** tab, select the **/login** request, then right click on it and **Send to Intruder**.
2. On **Intruder** tab, in **Positions**, select the username value of the request and click **Add**.
3. Navigate to **Payloads** tab, and on **Payload type**, choose **Simple List**.
4. Press **Load…** to load the wordlist for usernames.
5. Then click on “**Start attack**”.

Looking at the **Length** of the responses, some of them will be different. So, taking a look on the response, its possible to confirm that it returned “**Wrong password**” for example, meaning that its a **valid** username.

![enum](/pages/imgs/user-enum.png)

## 💪🏻 Burp Suite: Brute Force

1. Knowing a valid username, change its value in **Proxy** > **Positions** tab.
2. Now select the password value and click **Add**.
3. **Clear** the payload settings and **Load…** the passwords wordlist.
4. Then click on “**Start attack**”.

Generally, when you find the password and log in, the status code will be **different** from **200**, for example (**302**) and the request **length** will be **different**.

![brute](/pages/imgs/brute-force.png)