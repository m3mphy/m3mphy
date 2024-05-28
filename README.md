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







