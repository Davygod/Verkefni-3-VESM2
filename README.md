# Verkefni-3-VESM2
 ### 3.1 LCD (5%)
Fylgdu eftirfarandi tutorial verklega [Character LCDs](https://learn.adafruit.com/character-lcds/overview) að Python & CircuitPython. Kynntu þér vel kóðann og hvað pinnarnir gera.
**Ath.** LCD með kóðanum er einnig á TinkerCad.

1. Svaraðu eftirfarandi spurningum:

   1. Hver er helsti munurinn á Character LCDs og Graphical LCDs?
   * Svar: Persónu-LCD skjár er tilvalinn til að birta texta. Einnig er hægt að stilla þau til að sýna lítil tákn en táknin verða að vera aðeins 5x7 pixlar eða svo (mjög lítil!)
   Myndræna LCD-skjárinn er með eitt stórt pixlanet (í þessu tilfelli 128x64 þeirra) - Hann getur birt texta en bestur til að sýna myndir. Grafískar LCD skjáir hafa tilhneigingu til að vera stærri, dýrari, erfiðar í notkun og þurfa marga fleiri pinna vegna flækjunnar sem bætt er við.
   2. Hvað gerir RS pinninn á LCD?
   * Svar: RS-pinninn lætur örstýringuna segja LCD-skjánum hvort hann vilji sýna þessi gögn (eins og í ASCII staf) eða hvort það sé skipanabæti (eins og að breyta stöðu bendilsins).
   3. Afhverju þarf að tengja RW-pinnann í jörð ef við erum ekki að nota hann?
   * Svar: Vegna áhyggna af því að skrifa stafi á LCD-skjáinn.
   4. Hvað er hægt að birta marga stafi í LCD1602?
   * Svar: 32 stafi alls (16 í línu)
   5. Afverju þarf að stýra LCD1602 með nokkrum pinnum (4 eða 8) á sama tíma? útskýrðu!
   * Svar: D0-D7 eru pinnar sem eru með hráu gögnin (raw data) sem við sendum á skjáinn. RS-pinninn lætur örstýringuna segja LCD-skjánum hvort hann vilji sýna þessi gögn (eins og í ASCII staf) eða hvort það sé skipanabæti (eins og að breyta stöðu bendilsins). *EN*-pinninn er „virka“ línan sem við notum til að segja LCD skjánum þegar gögn eru tilbúin til aflestrar. RW-pinninn er notaður til að stilla stefnuna - hvort sem við viljum skrifa á skjáinn (algeng) eða lesa úr honum (sjaldgæfari)
   Góðu fréttirnar eru þær að ekki eru allir þessir pinnar nauðsynlegir fyrir okkur til að tengjast örstýringunni (Arduino). RW er til dæmis ekki þörf ef við erum aðeins að skrifa á skjáinn (sem er hvað oftast að gera) svo að við getum „bundið“ hann við jörðu. Það er líka leið til að tala við LCD með því að nota aðeins 4 gagnapinna í stað 8. Þetta sparar okkur 4 pinna! Af hverju myndi maður einhvern tíma vilja nota 8 þegar maður gæti notað 4? Við erum ekki 100% viss en við teljum að í sumum tilvikum sé það hraðvirkara að nota 8 - það tekur tvöfalt lengri tíma að nota 4 - og að hraðinn er mikilvægur. Hjá okkur er hraðinn ekki svo mikilvægur svo við munum spara nokkra pinna!
Svo til að safna saman þurfum við 6 pinna: RS, EN, D7, D6, D5 og D4 til að tala við LCD.

2. Breyttu kóðanum þannig að hann birtir nafnið þitt í línu 1 og settu dagsetningu í línu 2.
* Svar: [sjá kóða](https://www.tinkercad.com/things/c0ELhpUSLRG-lcd-1932020/editel)


#### Aukaverkefni (valkvæmt).
* Skoðaðu eftirfarandi [LCD kóðasýnidæmi](https://github.com/GunnarThorunnarson/VESM2VT05BU/blob/master/PowerSupplyLearningKitforUNO/Lesson%209%20LCD1602/code/LCD1602/LCD1602.ino). Hvers vegna er talan 26 notuð í for lykkjunum?
* Hvers vegna að nota 8 data pinna (DO - D7) þegar hægt er að nota aðeins 4 data pinna? 
* [Arduino Lesson 12. LCD Displays - Part 2](https://learn.adafruit.com/adafruit-arduino-lesson-12-lcd-displays-part-2)


### 3.2 DC motor og Transistors (5%)
(væntanlegt)

### 3.3 DC motor og H-Bridge (5%)
(væntanlegt)
