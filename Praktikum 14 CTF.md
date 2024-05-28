Tegin CTFI kolm või neli korda, iga korraga sain natuke rohkem tehtud.
<br> Kokku 570P, mis tuleb ülesannetest
50p network
120p mailbox
200p php shell code
100p secret header
100p api
![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/09682f5d-7afc-4475-86b3-6b1cf8bd2d12)


1) ![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/7c566a5e-f53f-4409-b92b-f122a65a233f)
Lahendused selles on nii ennastmõistetavad, et ei hakka neid kommenteerima.

 https://www.rapidtables.com/convert/number/hex-to-ascii.html
 https://base64.guru/converter/decode/ascii
 <br>
2) 
Ülesannete lahenduskäigud:
Varia 1
O>* 10.5.4.0/22 [110/20] via 10.5.0.5, eth1, 16w5d14h, sest 10.5.4.0 kuni 10.5.7.255 vahemikus asub meie algne 10.5.7.0/24
flg 10.5.0.5
<br>
secret header
Curl koos käsklustega, mis liiguvad uutele lehtedele tagastas algse stringi, mille ROT13 decoreriga sain vastuseks.
curl -L -X POST -H "User-Agent: Mozilla/5.0 (X11; Linux x86_64)" http://shared.target05:1235/page.php -i
flg 943c46ee-3336-48af-bb74-459b0f303907
<br>
<br>
API) lahenduskäik on piltidel
![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/f9363933-6b3f-4297-93b0-67c8333eb9fe)
![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/2ea37cfa-e5ae-4a5a-b232-2821bceaab36)

flg b5d7407c-1afb-42d6-aef4-40b94733aad9
<br>
Mailbox
<br>
Kasutasin selle jaoks .sh skripti, mis proovis kõikide võimalike openssl decryption meetoditega murda koodi kasutades parooli ja siis printis välja, kui dekrüpteerimine läbi läks. Kuigi enamus vastustest olid kasutud, oli ka päris pin nende vahel.
![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/afd6c44b-92fc-4997-8545-6ad8bdc5e829)


flg 1837
<br>
PHP SHELL CODE)
<br>
php koodis oli obfuskeeritud koodi, mille loetavaks tegemisel ja analüüsimisel leidsin xor krüpteeringu, mille abil sai http requestidest leida krüpteeringuid.
kasutasin python scripti, mille tegi chatgpt 3.5, et need krüpteeringud lahti teha.
```python
import base64
import zlib

# XOR Decryption Function
def xor_decrypt(data, key):
    decrypted = bytearray()
    key_length = len(key)
    for i in range(len(data)):
        decrypted.append(data[i] ^ ord(key[i % key_length]))
    return decrypted

key = "4696bd9a"

# Example encoded payloads
encoded_payload_post = "TKpy+CqtFbNk4RZ9TrYWThvh9h6rqWi2gEBxG0iuFusbfBT+TU7wrX/hCTbocW53o5LfXMpDHvcc3p6gRo8uRSIhrpFKfODILTTMNmKLanhq"

encoded_payload_response = "TKq8Yqv2olEki8IdHiiTjSYAZ0OuQa4tOqU2fmvA+LW0ch3GkJPQZAQfDa/wxEMYyeLToIb5UoRpEAkK6ObGOF1zn/QHxazIqTP9MCTLsU9MJznE9uBM9B98gnaJOVcApAk3PO1kmXUyfHutCXBdEnTb3VfdK07zYAepPDZzvMs5BNTTQ/WVcftyxbHQMqG9dViPJCcVbD/QHIYuI441PgE2BvRi5fnARZgrY8HH3QQxxio6cE25xC3goy2EGb8g1rKlwzsg7oSs+h/3K64d58FvddW/mbggHXjvCIqs1BdvXewcDi+zEgDmC5anHpSTwziKtJSk1TQ+VgCA8841GdTkKvh1THYIv9M2Bkw7rTSxx3V20h1NiMV6nVH+RFJnz/gz4ARlvDQZoEOBo50k1NGBl27d/v+YIuHHw2rJkPZropd9mRFhXCcqIN//r6WnhsSA0h0LPfEBQXHrujzP4KLkUl24/8qO4HlV3jSSp4R7wM2DyuVf1G5/41Zt5TqzolnGF5VCgYteviUYD/a3hZvayAWoRR0rPjRIW4NfcUgamA+U1SNX4D03C/nYJHgRxqSays5KhjTnJEUehQM4tGklRwmA45fgc8Yyx8TOWYHqoqOHEonYi8Tw4AyFsQ+1HsoYytOD1wxgglij2GhATRlTTP43p/xe9bTiXwjHDjPTRtgarYe3yXVet2oOM/jUZRuUtS3mpd9RedaCbD1eurp5ZfRdvigUh0EHaZ/b0D0vfg=="

# Step by Step Decryption Process for both payloads
def decrypt_and_decompress(encoded_payload):
    # 1. Base64 decode
    decoded_data = base64.b64decode(encoded_payload)
    
    # 2. XOR decrypt using the provided key
    decrypted_data = xor_decrypt(decoded_data, key)
    
    # 3. Decompress the decrypted gzipped content
    decompressed_data = zlib.decompress(decrypted_data)
    
    # Return the readable response
    return decompressed_data.decode('utf-8')

# Decrypt and decompress the POST payload
post_result = decrypt_and_decompress(encoded_payload_post)
print("Decrypted and Decompressed POST Payload:")
print(post_result)

# Decrypt and decompress the Response payload
response_result = decrypt_and_decompress(encoded_payload_response)
print("\nDecrypted and Decompressed Response Payload:")
print(response_result)
```
flg fb148ca92d484070b5446b3233eef174

viimase korra screenshot
![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/47f3c494-4752-44a5-8175-1dc76929a748)

