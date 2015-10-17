# Matematicka logika a grafy #

materialy - http://tf.czu.cz/~horaj/

## Teorie grafu ##

neorientovany graf je trojice:

 * Mnozina vrcholu (V) - mesta

 * Mnozina hran (E) - cesty

 * Mnozina zobrazeni (P), ktere kazde hrane prirazuje jednoprvkovou ci dvouprvkovou mnozinu vrcholu

## Popis grafu ##

Je mozne pouzit formalni popis uzlu, hran a jejich zobrazeni, ale casto je lepsi pouzit **diagram**

## Zvlastni pripady grafu ##

 * DISKRETNI graf - nema hrany
 * UPLNY - kazde dva vrcholy jsou spojene hranou
 * PODGRAF - vsechny tri mnoziny jsou podmnoziny
 * ROVINNY GRAF - takovy graf, jehoz diagram lze zapsat tak, ze se neprotinaji hrany - napriklad vyleptat plosny obvod. K5 a K3,3
                  nejsou rovinne, proto, pokud ve svem grafu najdu K5 nebo K3,3 tak nemuze byt rovinny, muzes i zcelovat hrany (tj.
                  vymazat bod stupne 2.
 * SOUVISLY GRAF - takovy graf, kde mezi libovolnymi dvema vrcholy existuje cesta
 * EULEROVSKY GRAF - GRAF, ve kterem existuje tah, ktery projde vsechny vrcholy alespon jednou
 * HAMILTONOVSKY - graf ve kterem existuje kruznice, ktera obsahuje kazdy vrchol prave jednou (hamiltonovska kruznice)


## Izomorfismus ##

Pokud jsou dva grafy izomorfni, jsou vlastne stejne - maji stejny pocet hran, vrcholu a stejne skore.


**Stupen vrcholy** - pocet hran, ktere jsou spojeny s danym vrcholem
**Skore** grafu je posloupnost stupnu jednotlivych grafu - tim lze snadno odlisit grafy, ktere nejsou izomorfni.
Zjistovani izomorfismu grafu je algoritmicky hodne slozita zalezitost.
Ne kazda posloupnost ale muze byt skore grafu - napriklad skore musi mit sudy soucet - jinak by byla hrana jen s jednim vrcholem

## Jak nakreslit graf podle skore ##

 * Vezmu skore, zjednodusuji ho postupne umazavanim vrcholu s nejvyssim stupnem.
 * Pokud zjistim ze existuje, tak ho muzu odspoda nahoru zase snadno nakreslit

## Sled ##

Je to posloupnost vrcholu a hran - jako bych cestoval po grafu.
Specialnim pripadem je tah - tam nikdy nejedu po stejne hrane (je-li uzavreny, koncim ve stejnem vrcholu)
Specialnim pripadem tahu je **cesta** - neopakuji se ani vrcholy (uzavrenou cestu nazyvame **Kruznice**)

## Faktor grafu ##

Je to takovy podgraf, ktery obsahuje vsechny vrcholy puvodniho grafu

### Kostra grafu ###

Je takovy Faktor grafu, ktery, je zaroven stromem. 

## Problem obchodniho cestujiciho ##

Postup pomoci Dijkstrova algoritmu:
 1. Uvedomim si odkud jedu
 1. Vsechna ostatni mista zapisu pod sebe
 1. Do druheho sloupce zapisu kam se muzu dostat z vychoziho bodu, kolik km a odkud (tj. v prnim kroku z vychoziho bodu)
 1. Vezmu nejkratsi cestu a v druhem sloupci zase zapisu kolik to bude km a pres jake mesto.
 1. Pokracuji dokud se nedostanu do ciloveho mesta, tim vim i nejkratsi cestu a zpetne ji rekonstruuji

tj. - dulezite je si psat nejen hodnotu hrany, ale i jeji identifikaci (tj. ze ktereho mesta)

**BACHA, vysledek neni minimalni kostra, minimalni kostra se nehleda dijkstrovym algoritmem**

## Orientovany graf ##

 * Ke kazde rade je prirazena usporadana dvojice vrcholu (tj. cesta mezi uzly je jednosmerna).
 * Musime tu uz rozlisovat kolik hran do vrcholu prichazi a kolik odchazi.
 * s izomorfismem to uz take neni tak jednoduche

### Korenove stromy ###

 * Orientovany graf, ktery by byl strom, kdyby graf nebyl orientovany
 * Existuje tam koren, coz je vrchol, ze ktereho vede cesta do vsech ostatnich vrcholu
 * Mluvime tam o otcich a synech (resp. predchudcich a naslednicich)
 * Vrcholy, ktere uz nemaji zadne nasledniky nazyvame **Listy**

#### Binarni korenovy strom ####

 * korenovy strom, jehoz kazdy vrchol ma maximalne dva nasledniky

##### Notace pro zapis stromu #####

 * infixova: 5,-,3 - u tehle notace je take nutne pouzivat zavorky, u ostatnich ne.
 * prefixova: -,5,3
 * postfixova: 5,3,-

 * Pro pocitac je nejvyhodnejsi asi prefixova (rozhodne ne infixova, ta je zase human readable)
 * Jsou dva typy objektu - operace maji dva nasledniky a cisla (vcetne promennych), ktere nemaji zadne nasledniky
 * Kdyz sestavujes prefixovou, tak lze jit po nejlevejsich podstromech

### Site ###

Orientovany souvisly graf bez smycek a nasobnych hran, ktery ma nezaporne ohodnocene hrany
Jsou urceny dva vrcholy: zdroj a stok (spotrebic). Ohodnoceni hrany se nazyva kapacita.
Pouzije se napriklad pri popisu silnicni site.
Uplatnuje se **Kirchhoffuv zakon** - jako u proudu, kolik vleze, tolik musi vylezt.
Muzu to delat tak, ze udelam ruzne rezy tou siti, a zjistuji kolik mi proleze z jedne casti do druhe.
Minimalni rez - tedy rez s nejmensi kapacitou je vlastne hrdlo lahve. Metodu rezu vsak ma smysl pouzit
jen u malych siti.

Jak to resit jinak?
Vyberu jednu cestu a poslu po ni tolik, kolik snese, pak dalsi a zase kolik se tam jeste vejde - pak se
ale muze stat, ze jednu cestu pretizim - poslu po ni vic nez kolik je idealni a tak se mi ucpe pro jine,
efektivnejsi pouziti.
Tak abych nalezl optimalni reseni, muzu jakoby v protismeru posilat antiauta a dopocitavat - tj. u kazde
hrany si eviduji kolik kapacity zbyva a kolik jsem uz vyuzil.

## Obarveni ##

Obarveni je zobrazeni, ktere prirazuej vrcholum atribut (barvu), tak aby nebyly hranou spojeny vrcholy stejne barvy.

### Chromaticke cislo grafu ###

Je kolik barev musim pouzit.
Tj. jedna barva pro diskretni graf. Tolik barev kolik vrcholy pro uplny graf.
Kazdy roviny graf ma chromaticke cislo maximalne 4 - obarveni mapy statu, staci max 4 barvy.
