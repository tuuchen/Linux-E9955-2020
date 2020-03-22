[Takaisin alkuun](../../../README.md)

# Linuxin asennus ja peruskäyttö

## 1. Linuxin asentaminen paikallisesti

### A. VirtualBox sekä Linux Mint

[Virtual Boxin](https://www.virtualbox.org/wiki/Downloads) versioksi valikoitui uusin 6.1.4, ja [Linux Mintin](https://www.osboxes.org/linux-mint/) versioksi valitsin valmiina levykuvana 64-bittisen 19.2 Tessa -version. Linux Mint on helppokäyttöinen, moderni ja miellyttävä Linux jakelu Linuxiin tutustumista ajatellen. Osboxes -sivulta löytyvän [ohjeen](https://www.osboxes.org/guide/) avulla Linux Mintin asennus virtuaalikoneeseen kävi mutkitta.

[![Mint](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/Mint.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/Mint.PNG)

Määritin Linux Mint -virtuaalikoneeseen hieman enemmän keskusmuistia (2048) suositellun 1024mb sijaan, sekä kytkin päälle 3D-kiihdytyksen 128mb videomuistilla.

Linux Mint virtuaalikoneen resoluution muuttamiseksi latasin myös ohjeessa näytetyn Guest Additions -levykuvan, ja levykuvan asettaminen Linux Mint virtuaalikoneeseen pöräytti Mintin työpöydältä asennuksen automaattisesti käytiin, ja hoitui näin valmiiksi saakka.

### B. Mielenkiintoiseen jakeluun tutustuminen - SteamOS

Debian jakeluun perustuva SteamOS -käyttöjärjestelmä on kiinnostanut minua vuoden 2013 ensimmäisestä julkaisusta asti. SteamOS on avoimeen lähdekoodiin perustuva kevyt, selkeä, suositun pelikirjaston päälle rakennettu käyttöjärjestelmä videopelaamiseen tarkoitetun tietokoneen käyttöjärjestelmäksi, jossa resurssit eivät mene hukkaan raskaan taustalla olevan käyttöjärjestelmän takia, ja jolla toisaalta myös onnistuu hiiren ja näppäimistön avulla PC:llä tarkoitettu peruskäyttö.

Raudasta ja rakentamisesta kiinnostuneelle henkilölle pelikonsolit eivät myöskään tarjoa kovinkaan paljoa mahdollisuuksia kustomoida, korjata tai päivittää laitteessa olevaa rautaa siinä määrin kuten kustomoidussa PC:ssä, joten SteamOS yhdistää konsolimaisen käyttöjärjestelmän PC:n laajennettavuuteen.

Mielenkiinnostani huolimatta aikaisempaa kokemusta minulla ei SteamOS:n asentamisesta ollut, joten käytin tilaisuuden hyväksi ja tutustuin SteamOS:ään virtuaalikoneen avulla.

SteamOS:n levykuva löytyi steamin [serveriltä](http://repo.steampowered.com/download/), ja verkosta löytyvien [ohjeiden](https://www.dedoimedo.com/computers/steamos-virtualbox.html) avulla asennus tapahtui helposti käyttöjärjestelmän näytöllä olevia kuvakkeita seuraamalla.

### Oletusnäkymä:

[![SteamOS](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/SteamOS.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/SteamOS.PNG)

### Työpöytänäkymä:

[![Desktop](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/SteamOS_Desktop.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/SteamOS_Desktop.PNG)

Ainut pienimuotoinen haaste oli Guest Additions asentaminen SteamOS:ään resoluution vaihtamiseksi. Tämä ei onnistunut SteamOS:n työpöydältä löytyvän komentorivin avulla, sillä se johti virheilmoitukseen ja virtuaalikoneen näytön pimenemiseen.

SteamOS virtuaalikoneen uudelleenkäynnistys antoi valinnaksi "recovery" -tilassa käynnistämisen, jonka komentorivin kautta Guest Additionsin sai lopulta asennettua, ja jonka jälkeen SteamOS heräsi uudelleen henkiin.

Toinen lisähaaste myös tässä oli että recovery-tilan komentorivi totteli US-mallisen näppäimistön syötteitä. Verkosta löytyvän US-näppiksen layoutin kuvalla tästäkin kuitenkin selvittiin, ja alun hämmenyksen jälkeen komentoriviin sai syötettyä haluttuja merkkejä.

## 2. Vaihtoehtoisia asennustapoja

### A. Linux Azure-pilvessä

Azure-pilveen oli kurssilaisille luotu kirjautumislinkit, joiden avulla Azuressa olevaa Linux-konetta pääsi RPD-työpöytäyhteydellä käyttämään. Ensimmäisen yhteyden muodostaminen kuitenkin kesti huomattavan pitkään, mutta kärsivällisesti odottamalla yhteys lopulta muodostui.

[![RPD](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/RPD.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/RPD.PNG)

SSH-etäyhteyden muodostaminen Azure-pilvessä olevaan Linux-koneeseen onnistui myös näppärästi komentrivin kautta.

[![VM](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/VM.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/VM.PNG)

### B. Linux USB-tikulle - Linux Mint & Puppy Linux

Linuxia pystyy käyttämään myös ulkoisesta tallennusmediasta, kuten USB-tikulta, ja Linuxista löytyy myös hyvin pienikokoisia jakeluita, kuten DSL (50mb) tai Puppy Linux (300mb).

Yksi helppokäyttöinen asennusohjelma Linuxin asentamiseen USB-tikulle on pendrivelinuxin [YUMI](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/), jonka listalta löytyy kattava valikoima valmiiksi tuettuja Linux-asennuksia.

Myös kattavan valikoiman muitakin levykuvia voi YUMI:lla asentaa ulkoiseen tallennusmediaan, esimerkiksi YUMI:lla voi myös tehdä USB-tikulle SteamOS:n levykuvan, jolla SteamOS:n voi asentaa isäntälaitteen kovalevylle.

Asensin YUMI:n avulla pöytälaatikon pohjalta löytyneelle 4-gigatavun USB 2.0 -tikulle kaksi eri kokoista Linux jakelua, jo ennestään tehtävässä esitellyn Linux Mintin, sekä pienemmän [Puppy Linuxin](http://puppylinux.com/) Bionic Puppy 64-bit -jakelun.

Tein VirtualBoxiin uuden virtuaalikoneen, jolla lähdin kokeilemaan Linuxin käynnistystä USB-tikun kautta. Virtuaalikoneen USB:lta käynnistämistä varten latasin vielä [Plop Linuxin](https://www.plop.at/en/ploplinux/index.html) boot-managerin, jonka levykuvan syötin virtuaalikoneen levyasemaan, ja tällä tavoin emuloin USB-tikulta käynnistämistä samalla tapaa kuin oikeassa laitteessa.

YUMI:n multiboot tarjoaa usean Liuxin käynnistämisen yhdestä tallennusmediasta.

[![USB](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB1.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB1.PNG)

### Linux Mint

Ensimmäisenä vuorossa oli Linux Mintin käynnistäminen. Vanhan USB 2.0 -tikun olemattoman tiedonsiirtonopeuden takia käyttöjärjestelmän käynnistys kesti noin puoli ikuisuutta. Tästä tuli siis selväksi, että kevyemmät Linux versiot sopivat paremmin hitaampiin laitteisiin. Toisaalta modernin Linuxin asentamiseen kannattaa käyttää nopeaa tallennusmediaa (esimerkiksi USB 3.0 tai uudempi).

Pitkän odotuksen jälkeen aukesi työpöytänäkymä:

[![Mint-USB](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB2.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB2.PNG)

### Puppy Linux: Ubuntu Bionic 64

Kevyempään Puppy Linuxiin perustuvan Ubunty Bionic 64:n käynnistys vanhan USB 2.0 -tikun avulla onnistui huomattavasti nopeammin. Käynnistys tapahtui noin muutamassa minuutissa, ja työpöydällä odotti ohjattu asennus, josta sai valittua mm. aikavyöhykkeen, kieliasetukset, ym. käyttäjälle mieluisia asetuksia.

Bionic vaikutti pienestä koostaan huolimatta todella monipuoliselta paketilta.

[![Mint-USB](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB3.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB3.PNG)

Latasin vielä kokeilumielessä Bionicin pakettienhallinnasta uuden teeman vastaamaan Window XP:n vastaavaa.

[![Mint-USB](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB4.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/USB4.PNG)

Halusin jatkaa vielä Bioniciin tutustumista hieman nopeammassa laiteympäristössä, joten tein sille VirtualBoxiin oman Puppy Linux-virtuaalikoneen, jonka käyttöjärjestelmän asensin USB-tikulla olevan Bionic Linuxin asennusohjelman kautta.

[![Puppy-installer](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/installer.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/installer.PNG)

Asennusohjelman avulla USB-tikulla olevan Bionic-käyttöjärjestelmän asetukset siirtyivät suoraan virtuaalikoneeseen tehtyyn levytilaan.

[![Mint-USB](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/Puppy.PNG)](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/Puppy.PNG)
