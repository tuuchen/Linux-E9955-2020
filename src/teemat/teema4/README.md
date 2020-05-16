[Takaisin alkuun](../../../README.md)

# Järjestelmän ylläpito

## 1. Käyttäjähallinta

### *1.1. Luo kaksi uutta käyttäjää (opettaja ja opiskelija). Aseta käyttäjille myös kotihakemistot. Käytä toisen luomisessa komentorivia ja toisen graafista käyttöliittymää.*

Luodaan komentorivin avulla opettaja, sekä opettajan hakemisto. 

Käytin `sudo useradd --create-home -d /home/opettaja opettaja` -komennon sijaan Linuxista löytyvää `adduser` -komentoa, joka tarjoaa näppärän komentorivinkäyttöliittymän käyttäjän lisäämiseen.  
  
`osboxes@osboxes:~$ sudo adduser opettaja`  
`Adding user 'opettaja' ...`   
`Adding new group 'opettaja' (1001) ...`   
`Adding new user 'opettaja' (1001) with group 'opettaja' ...`   
`Creating home directory '/home/opettaja' ...`   
`Copying files from '/etc/skel' ...`   
`Enter new UNIX password:`   
`Retype new UNIX password:`   
`passwd: password updated successfully`   
`Changing the user information for opettaja`   
`Enter the new value, or press ENTER for the default`   

	 `Full Name []: Olli Opettaja` 
	 `Room Number []: 123` 
	 `Work Phone []: 123` 
	 `Home Phone []: 123` 
	 `Other []: 123` 

`Is the information correct? [Y/n] Y` 

Graafisen käyttöliittymän avulla oppilas, sekä oppilaan hakemisto: 

[![opiskelija](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/opiskelija.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/opiskelija.png)

# 
  
### *1.2. Lisää toinen käyttäjistä ryhmään nimeltä “opiskelijat” ja toinen ryhmään "opettajat". Käytä ainakin toisessa operaatiossa komentorivia.*

`sudo usermod -a -G opettaja opettaja` 

[![ryhmät](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ryhmät.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ryhmät.png)

# 

### *1.3. Luo hakemistot “opiskelijoiden_tiedostot” ja "opettajien_tiedostot", joille annat oikeudet vain asianosaisille ryhmille. Varmista kokeilemalla molemmilla käyttäjillä, että oikeudet ovat voimassa. Käytä ainakin toisessa operaatiossa komentorivia.*

Opiskelijat:

`sudo mkdir /home/opiskelija/opiskelijoiden_tiedostot | sudo chown opiskelija /home/opiskelija/opiskelijoiden_tiedostot | sudo chgrp opiskelija /home/opiskelija/opiskelijoiden_tiedostot | sudo chmod 770 /home/opiskelija/opiskelijoiden_tiedostot` 

Opettajat:

`sudo mkdir /home/opettaja/opettajien_tiedostot | sudo chown opettaja /home/opettaja/opettajien_tiedostot | sudo chgrp opettaja /home/opettaja/opettajien_tiedostot | sudo chmod 770 /home/opettaja/opettajien_tiedostot` 

Testi:

[![oikeudet](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/oikeudet.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/oikeudet.png)

# 

### *1.4. Lukitse "opiskelija" käyttäjän tunnus väliaikaisesti. Voit tehdä tämän joko komentoriviltä tai graafisesta käyttöliittymästä.*

Lukitaan opiskelija: 

`sudo usermod -L opiskelija` 

[![lukittu](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lukittu.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lukittu.png)

# 

## 2. Prosessien hallinta

### *2.1. Käynnistä komentoriviltä muutamia ohjelmia, esim vlc-mediasoitin ja firefox selain. Selvitä mitkä ovat prosessien ID numerot ja millä prioriteetilla ohjelmat ajetaan? Ota kuvakaappaus tilanteesta.*  

VLC ID: 5956, prioriteetti 20.
Firefox ID: 5613, prioriteetti 20.

[![prosessit](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/prosessit.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/prosessit.png)

# 

### *2.2. Muuta prosessien nice-arvoja siten, että niitä ajetaan korkeammalla prioriteetilla.*  

[![prioriteetit](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/prioriteetit.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/prioriteetit.png)

# 

### *2.3. Lopeta prosessit komentorivillä käyttäen kill-komentoa. Kokeile erilaisia valitsimia. Kerro mitä valitsimet tekevät.* 

Prosessien lopettaminen työnumerolla: `kill %[työnumero]` 

Prosessin lopettaminen prosessin ID:llä: `kill [PID]` 

Prosessin lopettaminen ohjelman nimellä: `pkill [ohjelma]` tai `killall [ohjelma]` 

**Seuraavaksi lopetetaan komentorivin avulla VLC sekä Firefox.**

* Tarkistetaan ensin käynnissä olevien taustaprosessien numerot komennolla `jobs` 

* Lopetetaan prosessit komennolla `kill %` työnumeroiden mukaan, VLC `[5]` sekä Firefox `[6]` .

* Tarkistetaan prosessit vielä uudelleen komennolla `jobs` . 

[![lopetettu](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lopetettu.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lopetettu.png)

# 

### *2.4. Miten lopettaisit käynnistämäsi sovellukset yhdellä komennolla?* 

`pkill -9 -f "\.\/.+\s\.|firefox|vlc|\[^"` 

# 

## 3. Resurssien valvonta ja järjestelmälokit 

### *3.1 Tee ohjattu harjoitus resurssien hallintaan liittyen luvusta 4.4. "Resurssien hallinta". Vastaa sen jälkeen seuraaviin kysymyksiin:* 

*Mikä palveu käyttää eniten suoritinta Htop sovelluksessa?*  

* PID 1796 - cinnamon.

*Mikä palvelu käyttää eniten muistia?*  

* PID 1796 - cinnamon.

*Kuinka pitkään tietokone on ollut käynnissä?*  

* 32 minuuttia.

*Kuinka paljon muistia on käytössä yhteensä ja mikä on kokonaismäärä?*  

* 620M / 3.85G.

*Käynnistä Firefox prosessi, etsi se htop sovelluksella ja lopeta prosessi.*  

Lopetan Firefox prosessin lähettämällä signaalin `9 SIGKILL` . 

[![firefox](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/firefox.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/firefox.png)

*Käyttäen Iostat sovellusta katso kuinka paljon levylle on kirjoitettu yhteensä edellisen käynnistyksen jälkeen? Kuinka paljon dataa on luettu?*  

Kirjoitettu 75MB, luettu 691MB.

[![kirjoitettu-2](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/kirjoitettu-2.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/kirjoitettu-2.png)

*Mikä on ollut koneesi keskimääräinen ulospäin menevä liikenne?*  

224.00 Bit/s.

*Kuinka paljon koneesi on ladannut dataa yhteensä?*  

12.33 kByte.

[![verkkoliikenne](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/verkkoliikenne.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/verkkoliikenne.png)

*Mikä on koneesi lokaali IP-osoite?*  

10.0.2.15

[![ip-osoite](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ip-osoite.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ip-osoite.png)

*Testaa toimiiko yhteys www.laurea.fi osoitteeseen. Mikä IP-osoite vastaa osoitteesta?*  

30 pakettia lähetetty, 23 vastaanotettu, 23% hävikki, aikaa testiin kului 29449 millisekuntia (29,449 sekuntia). 

[![ping](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ping.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ping.png)

*Kuinka monta reititintä on matkalla virtuaalikoneestasi osoitteeseen www.laurea.fi?*  

Ainakin yksi, muutoin * -kappaletta. 

[![reitittimet](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/reitittimet.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/reitittimet.png)

# 

### *3.2 Asenna graafisessa käyttöliittymässä jokin sovellus, jolla voit tutkia järjestelmän lokitiedostoja. Avaa jokin järjestelmän lokeista (hakemistosta /var/logs).* 

[![logs](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/logs.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/logs.png)

# 

### *4. Kokeile tutkia syslog tai messages-tiedostoa käyttämällä "tail -f "komentoa (reaaliaikainen tiedoston seuranta). Missä tilanteissa tällaista seurantaa mielestäsi voisi hyödyntää?*

Lokien hallinta on olennainen osa palvelimen järjestelmänvalvojan vastuuta. Linux-lokitiedostoja tarkkailemalla saa yksityiskohtaisia ​​tietoja palvelimen suorituskyvystä, tietoturvasta, virheilmoituksista ja niiden taustalla olevista ongelmista. Jos haluaa käyttää ennakoivaa lähestymistapaa palvelimen hallintaan, lokitiedostoja on hyvä seurata myös reaaliajassa.

[![syslog](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/syslog.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/syslog.png)

---

[Teema 5](../teema5/README.md)