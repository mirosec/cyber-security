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
> 
> lets make hashed directory (folder) like in the instructions, then use command ls to see list of directories
> 
>  $ mkdir hashed
> 
>  $ ls
> 
Folder is ready. Let's download Rockyou dictionary. It comes packed in a tar file, which is like a zipped folder. -x modifier extracts content out and -f specifies filename. rm command will remove the tar file once we have extracted the contents.
> 
>  $ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
> 
>  $ tar xf rockyou.txt.tar.gz
> 
>  $ rm rockyou.txt.tar.gz
>
>  $ ls
> 
We now have rockyou.txt ready to use in dictionary attacks. we can use head command to see the first few lines of text in a file. Tip: You can simply type head r and then press TAB and it will autofill the file name.
> 
>  $ head rockyou.txt
> 123456
> 
> 12345
>
> 123456789
>
> password
>
> iloveyou
> 
We can also count the number of lines in a file using the $wc command with -l modifier to specifiy counting lines.

>  $ wc -l rockyou.txt
>
> 14344391 rockyou.txt
>
That is over 14 million words in total in the dictionary. Next we need to find out the hash type so hashcat can start cracking. This could be done manually, but it would be a long and inefficient way. We can try the $ hashid command with -m modifier. Oops I didn't install hashid in h1 assignment, so I'll have to do it now. 
>
>  $ sudo apt-get update
>
>  $ sudo apt-get install hashid
>
>  $ hashid -m
>
> 
Let's try MD5 like instructions said:
>
>  $ hashid -m '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved
>
Ok it created the solved file, but when I used $ cat command I think I printed the 14 million lines in the terminal. That's when I noticed I used hashid command instead of hashcat. Lets try again.
>
>  $ hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved
>
>  Device #1 Not enough allocatable device memory for this attack.
>
Well that was unexpected. I have 2048 MB base memory allocated to this virtual machine. Time to google:
>
>  Device #1 Not enough allocatable device memory for this attack virtual machine debian
>
It seems I can either shutdown the virtual machine and increase memory, or force it to use CPU instead by adding -D 1 modifier to the command. Let's try the lazy option.
>
>  $ hashcat -D 1 -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved
>
Unfortunately it just gave the same error. So time to turn off the virtual machine and increase memory from settings to 4096 MB. Now once more with feeling.
>
>  $ hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved
>
>  $ cat solved
>
>  $ 6b1628b016dff46e6fa35684be6acc96:summer
It works! The hash can be decrypted into **summer**. It took 0.03ms to solve. Hash type was MD5. Strange enough this time hashcat returned a message saying Host memory required for this attack: 0 MB, but that is a mystery to solve some other time. 

### d) d) Voluntary bonus: John the Ripper. Install and test John the Ripper Jumbo, see Karvinen 2023: Crack File Password With John. (We might do this together later)

### e) Voluntary bonus: The other John. Create an encrypted file (other than zip) and crack the hash with John.
