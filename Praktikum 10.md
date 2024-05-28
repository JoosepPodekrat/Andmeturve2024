Praktikum 10 praktiline pool: pole aega.
<br>
Praktikum 10 teooria pool:
<br>
Kolm rünnakut, IPv6s:
Router advertisementi võltsimine - IPv6 kasutab RA sõnumeid, et ruuteritega suhelda, mis luba  võltsitud sõnumite saatmine,
et liiklust ümber suunata ja andmeid muuta või pealt kuuulata.
<br>
Neighbor Discovery Protocoli võltsimine - IPv6 ühes võrgus olevate seadmete tuvastamise meetod, mida ründaja võib ära kasutada võltsitud NDP sõnumeid saates, 
näiteks man in the middle või DoS rünnakuga.
<br>
Ühenduste piiramine - Automaatsete rünnakute eest kaitsta on raskem, sest IPv6 aadressid on pikemad, ning ründeid võib tulla miljarditelt erinevatelt aadressidelt, mille vastu kaitsta on suhteliselt raske.
<br>
Teistsugune protokoll - Kasutajate kogematus IPv6 kasutamisel tähendab, et on suur tõenäosus jätte kogemata mingi kaitsetegevus tegemata, sest IPv4-jal sellist nõrkust ei olnud,
kuigi see pole otseselt protokolli süü, on see ikkagi nõrkuskoht.
<br>
2. ARP spoof rünnaku vaste IPv6 aadressiruumis on Neighbor Discovery Protocol
(NDP) spoofing rünnak. IPv6 kasutab NDP protseduuri IP-aadresside ja
MAC-aadresside seostamiseks, mille asemel ründaja võib edastada võltsitud sõnumeid, et suunata liiklus läbi enda masina, ehk man in the middle rünnak.
Allikas:
https://packetlife.net/blog/2009/feb/2/ipv6-neighbor-spoofing/
<br>
3. Kuna Windows on kõige levinum ja seega igasugustele kasutajatele loodud, siis microsoft kaitseb oma keskmiselt abitumaid aruvti kasutajaid tulemüüriga. 
Linuxi ja Maci kasutajatelt eeldatakse paremat arvuti kasutus oskust ja ettevaatlikkust, seega need süsteemid ei kasuta tulemüüri n-ö by-default. 
Need on ka pigem arendajatele ja arvutitest huvitatud inimestele loodud, kes eelistavad ise seadistada oma seadeid. 
<br>
4.
Skript;
```shell
#!/bin/bash
ip6tables -F
ip6tables -P INPUT DROP
ip6tables -P OUTPUT ACCEPT
ip6tables -P FORWARD ACCEPT
ip6tables -A OUTPUT -j ACCEPT
ip6tables -A INPUT -s ::1/128 -j ACCEPT
ip6tables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
ip6tables -A INPUT -p tcp --dport 80 -j ACCEPT
ip6tables -A INPUT -p tcp --dport 443 -j ACCEPT
```
