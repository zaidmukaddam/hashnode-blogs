## How to Brute Force ZIP File Passwords in Python

Hey Guys!
Say you're tasked to investigate a suspect's computer and you find a zip file that seems very useful but protected with a password. In this blog, you will write a simple, but yet precise Python script that tries to crack a zip file's password using [dictionary attack](https://en.wikipedia.org/wiki/Dictionary_attack).

We will be using Python's `built-in` **zipfile** module, and the third-party  [tqdm](https://github.com/tqdm/tqdm)  library for quickly printing progress bars:

```bash
pip3 install tqdm
``` 

As I have mention, we are going use dictionary attack, which means we need a wordlist to brute force this password-protected zip file. For this tutorial, we are going to use the big rockyou wordlist (with the size of about 133MB), if you're on Kali Linux, you can find it under the `/usr/share/wordlists/rockyou.txt.gz` path. Otherwise, you can download it [here](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt) .

You can also  [use crunch tool to generate your custom wordlist](https://www.rootinstall.com/tutorial/creating-custom-wordlists-using-crunch-utility/)  as you exactly specify.

Enough talking, let's now jump into the part we want.

# Scripting

```python
import zipfile
from tqdm import tqdm
``` 

Let's specify our target zip file along with the word list path:

```python 
# the password list path you want to use, must be available in the current directory
wordlist = "rockyou.txt"
# the zip file you want to crack its password
zip_file = "secret.zip"
``` 

To read the zip file in Python, we use the `zipfile.ZipFile` class that has methods to open, read, write, close, list and extract zip files (we will only use `extractall()` method here


```python
# initialize the Zip File object
zip_file = zipfile.ZipFile(zip_file)
# count the number of words in this wordlist
n_words = len(list(open(wordlist, "rb")))
# print the total number of passwords
print("Total passwords to test:", n_words)
``` 

Notice we read the entire wordlist and then get only the number of passwords to test, this can prove useful for **tqdm** so we can track where we are in the brute forcing process, here is the rest of the code:

```python
with open(wordlist, "rb") as wordlist:
    for word in tqdm(wordlist, total=n_words, unit="word"):
        try:
            zip_file.extractall(pwd=word.strip())
        except:
            continue
        else:
            print("[+] Password found:", word.decode().strip())
            exit(0)
print("[!] Password not found, try other wordlist.")
``` 

Since wordlist now is a Python generator, using tqdm won't give much progress information, that's why I introduced the total paremeter to give tqdm the insight on how many words are in the file.

We open the wordlist and read it word by word and tries it as a password to extract the zip file, reading the entire line will come with the new line character, as a result, we use the strip() method to remove white spaces.

The method extractall() will raise an exception whenever the password is incorrect, so we can pass to the next password in that case, otherwise, we print the correct password and exit out of the program.

***Results***


```kali
zaid@DESKTOP-SNN2HMG:~$ zip --password zaid secret.zip zaid.txt
zaid@DESKTOP-SNN2HMG:~$ gzip /usr/share/wordlists/rockyou.txt.gz
zaid@DESKTOP-SNN2HMG:~$ cp /usr/share/wordlists/rockyou.txt .
zaid@DESKTOP-SNN2HMG:~$ python3 zip_cracker.py
Total passwords to test: 14344392
 18%|███                              | 2530238/14344392 [02:15<10:47, 18258.95word/s]
[+] Password found: zaid
zaid@DESKTOP-SNN2HMG:~$
``` 

As you can see, I have found the password after around 2530K trials, which took about two minutes in my machine. Note the rockyou wordlist has more than 14 million words which are the most frequently used passwords sorted by frequency.

Alright, we have successfully built a simple but useful script that cracks the zip file password, try to use much more bigger wordlists if you failed to crack it using this list.

Hope you learned something new today!

Don't hesitate to comment below to raise any queries or suggestions.

Will see you guys in the next article!! :)
