# HACK THE BOX - OPTIMUM WRITEUP

Lets enumerate the box with nmap

![I](pics/1.png)

We can see that it has only one port open

Its a Web service on port 80

On viewing it,

![I](pics/2.png)

It says it is a "HttpFileServer 2.3"

But we don't know what type of file server that they mentioned

By clicking on it, I was redirected to another site

![I](pics/3.png)

So we can conclude that it is "Rejetto" file server

Lets search for Rejetto exploit in searchsploit

![I](pics/4.png)

Lets look for it in metasploit

![I](pics/5.png)

Configure the exploit and run it

We get SHELL

![I](pics/6.png)

We are in user "OPTIMUM\kostas"

Lets search for user flag

![I](pics/7.png)

Its time to escalate our privileges

Lets use local exploit suggester

![I](pics/8.png)

 Here we can see two exploits shown as vulnerable

But some of the exploits are false positive

We cannot blindly follow a particular exploit

So lets do trial and error to cross check these 

![I](pics/9.png)

So our first suggested exploit "bypassuac_eventvwr" got failed.

So its a false positive

Lets go for our second exploit 

![I](pics/10.png)

We got #ROOT

![I](pics/11.png)

Own the box


