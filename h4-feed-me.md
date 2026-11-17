# h4 Feed me

This is the fourth assignment for the course - https://terokarvinen.com/cyber-security/

---

### a) Installing a feed reader and adding feeds

I have installed and documented FeedFlow in my earlier assignment h2: https://github.com/mirosec/cyber-security/blob/main/h2-cyber-security-scene.md

### x) Why install a feed reader?

The main advantage a feed reader offers is simplicity: you only get the news from sources you selected and nothing else. There are no ads or recommended articles, it's just pure, distilled
news content for you to read in the order it was published. You have complete control on what you want to add to a feed reader. A feed reader also has a definitive end, there is no endless scrolling. Privacy is also improved when you don't have to log onto a news website on a browser just to read the latest news. 


<img width="1000" height="650" alt="image" src="https://github.com/user-attachments/assets/7545f504-f19d-46f0-90b0-af54cd50effa" />


### b, c, d) Adding more cyber security feeds

Finding new blogs to follow was super easy, I googled **cyber security blogs for rss feed** and started adding them by copying the link address for each site to the Feed URL field (shown in screenshot). I chose a few vendor blogs (Cisco Talos, Palo Alto unit 42 and Microsoft Security Blog) since they are relevant to my work. We provide networks solutions based on their technology. 

For general cyber security news I chose theregister.com because it's base in UK so it's good to have some variety to all the US-based sites. Finally I added darkreading for general news on cyber security, I opened the site and skimmed through a few articles to see what it was like and it seemed have quality news articles.

---

### y) Cyber security is serious business - Dangers of port scanning

This is a summary of a courtcase about port scanning a bank's network and its consequences (Supreme court of Finland, case Osuuspankkikeskus port scan KKO:2003:36) Have a brief look, summarize the key thing in a couple of bullets or sentences. 

**Port scanning** is a technique hackers use to search for vulnerabilities on the public side of a target network. Once a vulnerable port has been found it can potentially be used to gain unauthorized access to the target network (https://www.fortinet.com/resources/cyberglossary/what-is-port-scan)

- In 1998 17-year old cyber criminal A ran a port scanning software to scan the network of the bank OPK
- The scan did not pass the banks firewall, but caused damage through incurring costs in expert services required to analyze the attack
- A tried to plead to ignorance and deny any intention to use the port scan to breach the network through a vulnerable port
- The court rejected A's plea on the basis of A being experienced in IT - A should have known port scanning to be illegal
- A was sentenced to pay restitution based on the increased cyber security costs to the OPK bank

What we can take away from this case is that **pleading to ignorance won't save you from being prosecuted**. You can't simply say that you didn't know what you were doing. It did seem a bit overkill to hit a 17 year-old with a 18 000€ fee, although the court did reduce this to little under 6 000€ in the end. I doubt the port scan caused much actual damage or require meaningful extra work from the bank. 

This was the first port scanning court case in Finland and A probably had to be made an example of to deter any future port scanners. These days I would definitely not suggest port scanning random addresses, you will very likely be caught and prosecuted.

---

### f) Test environment: Port scanning 

Test is done on Debian linux virtual machine I setup in earlier assignments. 

First let's install **Network mapper** (nmap) the port scanning tool
> $ sudo apt-get install nmap

Next we should disconnect our VM from the internet so there is not even an accidental chance that we port scan an innocent network and become a devious cyber criminal. We will test the internet connection by pinging Google nameservers (8.8.8.8)


<img width="418" height="201" alt="image" src="https://github.com/user-attachments/assets/1e087dea-d819-419b-93c2-83dd82e0ee93" />


Next let's pull the virtual plug on this virtual machine. You could also just plug the physical cable or shutdown your router, but it's more exciting this way. (Also you don't have to shut off the internet for the entire house.)


<img width="564" height="294" alt="image" src="https://github.com/user-attachments/assets/d4b4a39d-8abd-4a69-8c4b-bb8bd7fd4654" />


Click the virtual cable button then OK.


<img width="567" height="372" alt="image" src="https://github.com/user-attachments/assets/ced22341-c120-499b-ab25-dbfce832ec06" />


Let's try pinging Google nameservers again, the ping process will be stuck, but you can press CTRL + C to cancel the process after a moment.


<img width="554" height="100" alt="image" src="https://github.com/user-attachments/assets/a8c5ef6c-24a7-453c-bdde-371b3e8c0372" />


100% packet loss means no connection, if you are extra paranoid you could check if the browser works. Next let's scan our own VM using the localhost address.

---

### Scanning our localhost virtual machine


<img width="621" height="241" alt="image" src="https://github.com/user-attachments/assets/c7ac0a21-4551-4eba-9113-aa449a46a26a" />


999 ports are closed. We can see port 631 is open and we can even see it's service or what it's used for. IPP is internet printing protocol, which like it's name suggests is used for communicating with printers over a network. If this port was open to the internet, attackers could intercept sensitive documents or even remotely print full black pages and jam our printer. 

https://www.security.gov.uk/services-resources/cyber-services-government/domain-and-vulnerability-knowledge-base/open-port-631-internet-printing-protocol-ipp/

Next we should install a daemon (process that runs in the background). I googled basic linux daemons and chose **firewalld**, since we could use it to easily manage ports and network traffic, and we can make port changes without restarting. 

Fail2ban is a great way to protect your VM also, especially if you run a internet facing webserver like Apache. I'll also install sshd (remote secure connection daemon) just in case firewalld doesn't actually open any ports.


<img width="594" height="231" alt="image" src="https://github.com/user-attachments/assets/55778ab2-2426-4039-81a4-1d92ab980153" />


We need to get access to Internet again, so time to plug the virtual cable back same way as we unplugged it. After we can make sure we have internet by pinging Google again.

---

### Installing daemon

> $ sudo apt-get install firewalld
> $ sudo apt-get install ssh

Let's unplug the virtual cable again before we test nmapping localhost.


<img width="635" height="262" alt="image" src="https://github.com/user-attachments/assets/07529e00-47c5-436b-8266-b724dc5c4b81" />


We can now see port 22 is also open for SSH or Secure Shell, which means you can connect to this VM using a terminal on another PC. This is a pretty dangerous port to have open, since it will be one of the most targeted ports. Getting SSH access on a server or computer means you have access to do anything you want based on the privileges your account has. If you managed to gain root access, you can do anything on that computer: steal data, shutdown or install services, install malware and so on. (https://goteleport.com/blog/ssh-port-22/)

Fun fact: SSH was created by a finnish person Tatu Ylönen in 1995

Since have no need for either of these ports, we could close them using firewalld. **Warning:** if you are currently using SSH to connect to your virtual machine, you can accidentally lock yourself out by block your SSH port. 

**Good source for info on ports:**
- https://www.protocolports.org/en/port/22
- https://www.protocolports.org/en/port/631


<img width="683" height="130" alt="image" src="https://github.com/user-attachments/assets/84dea028-c796-48d2-b6ad-4069c1fe1c31" />


Since SSH was installed as a service and not just a port, we need to use the remove-service modifier in the command. I simply used Google search AI to find the correct commands for firewalld.


<img width="616" height="107" alt="image" src="https://github.com/user-attachments/assets/7888f15d-d271-4440-9899-304bfef1a276" />


When testing these with nmap they will still show as open to the local network. Unfortunately I could not find a way to scan, if these ports are open to the internet without nmapping my public IP, which I'm not going to do in this case just 

---

### Voluntary e) & f): Port scanning Apache on local host

- Identify a port scan against Apache on the host being scanned, e.g. in logs. Perform the test against "localhost" address and disconnect the internet while port scanning.
- Modify nmap scan so that it cannot be detected by the method you found above.

Let's start with installing apache2 web server. This allows us to host websites on the virtual machine and it should open port 80 for http traffic.

> $ sudo apt update
> 
> $ sudo apt install apache2


<img width="700" height="250" alt="image" src="https://github.com/user-attachments/assets/cd2157ad-e53f-4621-88b5-3946cde27b84" />


### Checking the logs

Now we need to check the logs for apache2 to see what the port scanning looks like. After a quick googling to refresh my memory logs are found in /var/log/apache2/, there's an error.log and access.log. I ran **$ nmp localhost** and checked the access log with **$ sudo cat /var/log/apache2./access.log**. 

The log was empty, the port scan was not showing on it. I made sure apache2 was running:


<img width="900" height="90" alt="image" src="https://github.com/user-attachments/assets/0210ae6f-fb14-4a2d-9f0a-38066d6da447" />


I also checked with my browser, this did show up in the access logs. 


<img width="981" height="226" alt="image" src="https://github.com/user-attachments/assets/f593dcd8-1283-40fe-bab6-2a27efd9626f" />


### Running the scan

Maybe the issue is that nmap isn't somehow scanning apache in a way that triggers the logs. I tried googling for how to see port scans in apache logs, but didn't find anything useful. Let's check the the help for nmap with **$ nmap --help**. The end of the output showed something interesting:


<img width="869" height="279" alt="image" src="https://github.com/user-attachments/assets/104fa294-c22b-428d-9601-986895e9f2cf" />


let's try **$ nmap -v -A localhost** from the example list, this should run multiple types of scans. We can now clearly see apache2 and http mentioned.


<img width="700" height="389" alt="image" src="https://github.com/user-attachments/assets/9fa326ae-a42d-4209-b27b-bdac46e23bd6" />


Now for the logs **$ sudo cat /var/log/apache2./access.log**, we can literally see nmap scripting engine written on the logs.


<img width="730" height="362" alt="image" src="https://github.com/user-attachments/assets/a10e9324-d528-40cd-8152-8bc5ffadb148" />


### Avoiding detection

Next we need to perform a scan without being detected in the logs. I don't really have a clear idea on where to take this, so I'll google for common methods to avoid detection when port scanning with nmap. I looked through the list of nmap command modifiers the AI overview gave me and picked a few that would be good to try. These were the first options in the categories **Timing and rate, packet fragmentation and Source masking and spoofing**. 

> -T0 (Paranoid) and -T1 (Sneaky). These timing templates introduce massive delays between packets. -T0 waits at least 5 minutes between probes, while -T1 waits at least 15 seconds.
>
> -f (Fragment Packets). This splits the TCP header over several tiny IP packets (8 bytes of data per packet), making it harder for simple packet filters to inspect the payload.
>
> -D <decoy1,decoy2,ME> (Decoy Scan). Nmap generates fake scans using spoofed source IP addresses alongside your real IP (ME). The target's logs show multiple machines scanning simultaneously, hiding the true scanner among the noise.

I did have to ask the AI for further help with syntax (decoy was especially tricky) and ended up with **$ sudo nmap -A -T3 -f -D 192.168.1.10,192.168.1.25,ME localhost**. I had to add the -A since otherwise it wouldn't scan for apache2 specifically even though you could see port 80 open indicating a webserver.


<img width="1630" height="201" alt="image" src="https://github.com/user-attachments/assets/7898dde8-e8f5-4c1c-b61e-9799fab96da5" />


The logs looked hopeful at the start, but the nmap showed up again. The command didn't work. I asked the AI again for _how do I scan for apache using nmap without showing up in access logs_ and made this command: 

**$ nmap -p 80 -sV --script=http-title --script-args http.useragent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36" localhost"**. 


<img width="652" height="304" alt="image" src="https://github.com/user-attachments/assets/8e19cd0c-5d9e-4bc5-b7a9-8f8064e67399" />


Just when I thought it worked, you can still see **/nmaplowercheck** in the log. So nmap was almost removed, but not quite. I'll have to return to this some time later to see, if it's possible to hide it completely.


<img width="1773" height="582" alt="image" src="https://github.com/user-attachments/assets/2514c6e1-c28e-45c8-8865-62cb527e2e9d" />

