# h1 CyberScience

This is the first assignment for the course - https://terokarvinen.com/cyber-security/

### a) Science hunt. Find a review article related to the themes in the course. Detail your process to find and choose the article

I chose threat modeling for the topic of the article, since it is the starting point for applying cyber security. Bottom of the page in Google scholar search results includes related searches I used for search term ideas.

>https://scholar.google.com

>**Search**: threat modeling:review article, cyber threat modeling: review article, threat modeling:systematic literature review

>**Filters**:
>Top tier only, 
>Journals Only, 
>Since 2025
>Review articles

>Threat Modeling for the Defense Industry: Past, Present, and Future (2025)
>Clicked link for pdf 
>https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=10921707

This article is a systematic literature review, which is a synthesis of available and up to date research on the topic. 

>checked JUFO for journal validity https://jfp.csc.fi/jufoportaali
>IEEE Access is level 1 - basic, which is acceptable in this assignment

### b) Reviewing the review
#### Key areas being researched (research questions)
>- What are the latest technologies in current threat modeling methodologies?
>- What features are required to apply threat modeling in the defense industry?
>- Can the latest technologies identified in the first question be applied to the defense industry? If not, how should they be developed to meet the sector’s needs?

#### Widely agreed upon facts (conclusion and explanation)
>- Threat modeling methodologies based on automation do not consider larger mission-based (i.e. affecting organizational goals instead of assets) due to patterns used for automation.
>- Quantitative risk analysis does not illustrate how detailed elements relate to attacker Tactics, Techniques and Procedures (TTP). Threat modeling focusing on probability and and cost fails to show to detailed information about attackers methods. 
>- The DIEFD and extension of existing attack tree
methodologies do not address the shortcomings of traditional threat modeling methodologies. Traditional attack trees are manually done and too large and static, combining attack trees with TTP's requires AI to be done effectively.  

I used Gemini AI to explain terms mission-based, TTP and DIEFD (Data, Information, and Energy Flow Diagram) threat modeling, attack tree for information to base my answer on.

#### Open questions
>- How can latest technologies advance threat modeling in the defense industry?
>- How can AI-driven technologies be incorporated to maximize performance of threat modeling processes?

### c) Threat modeling quickrun. Create two risks and decide what to do with them. Imagine the details. Be brief, but specific.
#### Company 
>Janko's Concrete

#### Crown jewels
>data, reputation, business continuity

#### Bad guys - What do they want? How are they going to get it? Why us? (COI - Capability, Opportunity, Intent)
>Extortion Eddies are targeting construction firms for extortion in a recent trend where multiple construction firms were found to have inadequate protection from cyber threats.

#### List risks (only 2 example risks here). Likelyhood x impact = estimated value.
#### Employee data leak
> 70% x 2,000,000 € = 1,400,000 €

#### Construction project data leak (Blueprints, secret projects, NDA's, contracts)

> 20% x 10,000,000 € = 2,000,000 €

#### What shall we do with the biggest risk (META - mitigate, eliminate, transfer, accept)
Janko's is lacking expertise in cyber security so they decide to **transfer** the risk by purchasing secure access and data storage from a well-reputed service provider  for their construction project data. 

### d) Bonus - Create email alert for new research articles
There was a surprising lack of threat modeling review articles, so I created an alert for "threat modeling:review article" by clicking Create alert in Google Scholar's bottom of the left side panel.

### e) Install Linux on virtual machine
I'll try to be as detailed as possible within reason, so that someone with little knowledge could follow the instructions and do the same. 
#### VirtualBox for hosting virtual machines
>- First I downloaded Oracle Virtualbox for Windows Hosts from the official website. 
>- Installation warned me of missing dependencies (python core package / win32api bindings), but I'll install them later. Otherwise default choices at every step. 
>- Ran Oracle VirtualBox Manager after installation, chose basic mode for now
>- Clicked Configure VirtualBox Manager to work with your computer
>- Default folder was missing so I created Virtualbox VMs folder manually and selected it for default machine folder, clicked ok all other settings default
#### Installing Linux on virtual machine (VM)
>- Downloaded **Debian Linux 13.7.0 stable version** via regular download using browser, **complete installation package 64-bit PC DVD-1 iso**
>- VirtualBox Manager click **Create new virtual machine (VM)**
>- VM Name TestDebian, ISO image selected the file I downloaded for debian linux
>- Clicked Install guest additions, created username and password
>- Default settings for virtual hardware, after a quick google search I clicked Use EFI, since it's recommended for newer OS's
>- The screen was very small so I clicked View -> Scaled mode
>- Proceeded with installation, chose localization to match my own
>- Chose hostname debianvirtual, domain name .home
>- Didn't set specific root user, initial user will be admin, created user based on my name
>- Partition disk -  Guided - use entire disk, default settings on following screens
>- write changes to disk: yes, additional packages: no, network mirror:yes, proxy:no
>- Default settings on following screens, Finish installation
>- Checked browser and it works and has an internet connection

### f) Voluntary technical puzzle, without the use of AI
#### ==gCh8mclRFIs8GbsVGS
I am guessing this is a hash of a password or maybe a strong password, but let's pretend I don't know that. 
>- I copypasted this to notepad to see it's 20 characters long. 
>- Googled: what is 20 random characters cyber security
>- Found site: https://createpassword.in/blog/12-vs-16-vs-20-character-password-length-guide
>- 20 character password would be the best option for root/admin passwords
>- Site mentions **hashcat** or **john the ripper** as popular software to crack passwords
#### Installing hashcat
Let's try installing hashcat on debian linux and see what happens if we give it the puzzle, google How to install hashcat on linux
>- **VM machine terminal:** sudo apt install hashcat
>- Didn't work, system is asking for Media change insert disc, after googling the error it seems installation is attempted locally instead of online. Followed instruction on Google AI Overview to remove cd-rom from installation source list using terminal
>- **VM terminal:** sudo nano /etc/apt/sources.list
>- used # to comment out the **deb cdrom:** on the first line, then pressed ctrl+x, yes to save
>- **VM terminal:** sudo apt install haschat -> this time installation works
#### Using hashcat
>- **VM terminal:** hashcat
>- **VM terminal:** hashcat --help

Looks like we have to specify the attack type, hash type (autodetect might work) and then save the **==gCh8mclRFIs8GbsVGS** as a file on the VM for hashcat to work, can't just copypaste it directly to the terminal. Copypasting from host PC to VM doesn't work without changing settings and restarting the VM, but thankfully internet works on the VM so I can just get the hash from the course website. First let's see what folder I am in.
>- **VM terminal:** pwd
>- /home/miro
Now to open a new text file with nano and paste **==gCh8mclRFIs8GbsVGS** I copied from the course website using the browser in the VM.
>- **VM terminal:** nano
>- Then ctrl + shift + v to paste the puzzle. Ctrl + X to exit and save, name file to **puzzle.txt**
>- **VM terminal:** ls
>- Shows me the list of current files in the folder and I can see **puzzle.txt**
>- **VM terminal:** hashcat -a 0 puzzle.txt
>- Hashcat couldn't detect what type of hash was input
>- Google search: how to find out hash type
>- https://hashes.com/en/tools/hash_identifier tried this but it couldn't identify
>- https://hashcat.net/wiki/doku.php?id=example_hashes looked manually at this list and couldn't find a match, but there are some hashes that look similar with the double == marks
>- **24100	MongoDB ServerKey SCRAM-SHA-1	$mongodb-scram$*0*dXNlcg==*10000*4p+f1tKpK18hQqrVr0UGOw==*Jv9lrpUQ2bVg2ZkXvRm2rppsqNw=**
>- I tried different hashcat commands with the hash modifier -m 24100 and 24200, but didn't get any results. Also tried -a modifiers between 0-3 with no results.

This is getting too complicated, time to go back to the drawing board and look at this problem differently.

#### Trying other methods
I'm tempted to just google "what hash starts with ==", but I'm not sure if it would ruin the puzzle. I think I've made the classic mistake of assuming too much at the beginning. Maybe this isn't a hash, but some other type of encryption, so I searched **how to identify type of encryption.**
>- I found https://www.boxentriq.com/analysis/cipher-identifier and it says the puzzle is 100% base85.
>- Google base85 decoder linux
>- Tried using basenc -d --z85 puzzle.txt but it returned complete gibberish with random ??? icons
>- To paste the output to my host PC: Shutdown VM -> VM Settings -> general -> Shared clipboard -> bidirectional
>- Strangely the weird icons just paste as the original puzzle text on my host PC **==gCh8mclRFIs8GbsVGS**
>- I also tried https://www.boxentriq.com/encodings/base85-decoder, but that also just returned complete gibberish
>- Google how to identify base85

The search AI overview said: "Unlike Base64—which encodes 3 bytes into 4 characters (plus = or == padding)—Base85 encodes 4 bytes of binary data into 5 ASCII characters". So maybe the online tool scammed me and this is base64 instead.

>- https://www.boxentriq.com/encodings/base64-decoder
>- Invalid Base64 input for the selected format.
>- Google how to identify base64 -> Only upper and lower case letters, numbers 0-9, multiple of 4 characters, ends with one or two = signs

Could the assignment be devious enough to have actually reversed the encoding?

>- Google how to reverse text with linux
>- **VM terminal:** echo "==gCh8mclRFIs8GbsVGS" | rev
>- **VM terminal:** echo "SGVsbG8sIFRlcm8hCg==" | base64 -d
>- **VM terminal:** Hello, Tero!

We finally got the answer! The puzzle was in reversed base64 encoding. 


## References 
This is the first assignment for the course - https://terokarvinen.com/cyber-security/

Creating this web page - https://terokarvinen.com/2023/create-a-web-page-using-github/

Finding and checking article validity - https://terokarvinen.com/review-article/

Page layout and formatting - https://www.markdownguide.org/basic-syntax/

Example inspired by - https://www.constructiondive.com/news/turner-construction-data-breach-ssns-bank-accounts/828454/

Virtual machines - https://www.virtualbox.org/wiki/Downloads

Debian Linux - https://www.debian.org/distrib/
