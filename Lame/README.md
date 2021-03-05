# HACK THE BOX - LAME WRITEUP

This is an easy linux box based on CVE

Scan and enumerate the machine with nmap

![I](pics/1.png)

Here we can see,

FTP,SSH & Samba ports are open

Obviously we can see that FTP has enabled Anonymous login

So lets check for any info on that

![I](pics/2.png)

No usefule info,just a rabbit hole

Lets use enum4linux to enumerate SAMBA

NOTE:
Whenever you see a SAMBA port,try to enumerate with 'enum4linux'
enum4linux is a best tool used for SAMBA Recon and AD attacks

![I](pics/3.png)

We didn't get any info from SAMBA also

It seems like there is an authentication problem

Lets search for vsFTPd in searchsploit

![I](pics/4.png)

There is an famous backdoor exploit..lets try this in metasploit

![I](pics/5.png)

Configure the options and start the exploit

![I](pics/6.png)

It doesn't work

So lets search an exploit from SAMBA in searchsploit

![I](pics/7.png)

Here we can see a popular exploit form SAMBA which is in the given version range,lets try this

Lets configure and run the exploit 

![I](pics/8.png)

We got $SHELL

Lets get our flags,

![I](pics/9.png)

Although we used metasploit for this shell,

We can also get shell through Netcat using a command passed through the metasploit exploit

![I](pics/10.png)

If there is correct authentication on SAMBA,

You can pass this to get a reverse shell

INFO:
The nohup command executes another program specified as its argument and ignores all SIGHUP (hangup) signals. SIGHUP is a signal that is sent to a process when its controlling terminal is closed.



