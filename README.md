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




</p>
