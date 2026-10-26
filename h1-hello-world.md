# h1 CyberScience

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

## b) Reviewing the review
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

## c) Threat modeling quickrun. Create two risks and decide what to do with them. Imagine the details. Be brief, but specific.
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

## D) Bonus - Create email alert for new research articles
There was a surprising lack of threat modeling review articles, so I created an alert for "threat modeling:review article" by clicking Create alert in Google Scholar's bottom of the left side panel.

## e) Install Linux on virtual machine
> First I downloaded Oracle Virtualbox for Windows Hosts from the official website. 
> Installation warned me of missing dependencies (python core package / win32api bindings), but I'll install them later. Otherwise default choices at every step. 
> Ran Oracle VirtualBox Manager after installation, chose basic mode for now
> Clicked Configure VirtualBox Manager to work with your computer
> Default folder was missing so I created Virtualbox VMs folder manually and selected it for default machine folder, clicked ok all other settings default
> 

## References 
This is the first assignment for the course - https://terokarvinen.com/cyber-security/

Creating this web page - https://terokarvinen.com/2023/create-a-web-page-using-github/

Finding and checking article validity - https://terokarvinen.com/review-article/

Page layout and formatting - https://www.markdownguide.org/basic-syntax/

Example inspired by - https://www.constructiondive.com/news/turner-construction-data-breach-ssns-bank-accounts/828454/

Virtual machines - https://www.virtualbox.org/wiki/Downloads
