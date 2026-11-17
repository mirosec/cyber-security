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

**Port scanning **is a technique hackers use to search for vulnerabilities on the public side of a target network. Once a vulnerable port has been found it can potentially be used to gain unauthorized access to the target network (https://www.fortinet.com/resources/cyberglossary/what-is-port-scan)

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

<img width="618" height="261" alt="image" src="https://github.com/user-attachments/assets/1e087dea-d819-419b-93c2-83dd82e0ee93" />




How can criminals know what services your employer has? Disconnect your computer from the internet while doing the test (after you have installed the required software). Do the test inside your virtual machine.

    Install nmap port scanner
    Disconnect from the internet. Show that 'ping 8.8.8.8' stops working when internet is disconnected.
    Port scan your own computer. Use "localhost" as the address.
    Install a daemon
    Port scan again
    Analyze and explain the results
    Do not scan random computers.



