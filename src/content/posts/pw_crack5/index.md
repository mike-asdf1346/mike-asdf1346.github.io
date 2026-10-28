---
title: 'picoCTF Password_cracking5 Learning Journal'
published: 2026-10-28
draft: true
tags: ['CTF', 'Python', 'Journal']
toc: true
coverImage:
  src: './pico-cover.jpg'
  alt: 'Sorry, the image is not shown.'
---   

## Overview   
Platform: picoCTF    
Level: password_cracking5   
:::warning
This article contains flag!
:::  

## Goal:   
```text
Can you crack the password to get the flag? Download the password checker here
and you'll need the encrypted <flag>
and the <hash>
in the same directory too. Here's a <dictionary>
with all possible passwords based on the password conventions we've seen so far.
```    
first thing to do is:   
`wget <url>`    

## Content of dictionary.txt:   
```text
0000
0001
0002
0003
0004
0005
0006
0007
0008
0009
000a
000b
000c
000d
000e
000f
0010
...and so on...
```
I tried to use the given password dictionary and set file mode to readable:   
```python
with open("./dictionary.txt", "r") as f1:
```
  
Then use for loop to iterate through the whole dictionary:   
```python
        for password in f1:
            password = password.strip()
            print(password)
            user_pw_hash = hash_pw(password)
```   
:::note
 The output of the password would be '0001\n', thus, remove the '\n' by utilizing `strip()`, which removes both '\n, spaces' for a clean password.   
:::
## Last step:   
so now just copy and paste the rest of the code base and fix some indentation error
```python
def level_5_pw_check():
    with open("./dictionary.txt", "r") as f1:        
        for password in f1:
            password = password.strip()
            print(password)
            user_pw_hash = hash_pw(password)

            if( user_pw_hash == correct_pw_hash ):
                print("Welcome back... your flag, user:")
                decryption = str_xor(flag_enc.decode(), password)
                print(decryption)
                return
            print("That password is incorrect")
```    
so here's the result    

```python
### full code
import hashlib

### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c)>
###############################################################################

flag_enc = open('level5.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level5.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_5_pw_check():
    with open("./dictionary.txt", "r") as f1:        
        for password in f1:
            password = password.strip()
            print(password)
            user_pw_hash = hash_pw(password)

            if( user_pw_hash == correct_pw_hash ):
                print("Welcome back... your flag, user:")
                decryption = str_xor(flag_enc.decode(), password)
                print(decryption)
                return
            print("That password is incorrect")



level_5_pw_check()
```   

output:      
![result pw5](./picoCTFlv5.png 'Retrieved the flag')  

