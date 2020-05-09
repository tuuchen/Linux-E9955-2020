[Takaisin alkuun](../../../README.md)

# Järjestelmän ylläpito

## 1. Käyttäjähallinta

*1.1. Luo kaksi uutta käyttäjää (opettaja ja opiskelija). Aseta käyttäjille myös kotihakemistot. Käytä toisen luomisessa komentorivia ja toisen graafista käyttöliittymää.*

Luodaan komentorivin avulla opettaja, sekä opettajan hakemisto. 

Käytin tässä `sudo useradd --create-home -d /home/opettaja opettaja` -komennon sijaan Linuxista löytyvää `adduser` -komentoa, joka tarjoaa näppärän komentorivinkäyttöliittymän käyttäjän lisäämiseen.  
  
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

*1.2. Lisää toinen käyttäjistä ryhmään nimeltä “opiskelijat” ja toinen ryhmään "opettajat". Käytä ainakin toisessa operaatiossa komentorivia.*

`sudo usermod -a -G opettaja opettaja`

[![ryhmät](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ryhmät.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ryhmät.png)

#

*1.3. Luo hakemistot “opiskelijoiden_tiedostot” ja "opettajien_tiedostot", joille annat oikeudet vain asianosaisille ryhmille. Varmista kokeilemalla molemmilla käyttäjillä, että oikeudet ovat voimassa. Käytä ainakin toisessa operaatiossa komentorivia.*

Opiskelijat:

`sudo mkdir /home/opiskelija/opiskelijoiden_tiedostot | sudo chown opiskelija /home/opiskelija/opiskelijoiden_tiedostot | sudo chgrp opiskelija /home/opiskelija/opiskelijoiden_tiedostot | sudo chmod 770 /home/opiskelija/opiskelijoiden_tiedostot`  

Opettajat:

`sudo mkdir /home/opettaja/opettajien_tiedostot | sudo chown opettaja /home/opettaja/opettajien_tiedostot | sudo chgrp opettaja /home/opettaja/opettajien_tiedostot | sudo chmod 770 /home/opettaja/opettajien_tiedostot`  

Testi:

[![oikeudet](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/oikeudet.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/oikeudet.png)



#

*1.4 Lukitse "opiskelija" käyttäjän tunnus väliaikaisesti. Voit tehdä tämän joko komentoriviltä tai graafisesta käyttöliittymästä.*

Lukitaan opiskelija: 

`sudo usermod -L opiskelija` 

[![lukittu](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lukittu.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lukittu.png)

