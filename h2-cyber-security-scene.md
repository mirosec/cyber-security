# h2) Cyber security scene

This is the second assignment for the course - https://terokarvinen.com/cyber-security/

Read/watch/listen and summarize cyber security **a)** podcast and **b)** blog, **c)** Link a science article to either one. 

### a) Darknet Diaries - Ricky - https://darknetdiaries.com/episode/181/

This episode told the story of a Rick's journey into the world of cybercrime beginning from the late 2000's and how it affected his life. A key point in the story is that cyber attacks do not necessarily require technical expertise, someone with simple audacity and ability to lie can cause serious harm.

**The beginning: Cheating in competitive video games**

Ricky's first touch with cyber attacks was through video games. He was a high schooler who enjoyed competing in sports and video games. He had success in the game _Halo 3_ and climbed up the rankings, but eventually hit a wall when he was constantly being disconnected during his matches which caused him to lose to players worse than him. He wanted revenge an so he went on forums on the internet and researched what had been done to him. Ricky wanted easy victories and didn't care he was stooping to the level of the cheaters.

> **How the attack was done: Packet sniffing and denial of service**
> 
> The cheaters would first use a legitimate password recovery tool made for windows called _Cain & Abel_, this tool would be used to sniff network packets during a match to find out the target's IP address. Once the address was found, the attacker would use another tool to flood the target IP with network traffic and cause the target to to disconnect, and lose the match as a result.
> 
> This attack is outdated as games are hosted mostly on dedicated servers these days and a single PC isn't powerful enough to bring down a server made for thousands of people, however the dedicated server can still be attacked using larger DDoS attacks using botnets for example. 

**Early criminal career: Social engineering to steal usernames**

On the internet, social media and in gaming communities usernames are a valuable commodity. Rare gamertags (username) can be cool to show off, but stealing and instagram handle of a company can have a serious impact on a business. Ricky would first start with stealing Xbox live gamertags by social engineering different Microsoft support channels to gain information on the target account, and use that information to gain access to the email account linked to the gamertag. 

Ricky would use these stolen accounts for his own amusement by logging on to them and cheating in games, which would get these accounts banned. The amount of bans would get his console hardware banned from Xbox live and Ricky would simply go to Gamestop to sell the banned console and buy a new one. Some other unknowing customer would buy the banned console and be unable to go online. Ricky was addicted to the rush from stealing. 

Ricky would eventually start monetizing his crimes by selling stolen usernames on the blackmarket for bitcoin. People would pay up to thousands of dollars for a single rare username. His hacker peers would encourage him to move on to steal Instagram handles, which were even more valuable. 

> **How the attack was done: Social engineering**
>
> 1. First the attacker would choose a rare username to target such as _Wolverine_.
> 2. The attacker would call **Zune support** (Microsoft Music service) under the pretense of having account issues and tell them they can't remember the email address, but they have the gamertag linked to the Microsoft account. The attacker would then pretend to be in a hurry and want to get off the phone and get a support reference number (ticket ID), so he can return to the issue later.
> 3. Next the attacker would call **Xbox live support** and give this support person the support reference number received earlier, which would bypass the verbal authentication phase. The support person would now give any information on the account to the attacker, in this case the account email address was the crown jewel being targeted.
> 4. The attacker would then try to reset the email accounts (**AOL/Yahoo**) password by abusing vulnerability of password recovery questions. Sometimes it was simple guesswork "Favorite food? - Pizza" other times the support could be tricked to giving hints on the recovery question over a phone call. "What is your favorite mythical animal" "hint: it's hairy".
> 5. The attacker would then reset the Microsoft account password, and access the password change link through the stolen email account, gaining access to the victim's Microsoft account.
> 6. Finally the Microsoft account could either be stolen completely, or the username could be changed so that the attacker could take that name with another Microsoft account.

**Escalating into more serious cybercrimes**

At this point Ricky had been hacking and stealing usernames for about a decade. Account security was improving and the older methods were not as effective anymore. Ricky's criminal colleagues introduced him to SIM-swapping, which they use to transfer the victim's mobile phone number to the attackers phone. 

Using the stolen phone number Ricky would reset the victims email password and log in. The mailboxes would be searched for any indication of crypto wallets (crypto exchanges, cold wallet phrases etc.), the goal was to gain access to the crypto wallet and steal everything in it. This was highly effective and Ricky's criminal group managed to steal millions of dollars worth of bitcoin from multiple victims with these relatively simple and quick attacks. 

The episode included a victim's perspective in Mark's story when he got SIM-swapped. Mark had known of these attacks and prepared beforehand by having instructions on his mobile carrier account, that SIM-swaps require two types of identification and can only be done on-site at a store. Unfortunately an employee had been bribed to be part of the attack and Mark's safety procedures were simply ignored. The employee allowed the attacker to swap his SIM, which lead to Mark's Coinbase account being stolen. 

> **How the attack was done: Social engineering and SIM-swapping**
>
> 1. The main goal of the attacker was to get the target's mobile phone number. First the attacker gathers basic information on the target, like a name or email address.  
> 2. The attacker contacts customer support of large platforms like Amazon, PayPal or ebay posing as the target account owner, and tricks the support to reveal key information such as the mobile phone number. In preparation for the carrier security checks, the attacker would gain more information such as target addresses and social security numbers from public background-check services. 
> 3. Finally the attacker would use all the gathered information to contact the mobile carrier and SIM-swap the target's phone number into a SIM card inside the attackers burner phone. This would of course disable the victims SIM card on their phone leaving them helpless, while the attacker used the stolen phone number to break into the victim's email account.

**Downfall & aftermath**

Ricky had to launder the stolen bitcoins through local buyers a few thousand dollars at a time. He used the stolen money to fund expensive and lavish vehicles while lying to his family that he got the money through crypto investments. Eventually a member of Ricky's criminal group was arrested and the law enforcement leveraged that arrest into catching the rest of the group. Ricky was sentenced to 4 years in prison and ordered to pay 7.6 million USD in restitution. 

These days Ricky uses his past experience to speak at cyber security events and is working on building a cybersecurity company. Ricky emphasises the importance of guiding young hackers to use their abilities to prevent cybercrimes rather than commit them.

--------

### **b) Blog.** Read one article in one of these blogs

I chose a relatively recent article from Traficom's National Cyber Security Center (NCSC-FI) news feed, as it gave an overview of the recent cyber security threats and events in Finland.

>https://kyberturvallisuuskeskus.fi/en/news/traficom-and-supo-cyber-security-threat-level-remains-high-serious-cases-rise

**Current threat level in Finland**
>- Finland has had an elevated cyber threat level ever since Russia invaded Ukraine in 2022. 
>- Serious cases investigated by NCSC-FI (ransomware, data breaches and intrusion) has more than doubled since last year
>- Findings of software vulnerabilites have increased
>- Probability of catastrophic society-wide cyberattacks is low

**Software vulnerabilities**
>- Number of significant cases has increased significantly
>- Vulnerabilities are more frequent and exploited quicker than before compared to previous year

**Phishing and scam messages**
>- Number of reported messages increased by 64% compared to last quarter
>- Bank-themed scams especially popular
>- NCSC-FI highlights the need for sufficient funding to ensure digital society remains safe

**How prepared is Finland against cyber threats?**
>- NCSC-FI is actively aware of the cyber security situation in Finland, offers support to organizations in need
>- Cooperation between sectors of society (private / public) is close and cyber threat information is shared frequently

**State-sponsored cyber threat against Finland remains active**
>- SUPO actively works to stop foreign state cyber espionage and influence
>- SUPO provides intelligence to relevant authorities
>- Russian cyber threat against Finland is shaped by Russia's war on Ukraine
>- China's cyber activity in finland targets poorly protected consumer devices and network infrastructure to attack third countries

### **c) Science that.**
Link some theory, model or article you read in h1 CyberScience to a blog post or podcast episode you found here. Can you put a fresh security event in the context of larger understanding?

I chose a systematic literature review on how security affects e-banking adoption. 
> Security as a determinant of e-banking adoption: a systematic literature review
> 
> https://www.sciencedirect.com/science/article/pii/S187705092602257X
> 
> JUFO ID 71301, Level 1
> 
NCSC-FI mentioned that bank-themed phishing has been especially prominent lately. A bank account is a valuable target since a successful attack can directly reward the attacker with money. No need for ransoming, selling information or negotiating. The pool of potential victims are huge and includes millions of people. The attackers can focus on targeting masses of people using methods enhanced by AI. While the main goal of the attackers is to exploit unaware users to gain access to their accounts, the attackers are also targeting banks' AI fraud detection systems with data poisoning. 

As a personal story my own credit card was the target of a possible cyber attack. It's still unclear how it happened and it's being investigated, but my entire credit was drained with large purchases from Turkey / Ecuador within a day. Even though my card was geo-locked to work in EU only. There were no alerts or MFA requests of any kind, everything was bypassed. The bank couldn't even tell me what I could do differently to avoid this. This event did hurt the trust I have in banking. 

### **f) Voluntary bonus:** Install a feed reader and follow some RSS / Atom feeds. 
> Google rss feed reader
> 
> Google AI overview listed several options

**FeedFlow** sounded like a good option to start based on it's description, it doesn't have any fancy algorithms or AI features, just lists news as they come. Also it's free and open source. Later I can try the fancier feed readers, if the features in this one are lacking.
 
> **FeedFlow**: A clean, open-source, algorithmic-free cross-platform app (Android, iOS, macOS, Windows, Linux) that works locally or syncs via iCloud, Dropbox, Google Drive, or self-hosted backends.

> https://www.feedflow.dev/
> Download for windows -> redirected to Microsoft store for download -> finish install
> 
> Add feed

Now we need an URL for the feed, let's check if Traficom has one. 
> https://kyberturvallisuuskeskus.fi/en/rss-feeds
> 
> Right-clicked **Information Security now!** feed from the list and chose Copy link
> 
> Paste into Feedflow URL field
> 
All the Traficom cyber news are now listed in chronological order and ready to read!

## References

Podcast episode - https://darknetdiaries.com/episode/181/

Cain & Abel - https://en.wikipedia.org/wiki/Cain_and_Abel_(software)

Cain & Abel - How it is used - https://learning.oreilly.com/library/view/cybersecurity-attack/9781788475297/a11337fa-7a56-40a3-9325-5a7cff5877d9.xhtml
