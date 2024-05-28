1-3 Client side) kolm tükki ![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/4e4f8a9b-e16b-4b7b-bed6-3f024e56f1d8)<br>
4 SQL Injection intro) ![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/dd4e4cf4-5b91-4cd8-a4ce-5007e6e60059)<br>
5 Crypto basics) ![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/88f2f3a5-65fe-4830-a3fe-878531c3503b)<br>
6 Insecure direct object references) ![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/267f158e-ffb9-4390-ad09-4f357c005a13)<br>
7 XXE) ![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/9f4fc329-69cd-4a38-bd09-780c72250378)<br>
8 CSRF) Kuna webwolfi .html faili üleslaadimisega on mingi probleem, millele internetist lahendust ei leidnud, siis ei saa seda lõpuni teha, aga postitan lahenduskäigu, mis peaks töötama. Ilmselt on asi zapi pakettide kinni püüdmises.
HTML kood, mis failis olema peaks:
127.0.0.1 on minu kali IP.
```html
<form enctype="text/plain" method="POST" action="http:/127.0.0.1:8080/WebGoat/csrf/feedback/message">
	<input type="hidden" name='{"name": "WebGoat", "email": "webgoat@webgoat.org", "content": "WebGoat is the best!!", "ignoreme":"' value='sdfsdfdf"}'>
	<button>submit</button>
</form>
```
Pärast sellel lehel nupu vajutamist ja paketti kinni püüdmist peaks vastus olema loetav zapis inimloetaval kujul.
![image](https://github.com/JoosepPodekrat/Andmeturve2024/assets/144919619/95c22a2f-05fd-4956-944a-8c154ecb82d6)


