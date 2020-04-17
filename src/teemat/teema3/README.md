[Takaisin alkuun](../../../README.md)

# Komentorivin käyttö

## 1. Komentojen putkitus ja yhdistely

Komento: `cat /var/log/syslog | wc -l`

- Kommenolla tutkitaan syslog nimisen tekstitiedoston rivimäärää.

Tuloste: `179`

---

Komento: `ls -l | sort -r | more`

- Komento listaa nykyisessä polussa olevat tiedostot, järjestää ne käännetyssä järjestyksessä (uusimmasta vanhempaan), ja more -komennolla tuloksia on helppoa selata sekä etsiä.

Tuloste: `total 40`  
`-rw-r--r-- 1 osboxes osboxes 10 Apr 5 16:16 myoutput`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 16:06 Documents`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 16:06 Desktop`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 16:02 omatjutut`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 15:31 Videos`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 15:31 Templates`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 15:31 Public`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 15:31 Pictures`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 15:31 Music`  
`drwxr-xr-x 2 osboxes osboxes 4096 Apr 5 15:31 Downloads`

---

Komento: `ls | head -3 | tail -1 > myoutput`

- Tulostaa pelkästään nykyisessä polussa olevan kolmannen tiedostonimen.

Tuloste: Tekstitiedosto `myoutput` joka sisältää sanan `Documents`

---

## 2. Tiedostojen etsiminen

Miten etsisit locate -komennolla kaikkia tietokoneen mp3 -päätteisiä tiedostoja?

`locate *-mp3`

---

Miten etsisit find-komennolla tiedostoja, joita on muokattu tänään?

`find . -mtime -1 -print`

---

Miten etsisit tietokoneesta yli 10 Megatavun kokoisia tiedostoja?

`find . -size +10M`

---

Mitä tekevät find-komennon valitsimet -exec ja -ok?

`-exec` ajaa löydetyille tiedostoille haun yhteydessä määritetyn komennon ilman lisäilmoitusta, `ok` komento näyttää käyttäjälle ilmoituksen ennen komennon suorittamista.

---

Mitä tekevät komennot which ja whereis? Miten ne eroavat toisistaan?

`which` näyttää (shell) -komentojen polun PATH -muuttujan alta, `whereis` etsii komennon binääriset, lähde- ja manuaaliset sivutiedostot.

---

## 3. Tiedostojen pakkaaminen

Pakkaa kotihakemistosi kaikkine alihakemistoineen tar.gz –pakettiin

Komento: `tar cvfz uusipaketti.tar.gz *`

- Pakatun tiedoston koko: 83.8 kB

---

Tee sama xz - pakkausohjelmalla

Komento: `tar cvfJ toinenpaketti.tar.xz *`

- Pakatun tiedoston koko: 40.7 kB

---

Vertaa tiedostojen kokoa, paljonko niillä on eroa?

- XZ pakkaa tehokkaamin, tässä tapauksessa puolittaen pakatun tiedoston koon.

## 4. Tiedostojen ja hakemistojen oikeudet

Listaa joku kohdassa kolme pakkaamistasi tiedostoista ja tarkastele sen oikeuksia. Erittele kenellä on oikeus lukea, suorittaa ja kirjoittaa tiedostoa?

`-rw-r--r-- 1 osboxes osboxes 83837 Apr 8 10:08 uusipaketti.tar.gz`

Käyttäjällä `osboxes` on oikeus **lukea** sekä **kirjoittaa** tiedostoa `uusipaketti.tar.gz`.

Ryhmällä `osboxes`, sekä muilla käyttäjillä on oikeus lukea tiedostoa.

---

Muuta tiedoston oikeuksia siten, että kaikilla on oikeus lukea ja kirjoittaa sitä. Esitä ratkaisu sekä kirjain- että numeromuotoista komentoa käyttäen.

Kirjaimin: `chmod a=rw- uusipaketti.tar.gz`

Numeroin: `chmod 666 uusipaketti.tar.gz`

---

Miten poistaisit kohdan b tiedostolta kirjoitusoikeudet kaikilta? Lukuoikeudet saavat jäädä. Esitä ratkaisu sekä kirjain- että numeromuotoista komentoa käyttäen.

Kirjaimin: `chmod a-w uusipaketti.tar.gz`

Numeroin: `chmod 444 uusipaketti.tar.gz`

---

Luo hakemisto ja anna kaikille lukuoikeus sinne, mutta vain omistajalla tulisi olla kirjoitus ja suoritusoikeus siihen. Esitä ratkaisu sekä kirjain- että numeromuotoista komentoa käyttäen.

Kirjaimin: `mkdir -m go-wx hakemisto`

Numeroin: `mkdir -m 744 hakemisto`

## 5. Grep

### Tietojen etsiminen [teksimassan](regexr.com/50udq) seasta

Sosiaaliturvatunnus:

- Syöte: `grep '[0-9]\{6}-\{0,1\}[0-9]\{3\}[A-Z]\{1\}'`

- Tuloste: `130554-234B`

Sähköposti:

- Syöte: `grep -Eiorh '([[:alnum:]_.-]+@[[:alnum:]_.-]+?\.[[:alpha:].]{2,6})'`

- Tuloste: `foo@demo.net bar.ba@test.co.uk mika@sci.fi mika.stenberg@laurea.fi`

IP-osoite:

- Syöte: `grep -E -o '([0-9]{1,3}[\.]){3}[0-9]{1,3}'`

- Tuloste: `255.255.255.0 127.0.0.1`

### Tietojen etsiminen [teksitiedostosta](http://www.gutenberg.org/cache/epub/14152/pg14152.txt)

Asianajaja, poliisi, lääkäri yhdellä komennolla:

- Syöte: `grep 'asianajaja\|poliisi\|lääkäri'`

Tohtori Jekyll, sekä lukumäärä:

- Syöte: `grep -c 'Tohtori Jekyll'`

- Tuloste: `5`

Rivit, jotka eivät sisällä sanoja "elämä, ei, kuolema":

- Syöte: `grep -vE 'elämä|ei|kuolema'`

## 6. AWK

Käyttäjätunnus -sarake tiedostosta /etc/passwd:

- Syöte: `awk -F: '{print $1}' /etc/passwd`

Aakkosjärjestys edelliseen:

- Syöte: `awk -F: '{print $1}' /etc/passwd | sort`

Käyttäjän komentorivitulkin nimi:

- Syöte: `awk -F: '{print $7}' /etc/passwd`

## 7. SED

Merkkijonon `lääkäri` korvaaminen merkkijonolla `puoskari`

- Syöte: `sed -i 's/lääkäri/puoskari/g'`

Sama kuin edellä, mutta tulostus toiseen tektstitiedostoon

- Syöte: `sed 's/lääkäri/puoskari/g alkuperäinen.txt > kohde.txt`

Miten etsit tiedostosta sanaa veturi ja lisäät kaikkien sen esiintymien ympärille lainausmerkit?

- Syöte: `sed -i 's/veturi/"veturi"/g`

## 8. Tiedostojen manipulointi

Käytä paste komentoa kolmen tiedoston tietojen liittämiseksi yhteen tiedostoon

- Syöte: `paste nimet.txt numerot.txt osoitteet.txt > yhdistetty.txt`

Jaa isompi tekstitiedosto 500-rivin tiedostoihin

- Syöte: `split -l 500 alkuperäinen.txt`
