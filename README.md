# Verkefni-3-VESM2
 ### 3.1 LCD (5%)
Fylgdu eftirfarandi tutorial verklega [Character LCDs](https://learn.adafruit.com/character-lcds/overview) að Python & CircuitPython. Kynntu þér vel kóðann og hvað pinnarnir gera.
**Ath.** LCD með kóðanum er einnig á TinkerCad.

1. Svaraðu eftirfarandi spurningum:

   1. Hver er helsti munurinn á Character LCDs og Graphical LCDs?
   * __Svar:__ Persónu-LCD skjár er tilvalinn til að birta texta. Einnig er hægt að stilla þau til að sýna lítil tákn en táknin verða að vera aðeins 5x7 pixlar eða svo (mjög lítil!)
   Myndræna LCD-skjárinn er með eitt stórt pixlanet (í þessu tilfelli 128x64 þeirra) - Hann getur birt texta en bestur til að sýna myndir. Grafískar LCD skjáir hafa tilhneigingu til að vera stærri, dýrari, erfiðar í notkun og þurfa marga fleiri pinna vegna flækjunnar sem bætt er við.
   2. Hvað gerir RS pinninn á LCD?
   * __Svar:__ RS-pinninn lætur örstýringuna segja LCD-skjánum hvort hann vilji sýna þessi gögn (eins og í ASCII staf) eða hvort það sé skipanabæti (eins og að breyta stöðu bendilsins).
   3. Afhverju þarf að tengja RW-pinnann í jörð ef við erum ekki að nota hann?
   * __Svar:__ Vegna áhyggna af því að skrifa stafi á LCD-skjáinn.
   4. Hvað er hægt að birta marga stafi í LCD1602?
   * __Svar:__ 32 stafi alls (16 í línu)
   5. Afverju þarf að stýra LCD1602 með nokkrum pinnum (4 eða 8) á sama tíma? útskýrðu!
   * __Svar:__ D0-D7 eru pinnar sem eru með hráu gögnin (raw data) sem við sendum á skjáinn. RS-pinninn lætur örstýringuna segja LCD-skjánum hvort hann vilji sýna þessi gögn (eins og í ASCII staf) eða hvort það sé skipanabæti (eins og að breyta stöðu bendilsins). *EN*-pinninn er „virka“ línan sem við notum til að segja LCD skjánum þegar gögn eru tilbúin til aflestrar. RW-pinninn er notaður til að stilla stefnuna - hvort sem við viljum skrifa á skjáinn (algeng) eða lesa úr honum (sjaldgæfari)
   Góðu fréttirnar eru þær að ekki eru allir þessir pinnar nauðsynlegir fyrir okkur til að tengjast örstýringunni (Arduino). RW er til dæmis ekki þörf ef við erum aðeins að skrifa á skjáinn (sem er hvað oftast að gera) svo að við getum „bundið“ hann við jörðu. Það er líka leið til að tala við LCD með því að nota aðeins 4 gagnapinna í stað 8. Þetta sparar okkur 4 pinna! Af hverju myndi maður einhvern tíma vilja nota 8 þegar maður gæti notað 4? Við erum ekki 100% viss en við teljum að í sumum tilvikum sé það hraðvirkara að nota 8 - það tekur tvöfalt lengri tíma að nota 4 - og að hraðinn er mikilvægur. Hjá okkur er hraðinn ekki svo mikilvægur svo við munum spara nokkra pinna!
Svo til að safna saman þurfum við 6 pinna: RS, EN, D7, D6, D5 og D4 til að tala við LCD.

2. Breyttu kóðanum þannig að hann birtir nafnið þitt í línu 1 og settu dagsetningu í línu 2.
* __Svar:__ [sjá kóða](https://www.tinkercad.com/things/c0ELhpUSLRG-lcd-1932020/editel)


#### Aukaverkefni (valkvæmt).
* Skoðaðu eftirfarandi [LCD kóðasýnidæmi](https://github.com/GunnarThorunnarson/VESM2VT05BU/blob/master/PowerSupplyLearningKitforUNO/Lesson%209%20LCD1602/code/LCD1602/LCD1602.ino). Hvers vegna er talan 26 notuð í for lykkjunum?
* Hvers vegna að nota 8 data pinna (DO - D7) þegar hægt er að nota aðeins 4 data pinna? 
* [Arduino Lesson 12. LCD Displays - Part 2](https://learn.adafruit.com/adafruit-arduino-lesson-12-lcd-displays-part-2)


### 3.2 DC motor og Transistors (5%)
1. Kynntu þér eftirfarandi [Motors and Motion](https://www.instructables.com/lesson/Motors-and-Motion/)
og [Transistors](https://www.instructables.com/lesson/Transistors/) og svaraðu eftirfarandi spurningum:

   1. Hvernig er skrefmótor (e. stepper motor) ólíkur hefðbundnum DC mótor?
   * __Svar:__ DC mótorar snúast frjálsir þegar þeir eru knúnir af DC straumi. Þessir mótorar snúast frjálsir þegar þeir eru knúnir og hafa enga nákvæma staðsetningu. Þeir eru bestir sem vélfærafræði drifhjóla. Maður getur venjulega borið kennsl á DC mótor vegna þess að hann lítur út eins og kringlótt málmrör með skaft í miðju og tvö skaut að aftan. Þessir mótorar eru í fjölmörgum mismunandi stærðum og spennu.

Skrefmótorar hinsvegar eru með tvær eða fleiri aðskildar vafningar sem þarf að knýja í tiltekinni röð. Vegna þessa færist skaftið í litlum „þrepum“ um leið og aflið er hjólað á milli spóla. Þessir vélar eru góðar fyrir nákvæma staðsetningu og hraðastjórnun, sérstaklega þegar maður þarf mótor sem getur snúið 360 gráður snúning. Maður getur venjulega bent á skrefmótor vegna þess að hann er með lögun eins og kassa og/eða hefur 4 eða fleiri víra sem koma út úr hliðinni. Algengasta gerð skrefmótora er tvíhverfur mótor, sem hefur tvær vafninga, og fjóra víra (tvær fyrir hvern vír). Þetta eru venjulega tegundin sem maður mun mæta.
   2. Hvernig er stýrimótor (e. servo motor) ólíkur hefðbundnum DC mótor? 
   * __Svar:__ 
Stýrimótorar eru sérhæfðir DC-vélar með innbyggð stjórnborð sem þarfnast merkis frá örstýringu. Flestir servómótorar hafa takmarkaðan snúning og er hægt að beina þeim til að fara í mjög nákvæma staðsetningu. Hins vegar eru til stöðugar snúnings servó sem geta ekki fært sig í nákvæma staðsetningu, en hægt er að forrita með tilliti til hraða. Maður getur borið kennsl á servómótor vegna þess að hann er kassalíkur og hefur gírlíkan hlut festann við skaftið.
   3. Hvernig er hægt að stjórna í hvora áttina DC mótor snýst?  
   * __Svar:__ 
Til að knýja DC mótor þarf aðeins að tengja jákvæða spennu (innan aflmats) við eina tengi á mótornum og jörð við hina rafstöðina.
Til að snúa stefnu DC mótor með því að snúa einfaldlega vírunum sem eru tengd við hverja rafstöð. Ástæðan fyrir því að mótorinn snýst afturábak þegar maður gerir þetta er sú að segulpólarnir sem myndast innan vindanna snúast við þegar maður knýr hann öfugt. Þetta neyðir snúninginn til að snúast á gagnstæða leið til að samræma föstu segulana inni í sátinn (mótorhólfið).
   4. Hvað gerir transistor?
   * __Svar:__
   5. Hver er munurinn á NPN og PNP transistorum?
   * __Svar:__

1. Fylgdu [Lesson 13. DC Motors](https://learn.adafruit.com/adafruit-arduino-lesson-13-dc-motors) og settu hann upp í TinkerCad.

1. Svaraðu eftirfarandi spurningum:

   1. Afhverju þurfum við að nota PWM pinna til að stýra DC mótor?
   * __Svar:__
   2. Afhverju þurfum við að nota viðnám, transistor og diode með DC mótor í _Lesson 13. DC Motors_?
   * __Svar:__

1. Fylgdu [Lesson 13. DC Motors](https://learn.adafruit.com/adafruit-arduino-lesson-13-dc-motors) verklega með brauðbretti, DC motor og íhlutum.

### 3.3 DC motor og H-Bridge (5%)
(væntanlegt)

### Myndbönd fyrir verklegt Arduino
1. [Verkefni 3.1: LCD](https://www.youtube.com/watch?v=_nJolhGTI94&feature=youtu.be)
