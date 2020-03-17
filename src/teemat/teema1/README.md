[Takaisin alkuun](../../../README.md)

# 1\. Johdatus Linuxiin

- ### Mihin asioihin jakelupaketin valinnassa kannattaa kiinnittää huomiota ja millaisia ominaisuuksia käyttäjille olisi tarjolla? (A)

Linuxiin perustuvia käyttöjärjestelmiä eli jakeluita on satoja, joten kannattaa kiinnittää huomiota siihen, mitä käyttöjärjestelmältä haluaa ja mitä ominaisuuksia siihen tarvitsee, ja yksi keino tämän hahmottamiseen on omat käyttötottumukset, esimerkiksi viihde, työ- tai pelikäyttö.

Huomionarvoista on myös, että vaikka Linuxin asetuksia voidaan hallita graafisella käyttöliittymällä, ilman Linuxin komentorivin hallinnan opettelua ei Linuxia kannata tosissaan harkita.

Linuxin vahvuutena on kuitenkin vaihtojen tarjoaminen, ja jakelupaketin käyttöliittymiä voidaan tyypillisesti asentaa vapaasti eri versioiden välillä, mutta oletuksena jakelupakettien mukana tulee kuitenkin omansa.

Käyttäjän kannattaa ottaa siis myös huomioon, että kuinka paljon käyttöliittymää haluaa itse muokata. Esimerkkinä Gnome jakelu tarjoaa käyttöliittymältä yksinkertaisuutta, ja puolestaan KDE jakelu antaa käyttäjän muokata käyttöliittymää lähes loputtomasti.

Linux käyttöjärjestelmien päivitykset tapahtuu paketinhallinnan kautta, ja Linux käyttöjärjestelmien päivitysmalli on jakautunut kahteen leiriin, jossa toisessa päivitykset tapahtuvat isomman puolivuotisen koko jakelun kattavan päivityksen yhteydessä, ja toisessa päivityksiä tulee säännöllisin väliajoin. Säännölliset päivitykset tarjoavat käyttäjälle uusimpia ominaisuuksia, mutta riskinä on järjestelmän rikkoontuminen viallisen päivityksen yhteydessä.

Hitaampi päivitysmalli tarjoaa siis käyttäjälle vakaampaa toimintaa, ja nopeaa julkaisumallia suositellaan edistyneemmille käyttäjille.

Linuxiin on tarjolla yhä kattavampi tarjonta sovelluksia, mutta käyttäjän kannattaa ottaa huomioon, ettei Linuxilla voi varsinaisesti korvata Windows -käyttöjärjestelmää. Windowsin sovellukset eivät siis välttämättä toimi Linuxissa, mutta esimerkiksi Microsoft Officen voi Linuxissa korvata LibreOfficella sekä Photoshopin toimintoja vastaa Linuxissa Gimp. Myös pelikirjasto Linuxissa toimivissa peleissä on vastaavasti suppeampi kuin Windowsilla.

Käyttäjän kannalta huomionarvoinen asennustapa onkin niin sanottu dual boot, jossa tietokoneen käynnistämisen yhteydessä valitaan Windows tai Linux käyttöjärjestelmän väliltä, jolloin käyttäjä pääsee hyödyntämään molempien käyttöjärjestelmien parhaita puolia.

---

- ### Vertaa GPL-lisenssiä muihin suosittuihin avoimen lähdekoodin lisensseihin, kuten Apache ja MIT. Mitä eroja ja yhtäläisyyksiä näillä on? (C)

Yhtäläistä GPL, Apache sekä MIT -lisensseille on, että ne antavat vapaasti luvan lähdekoodin käyttämiseen sekä yksiyiseen että kaupalliseen käyttöön, kunhan alkuperiselle tekijälle annetaan tunnustus copyright huomautuksen muodossa. Niissä myöskin todetaan, että ohjelmiston toiminta ja vastuu jää ohjelmistokoodin käyttäjän kannettavaksi.

GPL-lisenssi on erityisesti Linuxin jakelusta tuttu avoimen lähdekoodin lisenssi, joka on MIT sekä Apache -lisenssistä poiketen niin sanottu copyleft-lisenssi, joka vaatii että lähdekoodista tuotetut teokset ovat myös GPL-lisenssin alaisuudessa, eikä siihen saa lisätä uusia rajoitteita. GPL-lisenssi vaatii myös, että muutoksista pitää lisätä huomio, ja ohjelman tulee sisältää tieto kyseisestä lisenssistä. GPL-lisenssin mukaisesti lähdekoodi pitää olla saatavana kaikille, joille lisenssin alaisuudessa olevaa ohjelmaa on levitetty. GPL-lisenssi siis kannustaa kehittäjiä suosimaan vaapata lähdekoodia.

MIT-lisenssistä poiketen Apache sekä GPLv3 -lisenssit sisältävät patenttisuojapykälän, joka antaa käyttäjälle oikeuden käyttää kaikkia ohjelmistosta tuotettuja patentteja lisensoidun ohjelmiston suorittamiseen, ja tämä oikeus raukeaa mikäli käyttäjä yrittää haastaa toisen käyttäjän patenttirikkomuksesta oikeuteen.

---

- ### Etsi verkosta tai haluamastasi lehdestä Linux-aiheinen uutinen ja kerro lyhyesti mistä oli kyse? (D)

[Maailman yleisin käyttöjärjestelmä keksittiin Suomessa – Tiesitkö, että käytät Linuxia päivittäin?](https://yle.fi/uutiset/3-9112625)

[![Video](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/uutinen-1.PNG)](https://areena.yle.fi/1-3675453)

Linux on maailman käytetyin käyttöjärjestelmä, vaikka ihmiset ei sitä välttämättä tiedosta. Ironista onkin, että vaikka Linux alunperin tarkoitettiin työpöytäkäyttöön, on Linux nimenomaan käyttöjärjestelmänä valloittanut kaiken muun, paitsi työpöydät. Syynä tähän on Windows käyttöjärjestelmän monopoliasema valmiiksi asennettuna käyttöjärjestelmänä työpöytälaitteissa.

Mobiilipuolella käyttäjä puolestaan saa hyvin todennäköisenä vaihtoehtona laitteeseen esiasennettuna Linux pohjaisen Androidin, sillä Androidin osuus myydyistä mobiililaitteista on jo noin 85%, ja kokonaisuudessaan Linux pohjaisia Android laitteita on Googlen mukaan aktiivisessa käytössä yli 1.4 miljardia.

Linux käyttöjärjestelmät ovat laajassa käytössä erityisesti palvelinympäristöstä, ja vastaavatkin monessa tapauksessa pilvipalveluiden toiminnasta, kuten Amazonin järjestelmistä, Facebookin tietokannoista, sekä Googlen hakutoiminnosta. Myös 99% maailmalla olevista supertietokoneista käyttää Linuxia. Linux on suosittu palvelinympäristöissä erityisesti sen luotettavuuden, modulaarisuuden, joustavuuden, sekä kustannustehokkuuden ansiosta.

Avoimen lähdekoodinsa ansiosta Linux on myös suosittu älyä sisältävässä kodin elektroniikassa, kuten esimerkiksi älytelevisioissa, älykelloissa, lieseissä tai pesukoneissa, kuin myös teollisuuden applikaatioissa, kuten bensapumpuilla sekä aikataulunäytöissä.

Kuten uutisessa mainittiin, olet todennäköisesti tämän luettuasi tänäänkin hyödyntänyt Linuxia!

# 2\. Linux työmarkkinoilla

- ### Miltä näyttää Linux-osaajien työtilanne tällä hetkellä [Open Source Job Reportin 2018](https://www.linuxfoundation.org/wp-content/uploads/2019/10/osjobsreport_2018.pdf) ja [Linux Job Reports 2017](https://resources.linuxfoundation.org/LF+Core/publication_Linux_2017_Jobs_Report_final.pdf) -raportin mukaan? Miten tilanne on kehittynyt edellisiin vuosiin verrattuna?

Vuoden 2018 raportin mukaan avoimen lähdekoodin osaajien rekrytointi on tällä hetkellä prioriteettina 83%:lle rekrytoinnista vastaavista esimiehistä, joka on 76%:n kasvu vuoteen 2017 verrattuna, ja nimenomaan Linux osaaminen on eniten etsitty taito avoimen lähdekoodin osaajien keskuudessa.

Linux osaaminen on 2018 raportin mukaan tällä hetkellä vähimmäisvaatimus alkutason pilvipalvelu- sekä niiden ylläpitotyötehtäviin, ja osaamispulan takia yritykset ovat siirtyneet uudelleenkouluttamaan yrityksen nykyisiä työntekijöitä sekä päivittämään serftifikaatein heidän osaamistaan.

Tämä puolestaan tarkoitti 2018 raportin mukaan hyvää työllisyystilannetta Linux osaajien keskuudessa, joiden työttömyystaso oli laskenut edelliseen vuoteen verrattuna.

Tarkat luvut Linux- sekä avoimen lähdekoodin osaajapulasta ja rekrytointitavoitteista vaihtelivat hieman 2018, 2017, aina 2012 raporttiin asti, mutta osaajapula on kuitenkin ollut jo vuosia jatkuva trendi, jonka seurauksena rekrytoijat sekä työnantajat käyttävät vahvoja keinoja osaajien löytämiseksi, kuten houkuttelevaa palkkaa sekä työsuhde-etuja.

Linux osaaminen on siis taito, joka antaa hyvät edellytykset työllistyä IT-alalle, esimerkiksi pilvipalveluiden sekä niiden järjestelmien ylläpitotyötehtäviin.

---

- ### Etsi verkosta ja lehdistä työpaikkailmoituksia, joissa haetaan/tarvitaan Linux-osaajia tai osaamista, millaisia löysit? Mitä osaamista ilmoituksissa erityisesti kaivataan, mille aloille ja mihin tehtäviin ilmoitukset sijoittuvat?

TE-palveluiden sivusto löysi 17.3.2020 "Linux" -hakusanalla 79 työpaikkaa. Linuxiin liittyviä toimialoja olivat:

- Tekniikan erityisasiantuntijat
- Myynnin, markkinoinnin ja tiedotuksen asiantuntijat
- Systeemityön erityisasiantuntijat
- Tietokantojen,- verkkojen ja ohjelmistojen asiantuntijat
- Fysiikan, kemian ja teknisten alojen asiantuntijat
- ICT-alan teknikot ja käyttäjätukihenkilöt
- Sähkölaitteiden asentajat ja korjaajat

Ohessa kolme erilaista Linuxiin liittyvää työtehtävää:

1. [Ohjelmistokehittäjä](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/työpaikka-1.PNG)

CSC-Tieteen ja tietotekniikan keskus etsi itselleen ohjelmistokehittäjää datan sekä metatietojen tallenukseen sekä niihin liittyviin hallintaprosesseihin ja vaatimuksena tehtävään oli lueteltu Linuxin sekä CentOS 7 tuntemus, kuin myös full stack kehitykseen liittyviä tekniikoita, kuten:

- Python, Django, DRF
- JavaScript, HTML5, CSS, frontti frameworkit
- Relaatiotietokannat, PostgreSQL

Työtehtävässä siis kaivattiin ohjelmointiosaamisen lisäksi ymmärrystä Linux järjestelmän toiminnasta.

---

2. [Tekninen asiakaspalvelija](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/työpaikka-2.PNG)

Vitec Software Group Ab etsi kehittymishaluista vahvan teknisen osaamisen sekä asiakaspalvelutaustan omaavaa henkilöä ratkomaan asiakkaiden ongelmatilanteita, ja vaatimuksena tehtävään vaadittiin vahvaa työasema- ja palvelinosaamista sekä Windows, että Linux ympäristöstä.

Nykyään työelämässä tyypillistä onkin, että etsitään osaajia, joilla yhdistyy tekninen osaaminen (esimerkiksi Linux osaaminen) kirjallisiin taitoihin, asiakaspalvelutaitoihin, kuin myös kielitaitoihin. Tässäkin työtehtävässä Linuxin sekä Linux palvelinympäristön tunteminen on varmasti valttikortti erottua joukosta.

---

3. [Linux Specialist](https://raw.githubusercontent.com/tuuchen/Linux-E9955-2020/master/src/materiaali/työpaikka-3.PNG)

Telia etsii Linux-osaajaa vahvistamaan Datacenter & Cloud Service yksikköä, ja työtehtävässä tehdään vaativaa ongelmanhallintaa. Työtehtävässä onnistumisessa vaaditaan:

- Ymmärrystä Linuxin palvelinkäyttöjärjestelmistä
- Verkkoteknologioiden ymmärrystä, kuten IP-verkot, palomuurit sekä kuormantasaus
- Kokemusta tietokantasovelluksista sekä niiden optimoinnista
- Kokemusta tietokantapalvelimien ylläpidosta
- Kokemusta tai halua opetella scriptausta
- Halua suorittaa AWS sertifiointi ensimmäisen 6kk:n aikana

Linux-käyttöjärjestelmän tuntemisesta on siis etua erilaisissa IT-alan työtehtävissä, oli työtehtävä ohjelmistokehitystä, asiakaspalvelutyötä tai vaativaa pilvipalveluiden ylläpitoa, mutta myös halukkuutta uuden oppimiseen ja työtehtävässä kehittymiseen esimerkiksi sertifikaattien osalta arvostetaan.

---

- ### Selvitä mikä on avoimen lähdekoodin rooli ja mihin Open Source -sovelluksia käytetään työmarkkinoilla tänä päivänä?

Tekstiä

---
