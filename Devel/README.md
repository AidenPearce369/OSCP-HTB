# HACK THE BOX - DEVEL WRITEUP

Lets enumerate the box with nmap

![I](pics/1.png)

Since Anonymous FTP Login is allowed

![I](pics/2.png)

No useful info from that

Lets check the website

![I](pics/3.png)

Lets use Gobuster to find directories

![I](pics/4.png)

No useful directories from the wordlist

Lets search for any exploit in Searchsploit

![I](pics/5.png)

And analyzing the source code from the website's main page

![I](pics/6.png)

We can see that "Welcome.png" from the FTP directory

So the website is in running from FTP Root Directory

Lets see we can upload a file in FTP Anonymous login

![I](pics/7.png)

So we can upload files, lets try uploading a aspx shell since its running in asp_client

![I](pics/8.png)

Configuring our listener

![I](pics/9.png)

Now,lets upload our shell.aspx to FTP

![I](pics/10.png)

Loading the page in website triggers the reverse shell and starts the meterpreter stage

![I](pics/11.png)

We got SHELL

![I](pics/12.png)

Here we are in the "APPPOOL/WEB" user,

Which is not a privileged user

So lets try the "local exploit suggester" to find a suitable exploit for privilege escalation

![I](pics/13.png)

Here we can see many exploits shown as vulnerable

But some of the exploits are false positive

We cannot blindly follow a particular exploit

So lets do trial and error to cross check these

![I](pics/14.png)

So our first suggested exploit "bypassuac_eventvwr" got failed.

So its a false positive

Lets go for our second exploit

![I](pics/15.png)

In this exploit "ms10_015_kitrap0d" we got a meterpreter shell

And the user is "NT AUTHORITY/SYSTEM"

Which is a "Admin" level privileged user

Lets hunt for flags

![I](pics/16.png)

User flag

![I](pics/17.png)

Root flag

![I](pics/18.png)

Own the box