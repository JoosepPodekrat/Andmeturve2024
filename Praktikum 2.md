# Praktikum 2
## Teise praktikumi tõestused:
1a)
Siin tuleks encrypted = räsiga ära vahetada, et leida konkreetne parool, hetkel on viimane neist seal sees.
Esimese kahe tähe printimine on enda meelerahuks, et programm kasutab õiget soola.
------------
import string, crypt
encrypted = 'XZkMWgaNMr552'
salt = encrypted[:2]
print(salt)
passwdlist = []
for c1 in string.ascii_lowercase:
                passwdlist.append(c1)

for c2 in string.ascii_lowercase:
        for c1 in string.ascii_lowercase:
                passwdlist.append(c2+c1)
for c3 in string.ascii_lowercase:
        for c2 in string.ascii_lowercase: 
                for c1 in string.ascii_lowercase:
                        passwdlist.append(c3+c2+c1)
for c4 in string.ascii_lowercase:
        for c3 in string.ascii_lowercase:
                for c2 in string.ascii_lowercase: 
                        for c1 in string.ascii_lowercase:
                                passwdlist.append(c4+c3+c2+c1)

for i in passwdlist:
        if encrypted == crypt.crypt(i, salt):


<img width="242" alt="image" src="https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/9172fe5b-597a-4dd4-a6c0-cd5c726050ac">
Paroolid: ut, ati, hack
1b)
Siin tuleks encrypted = räsiga ära vahetada, et leida konkreetne parool, hetkel on viimane neist seal sees.
Itereerimiseks on ilmselt lihtsamaid viise, kuid see töötab, seega pole põhjust optimiseerida nii väikeste paroolide jaoks.
------------

import string, crypt 
encrypted = '$6$SomethingHere$L5zuxicIHC90jGVZ9xgoOjUw36DjduwH1nPGJ.uwcgLqCvhlGe6wWp55eojE9jAIXxD>
salt = encrypted.rsplit("$", 1)[0]
passwdlist = []
for c1 in string.ascii_lowercase:
                passwdlist.append(c1)

for c2 in string.ascii_lowercase:
        for c1 in string.ascii_lowercase:
                passwdlist.append(c2+c1)
for c3 in string.ascii_lowercase:
        for c2 in string.ascii_lowercase: 
                for c1 in string.ascii_lowercase:
                        passwdlist.append(c3+c2+c1)
for c4 in string.ascii_lowercase:
        for c3 in string.ascii_lowercase:
                for c2 in string.ascii_lowercase: 
                        for c1 in string.ascii_lowercase:
                                passwdlist.append(c4+c3+c2+c1)

for i in passwdlist:
        if encrypted == crypt.crypt(i, salt):
                print ('parool on: ' + i)
                break

<img width="251" alt="image" src="https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/7731abf0-6d29-406a-8086-11223df7e3a2">
Paroolid: hd, led, asdf
