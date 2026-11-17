# h4 Feed me

This is the fourth assignment for the course - https://terokarvinen.com/cyber-security/

---

### a) Installing a feed reader and adding feeds

I have installed and documented FeedFlow in my earlier assignment h2: https://github.com/mirosec/cyber-security/blob/main/h2-cyber-security-scene.md

#### x) Why install a feed reader?

The main advantage a feed reader offers is simplicity: you only get the news from sources you selected and nothing else. There are no ads or recommended articles, it's just pure, distilled
news content for you to read in the order it was published. You have complete control on what you want to add to a feed reader. A feed reader also has a definitive end, there is no endless scrolling. Privacy is also improved when you don't have to log onto a news website on a browser just to read the latest news. 

<img width="1000" height="650" alt="image" src="https://github.com/user-attachments/assets/7545f504-f19d-46f0-90b0-af54cd50effa" />

#### b, c, d) Adding more cyber security feeds

Finding new blogs to follow was super easy, I googled **cyber security blogs for rss feed** and started adding them by copying the link address for each site to the Feed URL field (shown in screenshot). I chose a few vendor blogs (Cisco Talos, Palo Alto unit 42 and Microsoft Security Blog) since they are relevant to my work. We provide networks solutions based on their technology. 

For general cyber security news I chose theregister.com because it's base in UK so it's good to have some variety to all the US-based sites. Finally I added darkreading for general news on cyber security, I opened the site and skimmed through a few articles to see what it was like and it seemed have quality news articles.

#### e) Results from following the feeds



---

#### y) Cyber security is serious business - Dangers of port scanning

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

#### f) Test environment: Port scanning 

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

#### Scanning our localhost virtual machine

<img width="621" height="241" alt="image" src="https://github.com/user-attachments/assets/c7ac0a21-4551-4eba-9113-aa449a46a26a" />

999 ports are closed. We can see port 631 is open and we can even see it's service or what it's used for. IPP is internet printing protocol, which like it's name suggests is used for communicating with printers over a network. If this port was open to the internet, attackers could intercept sensitive documents or even remotely print full black pages and jam our printer. (https://www.security.gov.uk/services-resources/cyber-services-government/domain-and-vulnerability-knowledge-base/open-port-631-internet-printing-protocol-ipp/)

Next we should install a daemon (process that runs in the background - https://en.wikipedia.org/wiki/Daemon_(computing)). I googled basic linux daemons and chose **firewalld**, since we could use it to easily manage ports and network traffic, and we can make port changes without restarting. Fail2ban is a great way to protect your VM also, especially if you run a internet facing webserver like Apache. I'll also install sshd (remote secure connection daemon) just in case firewalld doesn't actually open any ports.

<img width="594" height="231" alt="image" src="https://github.com/user-attachments/assets/55778ab2-2426-4039-81a4-1d92ab980153" />

We need to get access to Internet again, so time to plug the virtual cable back same way as we unplugged it. After we can make sure we have internet by pinging Google again.

#### Installing daemon

> $ sudo apt-get install firewalld
> $ sudo apt-get install ssh

Let's unplug the virtual cable again before we test nmapping localhost.

<img width="635" height="262" alt="image" src="https://github.com/user-attachments/assets/07529e00-47c5-436b-8266-b724dc5c4b81" />

We can now see port 22 is also open for SSH or Secure Shell, which means you can connect to this VM using a terminal on another PC. This is a pretty dangerous port to have open, since it will be one of the most targeted ports. Getting SSH access on a server or computer means you have access to do anything you want based on the privileges your account has. If you managed to gain root access, you can do anything on that computer: steal data, shutdown or install services, install malware and so on. (https://goteleport.com/blog/ssh-port-22/)

Fun fact: SSH was created by a finnish person Tatu Ylönen in 1995

Since have no need for either of these ports, we could close them using firewalld. **Warning:** if you are currently using SSH to connect to your virtual machine, you can accidentally lock yourself out by block your SSH port. 

**Good source for info on ports:**
https://www.protocolports.org/en/port/22
https://www.protocolports.org/en/port/631

<img width="783" height="180" alt="image" src="https://github.com/user-attachments/assets/84dea028-c796-48d2-b6ad-4069c1fe1c31" />

Since SSH was installed as a service and not just a port, we need to use the remove-service modifier in the command. I simply used Google search AI to find the correct commands for firewalld.

<img width="716" height="137" alt="image" src="https://github.com/user-attachments/assets/7888f15d-d271-4440-9899-304bfef1a276" />


How can criminals know what services your employer has? Disconnect your computer from the internet while doing the test (after you have installed the required software). Do the test inside your virtual machine.

    Install nmap port scanner
    Disconnect from the internet. Show that 'ping 8.8.8.8' stops working when internet is disconnected.
    Port scan your own computer. Use "localhost" as the address.
    Install a daemon
    Port scan again
    Analyze and explain the results
    Do not scan random computers.



