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

- XZ pakkaa tehokkaamin puolittaen pakatun tiedoston koon.

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
