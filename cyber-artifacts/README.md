# cyber-artifacts

## crypto - hard

### This is the step-by-step method to solving the challenge from the developers Point of View

* This challenge is first met with the following description:
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/c253be32-56d2-4e23-8ff6-7701a59f339a" width="50%" height="50%">

* We first notice there is a key word here in the description, that word being `WAV`. It is mentioned two seperate times, so let's keep note of that.
* We see the two files named `some-kinda-code.txt` with 800,000 characters, and a Word doc called `Shadows of the Digital Abyss`, which when opened is password protected. 
* The .txt file we received is full of numbers like this: `0x52, 0x49, 0x46, 0x46,...` which we can assume is hex. If we take the clue from the description and try to convert this hex file into a WAV file, we can use this [site](https://tomeko.net/online_tools/hex_to_file.php?lang=en) to get a WAV file.
* From there, we can play the file and it sounds like morse code, and if we decode that (you can use a [morse code listener/visualization tool](https://databorder.com/transfer/morse-sound-receiver/)) we get the following output: `NJIT-IS-THE-BEST-SCHOOL-EVER` (which it is)
* Using this newly discovered password, we can put that into the Word doc that we found out was password protected. 
* Upon opening the Word doc, we see the following story:
*  <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/08b12182-2185-47cf-b23c-2968562d5c32" width="100%" height="100%"> 
* This story looks, and most definitely is, ***meaningless***
* Word has an interesting feature that you can use to hide data, if you click `Ctl+Shift+8`, a little line appears...
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/5e5a2a18-6c6d-4650-85bf-7fb857c6bb36" width="100%" height="100%"> 
* This hidden line `thylu.weewbu.sec/vybu/t/1V7m9xbz1xx0VO11JglCxDy5c_f2L4rwa/lyum?kif=ixqhydw` looks to be some sort of cipher. If we throw in into the [dCode Cipher Identifier](https://www.dcode.fr/cipher-identifier), this can be decoded from a ROT Cipher and the output is a link: `drive.google.com/file/d/1F7w9hlj1hh0FY11TqvMhNi5m_p2V4bgk/view?usp=sharing`
* If we follow this link, we are met with a random QR code, and when scanned brings you to this [random site](https://puginarug.com/), which you guessed it, is absolutely ***meaningless***
* However, if we download this QR code and put it into a [Steganographic Decoder](https://www.beautifyconverter.com/steganographic-decoder.php), we get our lovely flag
*  `jctf{sh0w_m3_th3_crypt0}`


