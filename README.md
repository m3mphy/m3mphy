# OVER THE WIRE BANDIT

### LEVEL 0 -> 1
The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. The password for the next level is stored in a file called readme located in the home directory.

![b0](https://github.com/m3mphy/m3mphy/assets/146635397/6063596f-2111-4ff1-a895-ca583a172b37)

This was a very basic level. All we have to do was read the content from readme using cat command.


### Level 1->2

The password for the next level is stored in a file called - located in the home directory.

![b1](https://github.com/m3mphy/m3mphy/assets/146635397/c209577a-a534-4ff1-bb2a-92396696251b)

In this level we have to specify the path to read the file.

### Level 2->3

The password for the next level is stored in a file called spaces in this filename located in the home directory.

![b2](https://github.com/m3mphy/m3mphy/assets/146635397/54a5a0c4-0e0c-4539-8a01-f05e01ba885a)

We would use quotes and inside quotes the filename to read the file.

### Level 3->4

The password for the next level is stored in a hidden file in the inhere directory.

![b3](https://github.com/m3mphy/m3mphy/assets/146635397/11c90616-f48b-4a52-96f6-b09b039fb952)  

Inside the inhere directory, there is a hidden file which can't be seen barely using ```ls``` command so here we used ```-a``` switch to search for any hidden files.

### Level 4->5

The password for the next level is stored in the only human-readable file in the inhere directory.

![b4](https://github.com/m3mphy/m3mphy/assets/146635397/aeeddd94-8b83-4ebf-abb1-0936d934d10f)

Using the command ```find -type f | xargs file``` list all the files with type of data.From there we can see that file07 contains ASCII text.

### Level 5->6

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
   1. Human-readable
   2. 1033 bytes in size
   3. not executable

![b5](https://github.com/m3mphy/m3mphy/assets/146635397/0bf922bb-c3ce-4231-9c39-7c80908dab41)

Using ```find . -type f -size 1033c !executable``` will give the file inside the inhere directory.

### Level 6->7

The password for the next level is stored somewhere on the server and has all of the following properties:
  
   1. Owned by user bandit7
   2. Owned by group bandit6
   3. 33 bytes in size

![b6](https://github.com/m3mphy/m3mphy/assets/146635397/ded6a527-aa36-490e-afee-ac6b3058e4d8)

![b6 1](https://github.com/m3mphy/m3mphy/assets/146635397/db44ae2f-4c1f-4489-b865-1f0071a89ab9)

Here we tell ```find``` to look into the ```root``` directory as we don't know where the file is located.

### Level 7->8

The password for the next level is stored in the file data.txt next to the word millionth.

![b7](https://github.com/m3mphy/m3mphy/assets/146635397/0cd03cf5-76bd-4a48-94a9-1c9bd7ebc29d)

With the help of ```grep``` command, we can find the password asscociated with ```millionth```

### Level 8->9

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

```bash
sort data.txt | uniq -c | grep "1 "
```
We first ```sort``` the data alphabetically, then used the the ```uniq``` to count the unique occurences and specify ```1``` to find the line that occurs only once.

### Level 9->10

The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.

![b9](https://github.com/m3mphy/m3mphy/assets/146635397/91f20130-7192-4c8b-a093-5ba82905b80b)

The ```strings``` command helps us to find the human-readable strings and then ```grep``` the strings beginning with several ‘=’ characters.

### Level 10->11

The password for the next level is stored in the file data.txt, which contains base64 encoded data.

![b10](https://github.com/m3mphy/m3mphy/assets/146635397/26689be6-19b4-4ae9-ad1a-beccb8496467)

Use ```base64 -d``` to decode the string.

### Level 11->12

The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
We can use this command to rotate by 13 or we can simply decode this using various online tools available.

![b11](https://github.com/m3mphy/m3mphy/assets/146635397/02416010-04f6-4ab4-af4c-a58389f8d448)

### Level 12->13

The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.

![b12](https://github.com/m3mphy/m3mphy/assets/146635397/b9f68c53-e683-4f5f-82fd-5c7378ef547d)

![b12 1](https://github.com/m3mphy/m3mphy/assets/146635397/dd81a612-65ef-460e-93a2-77de7cfccff1)

![b12 2](https://github.com/m3mphy/m3mphy/assets/146635397/939d5006-ca55-4cd8-a21f-dc1e96b88de2)

The ```-r switch of xxd``` convert an hexdump to binary. Then we use the ```file``` command to find out which compression tool has been used and recursively decompress the files with the right tool.

### Level 13->14

The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level.

![b13](https://github.com/m3mphy/m3mphy/assets/146635397/55d0eb9b-696d-4550-8e94-0f2ef2ef0441)

![b13 1](https://github.com/m3mphy/m3mphy/assets/146635397/ff950e89-68f6-4985-8bf6-3642ec8f36dc)

Here we used ```scp``` command to download the key in the local machine and then we run the ```ssh``` with ```-i``` switch for the key file. From here we get the access to the next level.

### Level 14->15

The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

![b14](https://github.com/m3mphy/m3mphy/assets/146635397/b9a39b3e-52c7-4e75-85cf-4e8efeba0724)

Simply entering the password on the localhost server of port 30000, we get the password for the next level.

### Level 15->16

The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

![b15](https://github.com/m3mphy/m3mphy/assets/146635397/0e25dd75-3e7c-4cf4-a951-e4c46f4efe06)

![b15 1](https://github.com/m3mphy/m3mphy/assets/146635397/9aaeafe0-65d7-4a57-811c-143d09c0308d)

We can access the password for next level with two ways shown.

### Level 16->17

The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

![b16](https://github.com/m3mphy/m3mphy/assets/146635397/fff3e200-c9d5-41ee-b4a3-f61ade4a2fc9)

![b16 1](https://github.com/m3mphy/m3mphy/assets/146635397/c382b040-a8c3-45b5-b7aa-9ee07cbf9640)

![b16 2](https://github.com/m3mphy/m3mphy/assets/146635397/050b45b4-a26f-448a-b35a-370a164061c3)

After scanning the ports using ```nmap```, we'll find which of the ports are open and then using ssl, we connect to the ports and check for the next level credentials by passing passwords of the current level. After getting the key, we'll save it and then run ```chmod 777``` on the key and connect it using ssh.

### Level 17->18

There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

![b17](https://github.com/m3mphy/m3mphy/assets/146635397/5a7f2601-f422-4fed-af15-cdd0e6e05d8a)

The ```diff``` command will compare 2 files line by line and show you the differences. After that login to the next level with the differences as the password.

### Level 18->19

The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

![b18](https://github.com/m3mphy/m3mphy/assets/146635397/4ec6c07a-2a13-4c17-8fd4-70a9bf522a78)

Here we used ```ssh with -t bandit18@bandit.labs.overthewire.org -p 2220 /bin/bash``` for shell. It allows the user to execute a command on the remote system without opening an interactive shell session.  

### Level 19->20

To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

![b19](https://github.com/m3mphy/m3mphy/assets/146635397/ded65453-1155-4a23-a3b8-f71f68338910)

### Level 20->21

There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

![b20t1](https://github.com/m3mphy/m3mphy/assets/146635397/5e5b8e8a-8a90-4a6f-adde-2fffaf43185e)

![b20t2](https://github.com/m3mphy/m3mphy/assets/146635397/1244a0ae-c390-4e33-b0b2-05993b4dd672)

Here we uysed 2 terminals. First we host a remote server in one terminal which sends password of the current level to the localhost at the specific port. Secondly we use another terminal to run ```suconnect``` with the specific port.

### Level 21->22

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

![b21](https://github.com/m3mphy/m3mphy/assets/146635397/0bbd3165-5bbd-46ed-8d92-109b9d2ce91c)

First we run ```ls -la``` command on the ```/etc/cron.d``` to find running programs. Then we read the content at ```/etc/cron.d/cronjob_bandit22``` to understand what's going on. Then ```cat /usr/bin/cronjob_bandit22.sh```. After understanding the script we get to the password.

### Level 22->23

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

![b22](https://github.com/m3mphy/m3mphy/assets/146635397/937a3b32-6fc8-4679-8ceb-e04073520e24)

![b22 1](https://github.com/m3mphy/m3mphy/assets/146635397/080eeb04-d735-4741-9684-a4467013d175)

The script tells us that the file where the password will be stored is an md5 hash. Following the above steps can help find the password.

### Level 23->24

A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

![b23](https://github.com/m3mphy/m3mphy/assets/146635397/8def7ca0-6504-4070-9000-9cb5d2906267)

![b23 1](https://github.com/m3mphy/m3mphy/assets/146635397/3acee245-b013-4e54-a089-3c9b26945f56)

The cron script execute and delete all scripts in ```/var/spool/bandit24```. We just need to write our own script, copy it in ```/var/spool/bandit24``` and wait for the result.

### Level 24->25

A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

![b24](https://github.com/m3mphy/m3mphy/assets/146635397/15bcc005-e73c-4805-b210-d87b0cfddf77)

![b24 1](https://github.com/m3mphy/m3mphy/assets/146635397/2a57e2a8-6bea-4156-bb98-60246d2df654)

![b24 2](https://github.com/m3mphy/m3mphy/assets/146635397/663512ec-5a4a-4c12-a8d9-655ce3cbfc57)

We will write a script as shown for this to bruteforce the password.

### Level 25->26

Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

![b25](https://github.com/m3mphy/m3mphy/assets/146635397/425b1f06-3c6d-4738-affb-3b3021ecda34)

![b25 1](https://github.com/m3mphy/m3mphy/assets/146635397/6976c768-ba72-4ce1-85fa-33f433c49afa)

Reduce the size of the terminal to enable 'more' to paging through text one screenful at a time. After that we will login through the key and then press 'v' to start vi.
Then, in vi type ':e /etc/bandit_pass/bandit26'.

### Level 26->27

Good job getting a shell! Now hurry and grab the password for bandit27!

![b26](https://github.com/m3mphy/m3mphy/assets/146635397/e4c714b9-7a1b-4cc7-a728-b294f7430bcd)

Now, as we already have a shell using vi, we can get the password for level 27.Once more is running we can type v to open vi and execute command through that tool. Same thing for the second part except the bandit27-do command will give us the password like in one of the previous level.

### Level 27->28

There is a git repository at ssh://bandit27-git@localhost/home/bandit27-git/repo. The password for the user bandit27-git is the same as for the user bandit27.

![b27](https://github.com/m3mphy/m3mphy/assets/146635397/ba5bcd69-8c16-4f69-a3b3-d7150ac8fc15)

 You need to create a temporary folder in /tmp/ and clone the repo. Then, to reveal the password you need to run the ```cat``` command.

### Level 28->29

There is a git repository at ssh://bandit28-git@localhost/home/bandit28-git/repo. The password for the user bandit28-git is the same as for the user bandit28.

![b28](https://github.com/m3mphy/m3mphy/assets/146635397/b0c47474-fb1e-4c98-981d-162a1d2bb129)

![b28 1](https://github.com/m3mphy/m3mphy/assets/146635397/4dfa68cf-37d2-4ffa-a1ab-0e538c36aa85)

You need to create a temporary folder in /tmp/ and clone the repo. Then, to reveal the password we use ```git show``` on the older commit.

### Level 29->30

There is a git repository at ssh://bandit29-git@localhost/home/bandit29-git/repo. The password for the user bandit29-git is the same as for the user bandit29.

![b29](https://github.com/m3mphy/m3mphy/assets/146635397/33c0a973-e573-416c-82b2-a7a5981b558a)

![b29 1](https://github.com/m3mphy/m3mphy/assets/146635397/616472a1-2182-449d-967b-d789f1c76b55)

![b29 2](https://github.com/m3mphy/m3mphy/assets/146635397/8d3ad551-9a54-4680-ba1f-106a4f31ec8a)

![b29 3](https://github.com/m3mphy/m3mphy/assets/146635397/20d6046b-7562-414c-a63c-c5cac8096270)

You need to create a temporary folder in /tmp/ and clone the repo. Then, to reveal the password you need to checkout the dev branch.

### Level 30->31

There is a git repository at ssh://bandit30-git@localhost/home/bandit30-git/repo. The password for the user bandit30-git is the same as for the user bandit30.

![b30](https://github.com/m3mphy/m3mphy/assets/146635397/f7634502-3400-4f90-a52a-a5df45b6e48b)

You need to create a temporary folder in /tmp/ and clone the repo. Then checking all the files in ```.git``` directory.

### Level 31->32

There is a git repository at ssh://bandit31-git@localhost/home/bandit31-git/repo. The password for the user bandit31-git is the same as for the user bandit31.

![b31](https://github.com/m3mphy/m3mphy/assets/146635397/bac26031-6775-44e6-ae8a-4085776940b6)

![b31 1](https://github.com/m3mphy/m3mphy/assets/146635397/16277ba0-f480-4d9b-b060-b50118afe908)

![b31 2](https://github.com/m3mphy/m3mphy/assets/146635397/9ff9d9b7-a646-4264-830a-3134affbc45e)

You need to create a temporary folder in /tmp/ and clone the repo. Then, we just follow the instruction in the README.md. Push a file called key.txt, add the file and push it to the master branch.

### Level 32->33

After all this git stuff its time for another escape.

![b32](https://github.com/m3mphy/m3mphy/assets/146635397/49cd31c9-6238-41f9-abd2-7455c7ea6ff2)

Here we get an interactive shell by inserting $0 in the fake shell, then we run vim end read the password for the next level.

### Level 33

This one is not really a challenge as there are no more levels to play in this game. But we can still try to login to check the password we found previously.

```bash
Congratulations on solving the last level of this game!

At this moment, there are no more levels to play in this game. However, we are constantly working
on new levels and will most likely expand this game with more levels soon.
Keep an eye out for an announcement on our usual communication channels!
In the meantime, you could play some of our other wargames.

If you have an idea for an awesome new level, please let us know!
```
