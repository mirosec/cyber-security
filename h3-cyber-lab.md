# h3 Cyber lab

This is the third assignment for the course - https://terokarvinen.com/cyber-security/

### x) Read/watch/listen and summarize (This subtasks x does not require tests with a computer. Some bullets per article is enough for your summary, feel free to write more if you like. Add a bullet for your own idea or question. Reading emphasized, no extensive essays needed for this subtask.)

#### Heinonen 2026: How to Install Linux to Virtualbox?
>- Very detailed instructions with explained basic concepts
>- Learn how to install linux on a virtual machine
>- Includes plenty of screenshots
>- Great for beginners with little technical knowledge

#### Karvinen 2020: Command Line Basics Revisited
>- Navigate folders
>- Create, edit and remove files
>- Install applications
>- Open secure remote connections
>- Learn directory structure

#### Karvinen 2022: Cracking Passwords with Hashcat
I won't summarize this separately as it's part of the hash cracking assignment below. 

### b) Linux. Install Linux on a virtual machine. Use Debian 13-Trixie.  & c) Crack the hash 6b1628b016dff46e6fa35684be6acc96 . Install hashcat and follow the steps in the article to crack the example hash. Karvinen 2022: Cracking Passwords with Hashcat.

I have already installed Linux on a virtual machine and hashcat, documentation can be found at https://github.com/mirosec/cyber-security/blob/main/h1-cyber-science.md. So I'll be skipping straight to cracking the hash.

#### Cracking the hash 6b1628b016dff46e6fa35684be6acc96

I'll be following the guide at https://terokarvinen.com/2022/cracking-passwords-with-hashcat/. 
> hashcat is already installed so I just have to powerup my virtual machine and open terminal
> lets make hashed directory (folder) like in the instructions, then use command ls to see list of directories
>   mkdir hashed
>   ls
> Folder is ready. Let's download Rockyou dictionary. It comes packed in a tar file, which is like a zipped folder. -x modifier extracts content out and -f specifies filename. rm command will remove the tar file once we have extracted the contents.
>  wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
>  tar xf rockyou.txt.tar.gz
>  rm rockyou.txt.tar.gz

### d) d) Voluntary bonus: John the Ripper. Install and test John the Ripper Jumbo, see Karvinen 2023: Crack File Password With John. (We might do this together later)

### e) Voluntary bonus: The other John. Create an encrypted file (other than zip) and crack the hash with John.
