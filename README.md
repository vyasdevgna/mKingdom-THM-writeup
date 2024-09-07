# mKingdom-THM-writeup
This repository contains a comprehensive writeup for the mKingdom room on TryHackMe, detailing the steps taken to achieve complete ownership of the machine. Below is an overview of the process, including reconnaissance, exploitation, and privilege escalation.



### Start with nmap scan 

```bash
sudo nmap <ip-address>
```

![image](https://github.com/user-attachments/assets/4a0e9e63-3c9a-4e79-8823-51a22a9fe50b)

The Nmap scan for the IP address shows that the host is up with a latency of 0.17 seconds. It has one open port, 85/tcp, which is running the mit-ml-dev service, while 999 other TCP ports are closed.



### Access the webpage on :85

![image](https://github.com/user-attachments/assets/76b1b795-ba4f-43ff-94ad-cec3ca077fab)



### I decided to run gobuster

[Download the wordlist here](https://github.com/digination/dirbuster-ng/blob/master/wordlists/big.txt)

```bash
gobuster dir -u http://<ip-address>:85 -w /home/user/wordlist/dirb/big.txt -x php,html,aspx,jsp
```
![image](https://github.com/user-attachments/assets/27a45576-b71c-41db-8b0a-0e15e5ac6d05)



### I accessed the /app through "http://ip-address/app/" and clicked on jump button which landed on the following page

![image](https://github.com/user-attachments/assets/b5415832-7751-4436-ab28-3a73169f1b62)



### Exploring the Blog page i found a blog posted by the admin

![image](https://github.com/user-attachments/assets/5c237961-e386-4358-ac42-cd425a5c3e00)



### I desided to use admin username and tried to login 

![image](https://github.com/user-attachments/assets/7587ddf2-7ef3-43b4-aca1-d5f35dfdd63e)



### I tried some random passwords and luckily 'password' worked

![image](https://github.com/user-attachments/assets/fb2af502-a03a-474d-b9a3-326c60769fda)



### Admin panel 

![image](https://github.com/user-attachments/assets/22a1f533-3df8-4a8c-9c68-bae1ef1fd7a4)



### This webapp uses Concrete CMS 8.5.2

![image](https://github.com/user-attachments/assets/bc7272bb-4183-4289-867e-cfb683b8391a)

[Get Wappalyzer to detect the technology used](https://chromewebstore.google.com/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg)



### There’s an existing RCE vulnerability in Concrete CMS 8.5.2

![image](https://github.com/user-attachments/assets/04043958-d4a9-491f-8e8a-21b3b6372fae)



#### Since I have admin rights i can navigate to System & Settings-> Allowed file types, and add ‘.php’ in the allowed file types

![image](https://github.com/user-attachments/assets/85febb9a-c864-410d-a30e-e4ff7def015d)




### I went to Files -> File Manager and uploaded a php shell file

[I used this reverse shell file](wget https://raw.githubusercontent.com/WhiteWinterWolf/wwwolf-php-webshell/master/webshell.php)

![image](https://github.com/user-attachments/assets/53ad07a7-c823-42d5-a0b7-fd53766ebf86)

![image](https://github.com/user-attachments/assets/271795f1-5752-4ad6-a645-94d310b2d40b)



### After clicking on close a prompt will be vivible with the php file link , click on it and open it 

![image](https://github.com/user-attachments/assets/1faeac29-a0a5-4924-95f0-3761e3901a26)



### This utility will be available once you open the link and you can exicute commands straight from it

![image](https://github.com/user-attachments/assets/9e9c3023-c60b-4721-b2d1-03352bfa906f)



### Example









