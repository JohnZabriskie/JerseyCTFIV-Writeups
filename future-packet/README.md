# future-packet

## misc - hard

### This is the step-by-step method to solving the challenge from the developers Point of View

* This challenge is first met with the following description:
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/65855d79-957e-4e56-848a-1b7bfe5e3c1f" width="50%" height="50%">

* We can download the Cisco Packet Tracer File and start taking notes of what is needed, the description states that an Accounting Computer has some "malware" on it, and that there is some evidence on one of the servers.
* When we open up the packet tracer file, we see the theoretical layout of the small business network (shown below):
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/9fa1902c-241d-42a1-97ec-66dab8f7e62a" width="125%" height="125%">
* We can take a look on the two servers that are in the orange field, and see the `DHCP Server` and the `Other Server`. The `DHCP Server` has some interesting contents if you click on `Desktop > Text Editor > File > Open` and you find a file named `BeforeAllCanOnlyNotice.txt` the contents of that file are: 

``` 
******This text file has some porky details below.******
_____________________________________________________________________________________________________________________

To gain the first flag you must decrypt this message below.

BAAAB AABAA AAABA BAABB BAAAA AABAA
_____________________________________________________________________________________________________________________

To obtain your next flag, you must next look into where the data goes from here, I got into your network through the firewall, and not I'm headed towards the CORE. I will be found with a simple command, some may use me to check who has access control... 


The password for the device is encrypted below:

AAABA ABAAA BAAAB AAABA ABBAB
_____________________________________________________________________________________________________________________

After you get through the core, I have deployed my malicious software onto your PC, you need to crack the code to get in and finish the flags!

74 68 65 72 65 5f 69 73 5f 6e 6f 5f 74 75 72 6e 69 6e 67 5f 62 61 63 6b 5f 6e 6f 77
_____________________________________________________________________________________________________________________
```
* The first clue here is to decrypt the first flag, but what the heck is that code. Well, we could throw that into a cipher identifier, or check out the clues given to us to find out what kind of cipher it is. 
* Name of file: `BeforeAllCanOnlyNotice.txt` -> [**B**]efore[**A**]ll[**C**]an[**O**]nly[**N**]otice...
* Top line of this file: This text file has some **porky** details below.
* We find out from either the Cipher Identifier or the Clues hidden that this is a [Bacon Cipher](https://en.wikipedia.org/wiki/Bacon%27s_cipher)!
* `BAAAB AABAA AAABA BAABB BAAAA AABAA` decoded is `SECURE` which noted from the text is our first flag
* The next code is a password `AAABA ABAAA BAAAB AAABA ABBAB` decoded is `cisco`. From the text we can see that the next clue is located in the CORE Switch. When we log onto the CORE Switch, we are met with a username and password. What better way then to try username: `admin` and the password we just uncovered: `cisco`. From here, we need to get in one more layer by typing `enable` and when prompted, type the password `cisco` again. 
* Next we need to find where the flag is hidden, the clue in the text says `I will be found with a simple command, some may use me to check who has access control... `. Doing a little bit of research, we can see that the CORE Switch is connected to the Firewall, and most firewalls need an ACL, or an Access Control List. To see that list, we can type in the command `show access-list` and there pops up the second flag `YOUR`.
* The last clue is to crack the final password and get into the Accounting Computer with the Malware. If we look at the last code `74 68 65 72 65 5f 69 73 5f 6e 6f 5f 74 75 72 6e 69 6e 67 5f 62 61 63 6b 5f 6e 6f 77`, this we can decode from hex -> `there_is_no_turning_back_now`
* If we look at Acct-2 computer, we see this application on it:
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/d8f0e7e3-565e-4727-bb31-18879b90717e" width="50%" height="50%">
* from there we are met with a screen with a prompt to enter a password: 
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/a51b0ee7-f0e8-4e47-bec8-a0b4761af826" width="100%" height="100%">
* If we put in the password `there_is_no_turning_back_now`, we are met with the last part of the flag `NETWORKS`
* We can put all this together for the final flag: `jctf{SECURE_YOUR_NETWORKS}`
