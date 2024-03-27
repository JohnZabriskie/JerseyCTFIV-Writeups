# the-only-way-out

## osint - hard

### This is the step-by-step method to solving the challenge from the developers Point of View

* This challenge is first met with the following description:
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/18f3223c-6c0b-4ccd-b8e0-4bc6511c774d" width="50%" height="50%">

* We are told about this user Simon Letti being in Puerto Rico, we are told about his posting on Instagram, and his love for [NICC](https://nicc.njit.edu) (NJIT Information Cybersecurity Club)
* We first have to go to Instagram and look for the NICC account, and see that this user (_cyb3rb0i) is very active on the latest NICC posts. 
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/d4d1c317-9925-427b-922f-fe32384b3180" width="100%" height="100%">
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/7677f3e0-e9ad-4154-a9ef-995df4fd387a" width="100%" height="100%">

* On his Instagram page we see two posts and in his bio a tag named "u/_cyb3rb0i", which most people know relates to Reddit.

* If we check out his Reddit account, we see one post showing his love for cybersecurity and all the projects he is working on. Toward the end of this post, it shows the first flag `{coder}` and then the clues to find his GitHub, which we will keep this for later
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/5d5736d6-cb03-46d5-a903-60bada1b1443" width="75%" height="75%">

* We can track back to his Instagram and one of his posts is showing his love for JerseyCTF and the other about this restaurant in San Juan called Hazel Bar that he went to. In the description of that post it tells us that this restaurant used to be called something else before the Hazel Bar that has a Brooklyn/East LA vibe to it. The description tells us that this is the answer for flag2. 
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/bd54c77e-f3a4-4c0f-9bf9-52c1aa53884a" width="100%" height="100%">

* If we look up on Google 'Hazel Bar San Juan PR' the first search result shows that restaurant's Facebook Page. In that page, we can see the address of the restaurant and the picture that is also on Simon's Instagram page. 
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/993b61bb-325c-4bfe-8648-536804174bbc" width="100%" height="100%">

* If we search for that address on [Google Maps](https://www.google.com/maps/place/562+C.+Cuevillas,+San+Juan,+00907,+Puerto+Rico/@18.4558726,-66.0851932,17z/data=!3m1!4b1!4m6!3m5!1s0x8c036f2ff99ef353:0x31a11650e900bff6!8m2!3d18.4558675!4d-66.0826183!16s%2Fg%2F11m_czfnj3?entry=ttu) we can click on the street view, and we find the result from  Jan 2016 that shows a restaurant in the same spot as named `SODA`, which is now closed and the answer for flag2.
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/72b39209-70c0-42f0-ab64-dc3491089d29" width="100%" height="100%">


* Let's now take a look and try to find Simon's GitHub from what we learned from all the other details. We can find his page by searching Simon Letti on Google or HitHub and it pops right up! You can confirm this is the correct account by his Reddit username in his README. 
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/2db87965-2126-48bd-bee2-8f81955688b6" width="100%" height="100%">

* There are a bunch of coding projects that he has on there, one of which could help in a CTF, but don't really relate to this challenge, and the other file is his README file. If you look at the commit history in that README, it will show at some point he removed his email from his README. Lets take down this email and try to send it a message.
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/b62d4753-f963-49d9-a399-d11cffc0633e" width="100%" height="100%">


* When we send an email to this account, we get what looks to be an auto reply. At first look it is a pretty normal message, but if we copy it and put it in notepad, there looks to be something hiding. 
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/e0edf795-143a-46b1-9053-277011e75169" width="50%" height="50%">
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/dd901dda-d0cc-4474-8340-2aa389223d6e" width="50%" height="50%">

* We can quickly uncover the hidden text through a [decoder](https://www.irongeek.com/i.php?page=security/unicode-steganography-homoglyph-encoder) and get this response: `This is the final clue to your puzzle. flag3{nothing2see}`

* We can put this all together to get our full flag: `jctf{coder:soda:nothing2see}`
