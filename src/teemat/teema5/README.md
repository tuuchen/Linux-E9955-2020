[Takaisin alkuun](../../../README.md)

# Palvelin ja tietoturva-asiaa

Asensin teemaa varten Virtual Boxiin valmiin [Kali Linuxin](https://www.osboxes.org/kali-linux/) levykuvan, jonka päivitin komennoilla `sudo apt-get update` sekä `sudo apt-get dist-upgrade`. Tällä tavoin Kaliin hyppääminen oli varsin helppoa ja nopeaa.

[![Kali](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/Kali.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/Kali.PNG)

## 5. Palveluita

### *5.1. Käynnistä Linux-terminaali ja tutki järjestelmän palveluita. Kuinka monta palvelua on running tilassa?*

[![prosessit-kali](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/prosessit-kali.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/prosessit-kali.png)

- 19 prosessia.

### *Etsi rsyslog -niminen palvelu. (Lue teoriaosa 5.1!) Millä komennolla löydät palvelun?*  

- `whereis rsyslog` kertoo palvelun sijainnin.
- `service rsyslog status` kertoo palvelun statuksen.

*Selvitä:*   

*- Onko palvelu käytössä? (enabled)*  

- Kyllä on.

*- Onko palvelu käynnissä? (running)*  

- Kyllä on. 

*- Mikä on Rsyslog palvelun PID?*  

- 557

[![rsyslog](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/rsyslog.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/rsyslog.png)


*- verkosta tai man-sivuilta mitä kyseinen palvelu tekee?*  

- rsyslog kirjaa tietoja erityyppisistä järjestelmistä. Rsyslog on edistyksellinen versio syslogista, ja siinä on uusia hienoja juttuja, kuten: 
    - Voit kuunnella TCP / UDP yhteyksiä rajoituksin (portit, lähde-IP: t)
    - Voit ladata paljon moduuleja
    - Voit erottaa lokisuodatuksen ohjelman, lähteen, viestin, pid jne. Mukaan (esimerkiksi jokainen viesti, joka on merkitty "yhteys suljettu" -sanomaan tiedostoon closed.log)
    - Voit hylätä viestin yhden tai useamman säännön jälkeen

*Uudelleenkäynnistä Rsyslog palvelu.*  

- `sudo systemctl restart rsyslog`

[![rsyslog-restart](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/rsyslog-restart.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/rsyslog-restart.png)

*Luo sen jälkeen uusi palvelu nimeltä testi. Palvelun tulee sisältää seuraava bash skripti:*

`echo "Testi starttaa"
while :
do
[ -d "/home" ] && echo "Directory /home/ exists.";
sleep 15s;
done`

*Ota kuva tekemästäsi palvelusta sekä palvelun Statuksesta.*  

[![testipalvelu](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/testipalvelu.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/testipalvelu.png)


*Mikä on palvelun PID?*   

- 1405

*Mitä statuksessa tulostetaan?* 

- Status kertoo, että /home/ hakemisto on olemassa. 

#

### *5.2. Linuxin kovennus*

### *TEHTÄVÄ A: PALOMUURIN ASENNUS JA MUOKKAUS*

*Asenna Linuxiisi UFW sekä GUFW -palomuurisovellukset. Käynnistä palomuuri ja katso sen status.*

[![gufw](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/gufw.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/gufw.png)


*Selvitä millaisia sääntöjä palomuurissasi on oletuksena?*

- Oletuksena tuleva liikenne on kielletty, ja lähtevä sallittu. 
 
*Salli kaikki http ja https liikenne koneelle* 

[![fw-allow](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/fw-allow.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/fw-allow.png)

*Kiellä kaikki saapuva ftp liikenne koneelle* 

[![ftp-deny](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ftp-deny.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ftp-deny.png)

*Kiellä kaikki ulospäin lähtevä liikenne koneelle porttiin 25* 

[![port-deny](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/port-deny.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/port-deny.png)

*Kiellä kaikki liikenne koneelle IP osoitteesta 15.15.15.51*  

[![ip-deny](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ip-deny.png)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/ip-deny.png)

### *TEHTÄVÄ B: LINUXIN KOVENNUS*

*1. Asenna Linuxiin ClamAV antivirus-ohjelma. Skannaa sillä kotihakemistosi.*  

[![scan](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/scan.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/scan.PNG)

*2. Tee myös kovennuslistan vaiheet 1 ja 3, "päivitykset", sekä "minimoi asennetut sovellukset."*  

- Päivitykset

[![update-1](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/update-1.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/update-1.PNG)  

- Katsaus asennettuihin sovelluksiin. Luotan tässä vaiheessa, että Kali-levykuva sisältää ainostaan tarpeellisia sovelluksia. Haluan myös säilyttää Apachen osana Linux jakeluani. Ylimääräisen sovelluksen poistaminen tapahtuu kuitenkin komennolla `apt-get remove [paketti]`

[![sovellukset-1](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/sovellukset-1.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/sovellukset-1.PNG)

*3. Valitse lisäksi kaksi haluamaasi kovennusta ja tee ne järjestelmääsi.* 

- Määritin palomuurin estämään sisään tulevan liikenteen.  

[![kovennus-1](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/kovennus-1.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/kovennus-1.PNG)

- Auditoin järjestelmän Lynis sovelluksella.  

[![lynis](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lynis.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/lynis.PNG)

### *5.3. Salasanojen murtaminen / testaus*

### *TEHTÄVÄ A: Salasanojen murtaminen*

*1-2. Luo Linuxiin kolme uutta käyttäjää aiemmin opitulla tavalla. Anna käyttäjille nimeksi: heikko, keski ja vahva. Nimet kuvaavat salasanojen vahvuutta.*

*Anna käyttäjälle heikko salasanaksi kolmen kirjaimen mittainen salasana, esim. "hei".*

*Anna käyttäjälle keski salasanaksi hieman pidempi salasana jossa on jo iso kirjain ja numero, esim. "Heik5".*

*Anna käyttäjälle "vahva" salasanaksi itse keksimäsi isoista ja pienistä kirjaimista, numeroista ja erikoismerkeistä koostuva salasana. Tätä harjoitusta varten salasanan pituus kannattaa pitää alle 5 merkin, muuten sen murtamisessa voi kestää todella pitkään.* 

*Kokeile lopuksi murtaa äsken luomasi käyttäjien salasanat.*

[![john-1](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/john-1.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/john-1.PNG)

- keski, sekä vahva -salasanojen murtaminen vesijäähdytetyllä, sekä 5.1 -gigahertsin kellotaajuudella toimivalla 8-ytimisellä i9-prosessorilla kesti huomattavan kauan, joka sikäli on lohdullista, mutta heikko sekä kali -käyttäjien salasanat ratkesivat varsin nopeasti. Resurssien säästämiseksi en jatkanut testiä loppuun asti.

### *TEHTÄVÄ B: Salasanojen murtaminen sanakirjan avulla*

*1. Tietokone voi helposti käydä läpi miljoonien salasanojen listan. Yhden suositun listan voi ladata esim. [täältä.](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt) Katso tiedoston sisään - montako riviä (eli salasanaa) tiedostossa on?*

- 14344394 riviä / salasanaa.

[![rockyou](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/rockyou.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/rockyou.PNG)

*2. Tallenna ao. salasanat teksitiedostoon ja koita murtaa ne käyttäen Johnnyssä edellä lataamaasi salasanatiedostoa. Kuinka helposti salasanat murtuvat? Murtuvatko kaikki? Ota kuvakaappaus ohjelman tuloksista ja selväkielisistä salasanoista.*

*ab87d24bdc7452e55738deb5f868e1f16dea5ace  
01f7b6a103603487e5ffd126ade782d2bcdd8922  
08ef1bdfe3096a52749aaa74f1a12cfc04d54e80  
e38ad214943daad1d64c102faec29de4afe9da3d  
55be6dcac991480ba75e05bd72065450af15248e  
56d9e9f2b6c560bb23e2ff136c24e3fb7e077e7c*  

- rockyou.txt:n avulla murtui kolme salasanaa.

[![john-2](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/john-2.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/john-2.PNG)

*3. Kokeillaan vielä suomalaisten suosimia salasanoja. Sellaiseenkin on olemassa sanalistoja, esim. [täällä.](http://www.mediafire.com/file/1z0aa9kraz5sr6r/finnish-unknown.txt.gz) Lataa ja pura paketti, katso miltä se näyttää ja montako riviä (eli salasanaa) se sisältää?*

- 36323 riviä / salasanaa.

[![john-3](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/john-3.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/john-3.PNG)
