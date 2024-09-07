# mKingdom-THM-writeup
This repository contains a comprehensive writeup for the mKingdom room on TryHackMe, detailing the steps taken to achieve complete ownership of the machine. Below is an overview of the process, including reconnaissance, exploitation, and privilege escalation.

## Start with nmap scan 

```bash
sudo nmap <ip-address>
```

![image](https://github.com/user-attachments/assets/4a0e9e63-3c9a-4e79-8823-51a22a9fe50b)

The Nmap scan for the IP address 10.10.99.81 shows that the host is up with a latency of 0.17 seconds. It has one open port, 85/tcp, which is running the mit-ml-dev service, while 999 other TCP ports are closed.

## Access the webpage on <ip-address>:85

![image](https://github.com/user-attachments/assets/76b1b795-ba4f-43ff-94ad-cec3ca077fab)

## I decided to run gobuster

[Download the wordlist here](https://github.com/digination/dirbuster-ng/blob/master/wordlists/big.txt)

```bash
gobuster dir -u http://<ip-address>:85 -w /home/user/wordlist/dirb/big.txt -x php,html,aspx,jsp
```
![image](https://github.com/user-attachments/assets/27a45576-b71c-41db-8b0a-0e15e5ac6d05)

### I accessed the /app through http://<ip-address>/app/ and clicked on jump button which landed on the following page

![image](https://github.com/user-attachments/assets/b5415832-7751-4436-ab28-3a73169f1b62)




