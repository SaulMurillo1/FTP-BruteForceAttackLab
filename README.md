<h1>FTP Brute-Force/Dictionary Attack</h1>


<h2>Description</h2>
This project consists of using the Hydra and Nmap Linux tools to perform dictionary/brute-force password attacks in order to obtain access to the target FTP server. 
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
Commands: nmap 192.189.261.3 -p 21 -sV -O
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
- We can see that the hydra tool found 7 valid passwords with the username included as well.
<br/>
<br/>
Commands: hydra -L /usr/share/metasploit-framework/data/wordlists/common_users.txt -P /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt 192.189.216.3 ftp
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




</p>
