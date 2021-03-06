# Verkefni-3-VESM2
 ### 3.1 LCD (5%)
Fylgdu eftirfarandi tutorial verklega [Character LCDs](https://learn.adafruit.com/character-lcds/overview) að Python & CircuitPython. Kynntu þér vel kóðann og hvað pinnarnir gera.
**Ath.** LCD með kóðanum er einnig á TinkerCad.
   * [Svar: Verklegt 3.1: LCD](https://www.youtube.com/watch?v=_nJolhGTI94&feature=youtu.be)

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

1. Breyttu kóðanum þannig að hann birtir nafnið þitt í línu 1 og settu dagsetningu í línu 2.
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
      * __Svar:__ Stýrimótorar eru sérhæfðir DC-vélar með innbyggð stjórnborð sem þarfnast merkis frá örstýringu. Flestir servómótorar hafa takmarkaðan snúning og er hægt að beina þeim til að fara í mjög nákvæma staðsetningu. Hins vegar eru til stöðugar snúnings servó sem geta ekki fært sig í nákvæma staðsetningu, en hægt er að forrita með tilliti til hraða. Maður getur borið kennsl á servómótor vegna þess að hann er kassalíkur og hefur gírlíkan hlut festann við skaftið.
   3. Hvernig er hægt að stjórna í hvora áttina DC-mótor snýst?  
      * __Svar:__ Til að knýja DC mótor þarf aðeins að tengja jákvæða spennu (innan aflmats) við eina tengi á mótornum og jörð við hina rafstöðina.
Til að snúa stefnu DC mótor með því að snúa einfaldlega vírunum sem eru tengd við hverja rafstöð. Ástæðan fyrir því að mótorinn snýst afturábak þegar maður gerir þetta er sú að segulpólarnir sem myndast innan vindanna snúast við þegar maður knýr hann öfugt. Þetta neyðir snúninginn til að snúast á gagnstæða leið til að samræma föstu segulana inni í sátinn (mótorhólfið).
   4. Hvað gerir smári (transistor)?
      * __Svar:__ Smári er rafrænn hluti sem tekur lítið magn af straumi og magnar það.
   5. Hver er munurinn á NPN- og PNP-smárum?
      * __Svar:__ Til að skilja betur muninn á þessu tvennu, skulum við skoða díóða um stund. Eins og díóða, eru smárar gerðir upp af stillingum PN-mótum.
Maður gæti sagt með tilgátu að NPN-smári sé í grundvallaratriðum 2 díóða bak við bak. Í fræðilegum heimi hefðir maður rétt fyrir sér, en í hinum raunverulega heimi maður alls ekki sagt það. Munurinn er sá að ekki aðeins eru P-svæðin í díóða töluvert stærri, þau eru heldur ekki beinlínis tengd. Hvert P-svæði er í raun að vera tengt við vírleiðslu, sem aftur hegðar sér hvorki eins og P-svæði eða N-svæðið að því er rafeindir eru taldar. Þessi sýning er líkari NP-WIRE-PN mótum. Þetta er greinilega alls ekki það sama. Hins vegar er mikilvægt að hafa í huga þessa hugmynd um PN-hlutdrægni.
Ólíkt díóða, hefur NPN-smári mjög þunnt P-svæði - ekki breiðara en nokkrar bylgjulengdir ljóss - samloka milli tveggja N-svæða. Þegar straumur er beittur á P-svæðið (tengdur við grunnpinnann), þá skakar hann grunn- og safnapinnana áfram, og dregur í raun úrrennslissvæðið báðum megin við P-svæðið miðað við strauminn sem beittur er.
Þetta framskekkjufyrirkomulag milli grunnsins og sendisins gerir það að verkum að rafeindir streyma frá grunnpinnanum til N-svæðisins sem er tengdur við sendinn (eins og díóða). Að því gefnu að rafmagnsmerkið við safnarann sé einnig jákvæðara en það sem gefur frá sér, þá geta rafeindirnar á safnaranum farið ókeypis í gegnum virka P-svæðið til sendisins. Sagt á annan hátt, straumurinn sem liggur frá grunninum til sendisins virkar eins og Trójuhestur til að virkja P-svæðið og leyfa mun stærri straumnum sem hangir við safnarann að fara um P-svæðið til sendisins.
Þegar lítill rafstraumur er beittur við grunnpinnann, magnar hann hann þannig að mun stærri straumur getur farið milli safnara og emitterpinna. Magn straums sem liggur milli safnara og emitter pinna er í réttu hlutfalli við strauminn sem er lagður á grunnpinnann.
PNP-smári aftur á móti virkar gagnstætt við NPN-smára. Hann hefur tvö P-svæði og mjög lítið N-svæði í miðjunni. Vegna þessa er öfugsnúið hlutskipti milli grunnsins og sendisins. Þegar straumur er beittur virkar þessi gagnstæða hlutdrægni eins og díóða og hindrar rafmagn í að renna. Það er aðeins þegar straumurinn byrjar að fjarlægja úr grunninum að rafeindir geta farið frjálslega milli safnara og sendanda.

1. Fylgdu [Lesson 13. DC Motors](https://learn.adafruit.com/adafruit-arduino-lesson-13-dc-motors) og settu hann upp í TinkerCad.
   * [Sjá kóða)](https://www.tinkercad.com/things/0oKAyk09PC4-exquisite-jaban/editel?tenant=circuits)

1. Svaraðu eftirfarandi spurningum:

   1. Afhverju þurfum við að nota PWM (pulse-width-modulation) pinna til að stýra DC mótor?
      * __Svar:__ Breyting púlsbreiddar er frábær aðferð til að stjórna magni sem afhentur er álagi án þess að dreifa orku. Ofangreindan hringrás er einnig hægt að nota til að stjórna hraða viftu eða til að dimma birtustig DC lampa eða LED.
   2. Afhverju þurfum við að nota viðnám, smára og díóða með DC mótor í _Lesson 13. DC Motors_?
      * __Svar:__ Litli DC mótorinn mun líklega nota meira afl en Arduino stafræna framleiðslan ræður beint við. Ef reynt er að tengja mótorinn beint við Arduino pinna eru góðar líkur á að það gæti skemmt Arduinoið.

           Hægt er að nota lítinn smára eins og PN2222 sem rofa sem notar aðeins lítinn straum frá Arduino stafræna framleiðslunni til að stjórna miklu stærri straumi mótorsins.
        Í smára eru þrjár leiðir. Mest af rafmagni rennur frá safnara til sendisins en það mun aðeins gerast ef lítið magn streymir inn í grunntenginguna. Þessi litli straumur fæst með stafræna framleiðslunni frá Arduino.

        Pinninn D3 í Arduino er tengdur við viðnáminn. Rétt eins og þegar ljósdíóða er notuð takmarkar þetta strauminn sem flæðir í smáranum gegnum grunninn.

        Það er díóði tengdur yfir tengingar mótorsins. Díóðinn leyfir aðeins rafmagni að flæða í eina átt (stefnu örvarinnar).

        Þegar maður slekkur á vélinni fær maður neikvæða spennu sem getur skemmt Arduinoið eða smárann. Díóðinn verndar gegn þessu með því að stytta slíka afturstraum frá mótornum.

1. Fylgdu [Lesson 13. DC Motors](https://learn.adafruit.com/adafruit-arduino-lesson-13-dc-motors) verklega með brauðbretti, DC motor og íhlutum.
   * Svar: [Verklegt 3.2: DC-mótor og smári](https://www.youtube.com/watch?v=-DsBnNlEvLk&feature=youtu.be)

### 3.3 DC motor og H-Bridge (5%)
1. Fylgdu [Lesson 15. DC Motor Reversing](https://learn.adafruit.com/adafruit-arduino-lesson-15-dc-motor-reversing) og settu hann upp í:
   1. TinkerCad
      * [Svar](https://www.tinkercad.com/things/9TAx5MRI04h-amazing-stantia-wluff/editel?tenant=circuits)
   1. Verklega
      * [Svar](https://www.youtube.com/watch?v=HYimzUp3YGY&feature=youtu.be)
  
1. Lestu þér til um [L293D H-Bridge](https://maker.pro/custom/projects/all-you-need-to-know-about-l293d) og svaraðu eftirfarandi spurningum:

   1. Hvað er hægt að gera með L293D?
      * __Svar:__ L293D er einn af vinsælustu driverum á markaðnum. Það eru nokkrar ástæður sem gera L293D að ákjósanlegum driver fyrir notendur, svo sem, ódýr verð (miðað við aðra drivera), rétta lögun og stærð, auðveld stjórnun, engin þörf á hlífðarrás og díóða, engin þörf á hitaskipum og góð viðnám að hitastigi og háhraða breytileika. Þessi IC getur sett upp mótora með spennu á milli 5V til 36V og straumi allt að 600 mA. Hins vegar þolir það allt að 1200 mA straum í 100 míkrósekúndu og er ekki endurtekið. Tíðni þessa IC er 5 kHz. Ef mótor þinn samsvarar þessum forskriftum skaltu ekki hika við að nota L293D.
        L293 og L293D tækin eru fjórfaldur hástraumur hálfur H ökumaður. L293 er hannaður til að veita tvískipta drifstrauma allt að 1 A við spennu frá 4,5 V til 36 V. L293D er hannaður til að veita tvíákeyrslustraum sem er allt að 600 mA við spennu frá 4,5 V til 36 V. Bæði tækin eru hannað til að knýja framleiðsluhleðslu eins og gengi, segulloka, DC og tvískauta stigmótora, auk annarra hástraums / háspennuálags í jákvæðum framboðsaðgerðum.

        Hver framleiðsla er heill drifrás með totem-stöng, með Darlington smári vaski og gervi-Darlington uppspretta. Ökumenn eru virkir í pari, með ökumenn 1 og 2 virkjaðir af 1,2EN og ökumenn 3 og 4 virkjaðir af 3,4EN. L293 og L293D einkennast fyrir notkun frá 0 ° C til 70 ° C.

        Aðrir mikilvægir eiginleikar L293D eru:

          * Breitt framboðsspennusvið: 4,5 V til 36 V
          * Aðskilið inntak-rökfræði framboð
          * Innri ESD vernd
          * High-Noise-Immunity input
          * Útgangsstraumur 1 A á rás (600 mA fyrir L293D)
          * Hámarksafgangsstraumur 2 A á rás (1,2 A fyrir L293D)
          * Úttak klemmudíóða fyrir hvatvís skammvinn kúgun (L293D)
   1. Hver er munurinn á L293 or L293D?
      * __Svar:__ Stafur 'D' í nafni gefur til kynna innbyggða díóða og það þýðir að við þurfum ekki að bæta við neinum ytri íhlutum. Þetta er aðalmunurinn.
   1. Í lesson 15 er eftirfarandi kóðabútur, útskýrðu hann útfrá H-Bridge
   ```
   void setMotor(int speed, boolean reverse)
   {
     analogWrite(enablePin, speed);
     digitalWrite(in1Pin, ! reverse);
     digitalWrite(in2Pin, reverse);
   }
   ```
      * __Svar:__ Hraðinn er stilltur með því að nota analogWrite til að kveikja á pinna. Kveikjupinni L293 kveikir og slekkur bara á mótornum, óháð því hvað in1 og in2 pinnar L293 eru stilltir á.
      Til að stjórna stefnu mótorsins verður að stilla pinna in1 og in2 á gagnstætt gildi. 
      Ef in1 er HIGH og in2 er LOW, mun mótorinn snúast á einn veg, ef á hinn bóginn er in1 LOW og in2 HIGH, þá mun mótorinn snúast í gagnstæða átt.
      '!' skipun þýðir 'ekki'. Þannig að fyrsta digitalWrite skipunin fyrir in1 setur það á hið gagnstæða af öllu því sem gildi 'öfugt' er, þannig að ef öfugt er HIGH þá setur það það á LOW og öfugt.
      Önnur digitalWrite fyrir 'in2' stillir pinnann á það sem gildi 'reversed' er. Þetta þýðir að það verður alltaf öfugt við hvað sem er in1.
   1. L293D er með tvo +V pinna (8 and 16), útskýrðu þá.
      * __Svar:__ Pinninn +Vmotor (8) veitir afl fyrir mótorana og +V (16) fyrir rökfræði flísarinnar. Við höfum tengt þetta báða við Arduino 5V pinnann. Hins vegar, ef þú myndir nota öflugri mótor, eða hærri spennu mótor, myndirðu útvega mótorinn sérstakt aflgjafa með því að nota pinna 8 sem er tengdur við jákvæða aflgjafa og jörð seinni aflgjafans er tengd jörðu Arduino.
  
1. Lestu þér til um [mismunandi tegundir mótora](https://learn.adafruit.com/adafruit-motor-selection-guide/types-of-motors) og horfðu á þessi [tvö myndbönd](https://www.youtube.com/playlist?list=PLRIGIzu0Z7KlYY6FyZ0_Y0ZmVFyAvtDO0). <br> og nefndu í hvaða tilfellum (komdu með dæmi) eftirfarandi mótorgerðir væru notaðar og afhverju:

      1. Brushed DC Motor.
         * Notkun:
            * Leikföng
            * Cell Buzzers
            * Þráðlaus verkfæri
            * RC Servos
            * Gírhreyflar
          * Kostir:
            * Ódýrt
            * Léttur
            * Sanngjarnt skilvirkt
            * Gott lághraða togi
          * Takmarkanir:
            * Hávaði - Til viðbótar við heyranlegt væla frá kommutatorburstunum skapa þessir vélar mikinn rafmagnshljóð sem getur fundið leið aftur í aðrar rafrásir og valdið vandamálum.
      1. Brushless DC Motor.
         * Notkun:
            * Fjölnota
            * Drónar
            * Útvarpstæki
            * Diskadrifar
            * Viftur
            * Industrial Servos
            * Hybrid drivers
            * High-End Gearmotors
         * Kostir:
            * Rólegur
            * Skilvirkur
         * Takmarkanir:
            * Stjórnandi - Sumar tegundir burstalausra véla þurfa sérstakan stjórnara til notkunar.
      1. Stepper motor.
         * Notkun:
            * 3D prentarar
            * CNC vélar
            * Myndavél rigs
            * Vélmenni
            * Prentarar
            * Nákvæmni gírhreyflar
         * Kostir:
            * Nákvæm, endurtekin staðsetning
            * Nákvæm hraðastjórnun
            * Framúrskarandi lághraða togi
            * Frábært "halda togi" til að viðhalda stöðu
         * Takmarkanir:
            * Lítil skilvirkni
            * Getur þurft að umrita í dulmál eða takmarkanir til að koma upp viðmiðunarstöðu
            * Með fyrirvara um skref sem misst var af ef of mikið er lagt af
