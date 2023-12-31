<h1>FTP Brute-Force/Dictionary Attack</h1>


<h2>Description</h2>
This project consists of using the Hydra and Nmap Linux tools to perform dictionary/brute-force password attacks in order to obtain access to the target FTP (Port 21) server. 
<br />
<br />
<br />

Disclaimer: The Kali Linux user machine and target machine used in this project was provided to me by INE for educational purposes. The misuse of the information in this project lab can result in criminal charges brought against the individual/individuals in question.
<br />


<h2>Languages and Utilities Used</h2>

- <b>nmap</b>
- <b>hydra</b>


<h2>Environments Used </h2>

- <b>Kali Linux</b>

<h2>Project walk-through:</h2>

<p align="left">
Ping target machine to verify that it is active. After verifying target machine as active, perform an nmap port scan: <br/>
<br/>
- INE has provided me with Kali Linux GUI & target machine (target machine is one ip address above from mine).  I will run an ip a command to verify my own ip address. Then, I'll run an nmap scan to possibly discover any open ports. 
<br/>
- We can see below that port 21, commonly known as FTP, is in fact open. 
<br/>
<br/>
Commands: ip a
<br/>
ping 192.189.216.3
<br/>
nmap 192.189.216.3
<br/>
<br/>
<img src="https://i.imgur.com/47nd3RG.png" height="80%" width="80%" alt="SMB Nmap Scripting" class="center"/>
<br />
<br />
<br />
<br />
<br />
<br />
<br />
Run nmap scan that will enumerate the FTP version and OS of the target machine: <br/>
<br/>
- It looks like the version for port 21 is ProFTPD 1.3.5a. We can also see that the nmap scan did an aggressive OS scan and it guessed Linux 2.6.32 with a 96% certainty. 
<br/>
<br/>
Command: nmap 192.189.261.3 -p 21 -sV -O
<br/>
<br/>
<img src="https://i.imgur.com/mPPUtmq.png" height="80%" width="80%" alt="SMB Nmap Scripting" class="center"/>
<br />
<br />
<br />
<br />
<br />
<br />
<br />
Utilize the hydra tool to perform a brute-force password attack on the target FTP server: <br/>
<br/>
- Hydra is an open source, password brute-forcing tool designed around flexibility and high performance in online brute-force attacks.
<br/>
- In the hydra command below, two wordlists were used to help brute-force the passwords which were found. The first wordlist (-L) "common_users.txt" is a wordlist of common usernames, while the second wordlist (-P) "unix_passwords.txt" is a wordlist of common passwords. 
<br/>
- We can see that the hydra tool found 7 valid passwords with the username included as well.
<br/>
<br/>
Command: hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt 192.189.216.3 ftp
<br/>
<br/>
<img src="https://i.imgur.com/Ht9U4F3.png" height="80%" width="80%" alt="SMB Nmap Scripting" class="center"/>
<br />
<br />
<br />
<br />
<br />
<br />
<br />
Check if FTP server allows users to log in anonymously: <br/>
<br/>
- A user can try to log into the FTP server anonymously by using the command below and not entering anything for both the username and password. We can see below that the "Login failed", which means this FTP server does not allow users to log in anonymously.
<br/>
<br/>
Command: ftp 192.189.216.3
<br/>
<br/>
<img src="https://i.imgur.com/4pEF68n.png" height="80%" width="80%" alt="SMB Nmap Scripting" class="center"/>
<br />
<br />
<br />
<br />
<br />
<br />
<br />
Now use one of the usernames and passwords that we found in the prior step when conducting a brute-force password attack using Hydra: <br/>
<br/>
- This time, I logged in with the sysadmin:654321 username/password which was found in a prior step. We can see that I was allowed access to the FTP server and was able to find a text file name "secret.txt". I was also able to view the information in the secret.txt file.
<br/>
<br/>
Command: ftp 192.189.216.3
<br/>
sysadmin
<br/>
654321
<br/>
ls
<br/>
get secret.txt
<br/>
exit
<br/>
ls
<br/>
cat secret.txt
<br/>
<br/>
<img src="https://i.imgur.com/VZI2I36.png" height="80%" width="80%" alt="SMB Nmap Scripting" class="center"/>
<br />
<br />
<br />
<br />
<br />
<br />
<br />
Use Nmap tool as another way to perform a brute-force password attack on the target FTP server: <br/>
<br/>
- We can see below that nmap can also be used to perform a brute-force attack by using a script called ftp-brute. 
<br/>
<br/>
Command: nmap 192.189.216.3 -p 21 --script ftp-brute --script-args userdb=/root/users
<br/>
<br/>
<img src="https://i.imgur.com/s4oTXPc.png" height="80%" width="80%" alt="SMB Nmap Scripting" class="center"/>
<br />
<br />
<br />
<br />
<br />
<br />
<br />




</p>
