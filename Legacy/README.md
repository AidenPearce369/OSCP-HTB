# HACK THE BOX - LEGACY WRITEUP

Lets enumerate the box with nmap

![I](pics/1.png)

We can see 2 ports are open

And we have a SAMBA port

Lets enumerate the SAMBA port with "smbmap"

![I](pics/2.png)

It seems like an authentication failure

Using enum4linux and smbclient results the same

Since it is a Windows box, there is a high chance of having SAMBA exploits

So lets scan for vulnerabilities in nmap

![I](pics/3.png)

These are all the "nse" scripts available for scanning SMB vulns using nmap

Lets run the scan

![I](pics/4.png)

Here we got "smb-vuln-ms08-067" VULNERABLE

Lets use this exploit from metasploit,

You can also use custom exploit from ExploitDB,Searchsploit

But i prefer metasploit because its well maintained

Lets search the exploit in metasploit

![I](pics/5.png)

Configure the exploit

![I](pics/6.png)

Run the exploit 

![I](pics/7.png)

We got the SHELL

Lets check the privileges

![I](pics/8.png)

We are in "NT AUTHORITY/SYSTEM"

Which is an admin level privilege

Lets scan for our flags

![I](pics/9.png)

Hunt the flags

![I](pics/10.png)

![I](pics/11.png)

Own the box
