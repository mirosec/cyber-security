# h3 Cyber lab

This is the third assignment for the course - https://terokarvinen.com/cyber-security/

---

### x) Read/watch/listen and summarize (This subtasks x does not require tests with a computer. Some bullets per article is enough for your summary, feel free to write more if you like. Add a bullet for your own idea or question. Reading emphasized, no extensive essays needed for this subtask.)

#### Heinonen 2026: How to Install Linux to Virtualbox?
- Very detailed instructions with explained basic concepts
- Learn how to install linux on a virtual machine
- Includes plenty of screenshots
- Great for beginners with little technical knowledge

#### Karvinen 2020: Command Line Basics Revisited
- Navigate folders
- Create, edit and remove files
- Install applications
- Open secure remote connections
- Learn directory structure

#### Karvinen 2022: Cracking Passwords with Hashcat
- I won't summarize this separately as it's part of the hash cracking assignment below. 

### b) Linux. Install Linux on a virtual machine. Use Debian 13-Trixie.  

I have already installed Linux on a virtual machine and hashcat, documentation can be found [here](https://github.com/mirosec/cyber-security/blob/main/h1-cyber-science.md). So I'll be skipping straight to cracking the hash.

---

### c) Crack the hash 6b1628b016dff46e6fa35684be6acc96 . follow the steps in the article to crack the example hash. Karvinen 2022: Cracking Passwords with Hashcat.

#### Cracking the hash 6b1628b016dff46e6fa35684be6acc96

I'll be following Tero's [guide](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/). Unfortunately my shared clipboard between PC and VM linux stopped working even though the settings are correct, but I simply don't have enough time to solve the issue. I'll just have to copy the outputs by hand, but I'll have to skip the long ones.

**Update**: Fix for the shared clipboard can be found here [here](https://github.com/mirosec/cyber-security/edit/main/h3-cyber-lab.md#later-update-on-shared-clipoard)

- hashcat is already installed so I just have to powerup my virtual machine and open terminal
 
- lets make hashed directory (folder) like in the instructions, then use command ls to see list of directories
 
```
$ mkdir hashed
 
$ ls
```
 
Folder is ready. Let's download Rockyou dictionary. It comes packed in a tar file, which is like a zipped folder. -x modifier extracts content out and -f specifies filename. rm command will remove the tar file once we have extracted the contents.
 
  ```
  $ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
 
  $ tar xf rockyou.txt.tar.gz
 
  $ rm rockyou.txt.tar.gz

  $ ls
  ```
 
We now have rockyou.txt ready to use in dictionary attacks. we can use head command to see the first few lines of text in a file. Tip: You can simply type head r and then press TAB and it will autofill the file name.
 
  ```
$ head rockyou.txt
 
 123456
 12345
 123456789
 password
 iloveyou
```
 
We can also count the number of lines in a file using the $wc command with -l modifier to specifiy counting lines.

  ```
$ wc -l rockyou.txt

 14344391 rockyou.txt
```

That is over 14 million words in total in the dictionary. Next we need to find out the hash type so hashcat can start cracking. This could be done manually, but it would be a long and inefficient way. We can try the $ hashid command with -m modifier. Oops I didn't install hashid in h1 assignment, so I'll have to do it now. 

  ```
$ sudo apt-get update

$ sudo apt-get install hashid

$ hashid -m
```

 
Let's try MD5 like instructions said:

  ```$ hashid -m '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved```

Ok it created the solved file, but when I used $ cat command I think I printed the 14 million lines in the terminal. That's when I noticed I used hashid command instead of hashcat. Lets try again.

  ```
  $ hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved

  Device #1 Not enough allocatable device memory for this attack.
```

Well that was unexpected. I have 2048 MB base memory allocated to this virtual machine. Time to google:

  Device #1 Not enough allocatable device memory for this attack virtual machine debian

It seems I can either shutdown the virtual machine and increase memory, or force it to use CPU instead by adding -D 1 modifier to the command. Let's try the lazy option.

  ```$ hashcat -D 1 -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved```

Unfortunately it just gave the same error. So time to turn off the virtual machine and increase memory from settings to 4096 MB. Now once more with feeling.

  ```
  $ hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved

  $ cat solved

  6b1628b016dff46e6fa35684be6acc96:summer
```
It works! The hash can be decrypted into **summer**. It took 0.03ms to solve. Hash type was MD5. Strange enough this time hashcat returned a message saying Host memory required for this attack: 0 MB, but that is a mystery to solve some other time. 

---

### d) Voluntary bonus: John the Ripper. Install and test John the Ripper Jumbo, see Karvinen 2023: Crack File Password With John. (We might do this together later)

Let's jump right in and follow the instructions on https://terokarvinen.com/2023/crack-file-password-with-john/. I skipped update and wget since we did those already.

  ```
$ sudo apt-get -y install micro bash-completion git build-essential libssl-dev zlib1g zlib1g-dev zlib-gst libbz2-1.0 libbz2-dev atool zip

  E:unable to locate package zlib-gst
  ```
 
Tried googling the error, but couldn't find anything definitive. Maybe it's because this is a newer version of Debian. Let's just proceed, hopefully it won't cause any errors, otherwise we'll return to look into it deeper.

  ```
$ git clone --depth=1 https://github.com/openwall/john.git

  bash: git: command not found
```

Seems git wasn't installed with the first command. Let's install it.

  ```
  $ sudo apt-get install git

  choose y for disk usage            # there is a prompt to choose yes or no, you pick one then press enter

  $ git clone --depth=1 https://github.com/openwall/john.git

  $ cd john/src

  $ ./configure

  configure: error: no acceptable C compiler found in $PATH
```

Quick google and we need to install a C compiler

  ```
$ sudo apt-get install build-essential

  $ ./configure

  configure error: OpenSSL headers not found, install them or use --without openssl option
```

Back to google and seems we need libssl-dev

  ```
$ sudo apt-get install libssl-dev

  $  ./configure

  Configure finished. Now "make -s clean && make -sj1" to complete
```

Assignment says type -sj4 but terminal says -sj1. The assignment is for an older linux so lets trust the terminal message this time.

  ```$ make -s clean && make -sj1```

It started compiling, let's wait for a few minutes and see what happens.

  ```
 make process completed.

  $ cd ../run/

  $ ls -l
```

We can see a long list of executables and scripts, python files. Let's run John.

  ```$ $HOME/john/run/john```

We see John the Ripper 1.9.0-jumbo, installation was successful and John is running.

Let's download Password Protected ZIP to crack.

  ```
$ wget https://TeroKarvinen.com/2023/crack-file-password-with-john/tero.zip

  $ unzip tero.zip

  incorrect password
```

We managed to extract an empty folder secretFiles/, but it's contents remain encrypted. We need to decrypt the SECRET.md file inside. We need to extract the password hash into a new file called tero.zip.hash

  ```$ $HOME/john/run/zip2john tero.zip >tero.zip.hash```

Let's have a look at the extracted hash

  ```$ cat tero.zip.hash```

It printed out the hash in long output, but it looks like extraction worked. Let's crack it with John now.

  ```
$ $HOME/john/run/john tero.zip.hash

  Using default input encoding: UTF-8

  no password hashes loaded (see FAQ)
  ```

I googled the error, but it was hard to find anything useful. There was a part about unshadowing, but it seems kind of complicated for this assignment. I tried to add --format=crypt.

  ```$ $HOME/john/run/john tero.zip.hash --format=crypt```

But it gave the same exact error. I even tried installing zliblg (there was no zlib-gst) which was missing earlier, but it didn't help either. We hit a wall for now, maybe we'll come back later to try fix the error.

---

### Later update - Finding and installing the right package

After trying to install multiple different packages and trying again with no success (libbz2, bzip2, libzzip-dev) I consulted my software developer friend, and got the advice to compile John again now that the packages were installed. To do that I had to remove the already compiled John. 

I ran  ```$ make uninstall -s clean && make -sj1``` to remove and compile John again, but it didn't work at first. At this point I gave up after a long day and swore to return to fix this later.

Few days later after extensive googling I found that I actually have to run the `.confgure` and `make install` part all over again after `make uninstall`. With a new boost of motivation I was determined to make it work this time. I read the instructions again and noticed this key line:

*If you're missing any dependencies, you'll get a warning here. That's how I found out what packages to install beforehand with 'apt-get'.*

Taking a new look at the dependencies after running ```$ ./configure```


<img width="1689" height="766" alt="image" src="https://github.com/user-attachments/assets/17fa8bee-953e-4c43-b468-502a21a6fe37" />


We can see the culprit libbz2, but there is no such package time to run apt install next and spam the trusty TAB button to see all the options


<img width="1690" height="450" alt="image" src="https://github.com/user-attachments/assets/824919be-4161-408e-8c3d-53529a9794fd" />


I already have libbz2-1.0 installed so that package was not the right one. The dev package was missing however, let's try install it!


<img width="1653" height="679" alt="image" src="https://github.com/user-attachments/assets/df760c5c-d039-4973-a3c0-67c570cae6f7" />


Now ```$ ./configure``` again and we can see the libbz2 dependency being filled this time


<img width="1687" height="136" alt="image" src="https://github.com/user-attachments/assets/ded3b88e-0389-4004-bcab-d28be7cb5571" />


Next I ran ```$ make -s clean && make -sj4``` again to compile John once more and followed the instructions of the assignment up to where I got stuck in the first place and...


<img width="1686" height="727" alt="image" src="https://github.com/user-attachments/assets/1bbd2b5c-4ca3-4531-806d-a544726ab0c1" />


Wohoo! We got it this time! The password is ```butterfly```. Now that we have they key, it's time to open the treasure


<img width="1663" height="682" alt="image" src="https://github.com/user-attachments/assets/ce5f8a50-dd63-4a62-baa5-39193510b0b7" />


This was a fun exercise and I'll return to create some encrypted files myself to try different cracking methods. 

---

### Later update on shared clipoard

Having to type everything manually between my host PC and the VM is very inefficient and prone to typos. To get the shared clipboard working bidirectionally between host PC and VM I had to install Guest Additions on the VM. First I needed to add VBoxGuestAdditions.iso to the virtual optical drive in VirtualBox Manager. 

This can be done in Oracle Virtualbox Manager -> Settings -> Storage -> Controller:IDE -> Add Optical Drive icon -> double click VBoxGuestAdditions.iso.

I followed the guide on https://share.google/aimode/lAOjcqblXFt6pRwOB to mount the CD in linux, but left out the first part with the Install Build Prerequisites.

<img width="1501" height="442" alt="image" src="https://github.com/user-attachments/assets/ef643547-c482-4aa3-ba3b-1577e3f2f35b" />
