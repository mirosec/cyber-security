# h2) Cyber security scene

This is the second assignment for the course - https://terokarvinen.com/cyber-security/

## h2 Scene 
Cyber moves fast. Here, you'll start following the scene.

Read/watch/listen and summarize (These subtasks a, b and c do not require tests with a computer. Some bullets per article is enough for your summary, feel free to write more if you like. Add a bullet for your own idea or question.)

a) Podcast. Listen and summarize one episode of one the following (Note: yes, just one, single episode out of all of these. More is a voluntary bonus task.)
Darknet Diaries podcast, or
Herrasmieshakkerit podcast (in Finnish, but your summary must be in English), or
Covert Access Team podcast, or
SANS Stromcast podcast, or
Helsec w44 Thu 18:00 livestream, one presentation (or physically there, if you got a ticket)

### Darknet Diaries - Ricky

This episode told the story of a Rick's journey into the world of cybercrime beginning from the late 2000's and how it affected his life. 

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

At this point Ricky had been hacking and stealing usernames for about a decade. Account security was improving and the older methods were not as effective anymore. Ricky's criminal colleagues introduced him to SIM-swapping, which they use to transfer the victim's mobile phone number to the attackers phone. Using the stolen phone number Ricky would reset the victims email password and log in. The mailboxes would be searched for any indication of crypto wallets (crypto exchanges, cold wallet phrases etc.), the goal was to gain access to the crypto wallet and steal everything in it. 


b) Blog. Read one article in one of these blogs (Note: yes, just one, single post out of all of these. More is a voluntary bonus task.)
Schneier on Security (author of the book "Applied Cryptography"), Atom feed, or
Krebs on Security, or
Traficom - NCSC News
Traficom is the Finnish Transport and Communications Agency
Unit42, or
Simon Willison (about AI, pick a security focused post)

c) Science that.
Link some theory, model or article you read in h1 CyberScience to a blog post or podcast episode you found here. Can you put a fresh security event in the context of larger understanding?

d) Download Debian. Download Debian 13-Trixie installation image on the computer you'll use in the class.
Go to Debian.org. On the Other downloads, under heading "Try Debian live before installing", choose "Live Xfce". The direct link for "Live Xfce" ISO image will soon become obsolete as new versions are published.
(Mac users: The linked image is for regular PC's, also known as amd64. If you have an M1, M2, M3, M4... Mac, it uses arm64 processor architecture, and you need to figure it out yourself. I suggest using UTM.)

e) Voluntary bonus: Install Debian 13-Trixie Linux on a virtual machine. (Everyone will do this later on the class.)

f) Voluntary bonus: Install a feed reader and follow some RSS / Atom feeds. (If time permits, everyone will do a version of this later.)

g) Voluntary bonus: Read more blog posts and listen to podcasts. Link those news into larger theory framework, citing relevan articles.

## References

https://darknetdiaries.com/transcript/181/

Cain & Abel - https://en.wikipedia.org/wiki/Cain_and_Abel_(software)

Cain & Abel - How it is used - https://learning.oreilly.com/library/view/cybersecurity-attack/9781788475297/a11337fa-7a56-40a3-9325-5a7cff5877d9.xhtml
