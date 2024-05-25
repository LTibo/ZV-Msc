# Tételek (Msc, 2024 június)

## Áfonya

Jelölések:

- M: automata

- L(M): nyelv, amit az automata fejez ki

- Σ<sup>∗</sup>: összes megkonstruálható szó

- M= (Q, Σ, δ, q<sub>0</sub>, F)
  
  - Q: automata állapothalmaza
  
  - Σ: input ABC
  
  - δ: átmenetek halmaza
  
  - q<sub>0</sub>: kezdő állapot
  
  - F: végállapotok halmaza

- 1. **Felismerhető Nyelv**: Egy nyelv felismerhetőnek tekinthető, ha létezik olyan véges automata (DFA vagy NFA), amely pontosan azokat a szavakat fogadja el, amelyek a nyelv részét képezik. Ebben az esetben L a nyelv, amelyet az M automata felismer.
  
  2. **Összefüggő Automata**: Egy automata összefüggő, ha minden állapota elérhető a kezdőállapotból (q<sub>0</sub>​) valamely bemeneti szó hatására, amely a Σ<sup>∗</sup>-ból származik. Ez biztosítja, hogy az automata minden része hasznosul a nyelv felismerésében.
  
  3. **Homomorf Kép**: Egy M′ automata M homomorf képe, ha létezik egy homomorfizmus (azaz egy állapot-leképező függvény) ϕ az M automata és M′ között, amely a tranzíciók és az elfogadó állapotok között is megfelelő kapcsolatot tart fenn. A homomorfizmus garantálja, hogy ha M egy szót elfogad, akkor M′ is elfogadja azt, és fordítva, tehát L(M)=L(M′).
  
  ![](assets/2024-05-11-17-34-10-image.png)
  ![](assets/2024-05-11-17-34-34-image.png)
  ![](assets/2024-05-12-10-12-34-image.png)
  ![](assets/2024-05-12-10-22-35-image.png)
  ![](assets/2024-05-12-10-36-07-image.png)
  ![](assets/2024-05-12-10-38-23-image.png)
  ![](assets/2024-05-12-11-09-16-image.png)
  
  A képen az M<sub>L</sub>​ automata leírása látható, amely egy speciális típusú automata, amelyet egy adott nyelv, L, felismerésére használnak. Az M<sub>L</sub>​ automata a következő részekből áll:
  
  - **Állapotok:** Az állapotok halmaza Σ∗/ρ<sub>L</sub>​ a Σ<sup>∗</sup> karakterláncokon értelmezett ρL​ reláció szerinti osztályokból áll. Itt ρ<sub>L​</sub> a nyelv L szintaktikus jobbkongruenciája, amely egy olyan ekvivalencia reláció, amely szerint két sztring ekvivalens, ha bármely szó hozzáfűzésével a nyelvben maradnak vagy együtt kilépnek belőle.
  
  - **Ábécé:** Σ, amely az automata által felismert szimbólumok halmazát jelenti.
  
  - **Átmenetifüggvény:** δL​, amely meghatározza az állapotátmeneteket. A függvény egy adott állapotból (ami egy ekvivalenciaosztály) és egy karakterből kiindulva meghatározza a következő állapotot (szintén egy osztály). A definíció szerint δL​(x/ρL​,a)=xa/ρL​, tehát ha x egy osztályt képvisel, és a egy karakter, akkor az xa konkatenációjának osztálya adja a következő állapotot.
  
  - **Kezdőállapot:** ϵ/ρL​, ami az üres sztring osztálya.
  
  - **Elfogadó állapotok:** L/ρL​, amelyek azokat az osztályokat tartalmazzák, amelyek olyan sztringekből állnak, amelyek elemei a L nyelvnek.
  
  További fontos jellemzők:
  
  - **Véges indexű:** Σ∗/ρL​ véges, ami azt jelenti, hogy véges számú ekvivalenciaosztály van, így az automata állapotainak száma is véges.
  
  - **Szaturálja L-et:** A ρL​ reláció szaturálja az L nyelvet, ami azt jelenti, hogy az L nyelv pontosan azokból a szavakból áll, amelyeket az ML​ automata elfogad. Ezért ρL​ teljes mértékben kompatibilis L-lel, tehát L pontosan az ML​ által elfogadott szavak halmaza.

- **Monoid**:
  
  - Az algebra egyik alapvető struktúráját jelöli, amely magában foglal egy halmazt és egy, a halmazon értelmezett asszociatív bináris műveletet. Ezenkívül a monoidnak rendelkeznie kell egy olyan egységelemmel, amely a művelet szempontjából neutrális, vagyis amikor bármely elemmel kombinálják a művelet során, az eredeti elemet adja vissza. Tehát egy monoidot a következő tulajdonságok definiálják:
    
    1. **Halmaz**: Legyen M egy nem üres halmaz.
    2. **Bináris Művelet**: Legyen ⋅ egy bináris művelet M halmazon, tehát ⋅:M×M→M. Ez a művelet minden a,b∈M esetén meghatározza a⋅b-t, ami szintén M-ben van.
    3. **Asszociativitás**: A művelet asszociatív, ami azt jelenti, hogy minden a,b,c∈M esetén teljesül az (a⋅b)⋅c=a⋅(b⋅c) egyenlőség.
    4. **Egységelem**: Létezik egy e∈M elem (nevezik egységelemnek vagy neutrális elemnek), amelyre minden a∈M esetén teljesül, hogy e⋅a=a⋅e=a.
    
    ### Példák Monoidokra
    
    - **Számok összeadása**: A természetes számok (N) halmaza az összeadás műveletével monoidot alkot, ahol az egységelem az 0, mert 0+a=a+0=a minden a∈N esetén.
    - **Számok szorzása**: A pozitív egész számok (N+) szorzása szintén monoid, az egységelem itt az 1, mivel 1⋅a=a⋅1=a minden a∈N+ esetén.
    - **Sztringek konkatenációja**: A sztringek halmaza (például az ASCII karakterekből álló sztringek) a konkatenáció műveletével monoidot alkot, ahol az egységelem az üres sztring (""), mert bármely sztring konkatenálása az üres sztringgel önmagát adja eredményül.

### 

# 1. Automaták minimalizálása

Egy M automatát minimálisnak nevezünk, ha bármely vele ekvivalens M ′ automata esetén M -nek legfeljebb annyi állapota van, mint M ′-nek.

**<u>Minimális automata egyértelműségének bizonyítása</u>**

1. **Automata Definíciója és δ∗ Jelölés**:
   
   - M=(Q, Σ, δ, q<sub>0</sub>​, F) egy véges automata.
   - δ<sup>∗</sup>(q,x)=qxM​ azt az állapotot jelöli, amelybe az M automata a q állapotból az x szó (bemeneti sztring) hatására kerül. Ez kiterjeszti a δ tranzíciós függvényt, hogy szavakat (nem csak szimbólumokat) is kezeljen.

2. **Összefüggő Automata**:
   
   - Az M′ automata, amely M összefüggő része, a következőkből áll: 
     M′=(Q′,Σ,δ′,q<sub>0</sub>​,F′).
   - Q′={q<sub>0</sub>​x ∣ x∈Σ<sup>∗</sup>} az összes olyan állapot, amit a kezdőállapotból elérhetünk, bármilyen Σ<sup>∗</sup>-beli szóval.
   - δ′ az M tranzíciós függvényének megszorítása az Q′-beli állapotokra.
   - F′=F∩Q′ az elfogadó állapotok az M′ automata számára.
   - Ha M összefüggő, az azt jelenti, hogy az M automata minden állapota elérhető a kezdőállapotból.

3. **Homomorfizmus és Izomorfizmus**:
   
   - Két automata közötti leképezést ϕ: Q → Q′ homomorfizmusnak nevezzük, ha teljesülnek a következő feltételek:
     1. ∀q ∈ Q, a ∈ Σ: ϕ(δ(q, a)) = δ′(ϕ(q), a), ami azt jelenti, hogy ϕ "megőrzi" a tranzíciós viselkedést.
        ![](assets/2024-05-10-23-36-08-image.png)
        Ha az M automata q állapotából a a szimbólum hatására egy új állapotba (δ(q,a)) lép, és ezt az állapotot leképezzük a ϕ függvénnyel, akkor az eredményül kapott állapotnak meg kell egyeznie azzal az állapottal, amibe az M′ automata az M automata q állapotának képe (ϕ(q)) és az a szimbólum alkalmazása után lép.
     2. ϕ(q<sub>0​</sub>)=q<sub>0</sub>′​, azaz a kezdőállapotok megfelelnek egymásnak.
     3. ϕ<sup>−1</sup>(F′)=F, az elfogadó állapotok megőrzése.
        ![](assets/2024-05-10-23-34-45-image.png)
   - Ha ϕ ráképezés, akkor azt mondjuk, hogy M ′ az M homomorf képe. Ha ϕ bijekció, akkor izomorfizmusnak hívjuk és azt mondjuk, hogy M és M′ izomorfak, jele M ∼= M ′
   - Bizonyítható, hogy ha ϕ homomorfizmus, akkor az (1) tulajdon-
     ság nemcsak egy a ∈ Σ input szimbólumra, hanem tetszőleges x ∈ Σ∗ szóra is teljesül: minden q ∈ Q állapot esetén ϕ(δ∗(q, x)) = δ′∗(ϕ(q), x).
- **Lemma**: Legyenek M = (Q, Σ, δ, q<sub>0</sub>, F ) és M′=(Q′, Σ, δ′, q′<sub>0</sub>, F ′) automaták. Ha van homomorfizmus M -ből M ′-be, akkor L(M ) = L(M ′).
  
  - A lemma kijelentése szerint ha van egy L⊆Σ<sup>∗</sup> felismerhető nyelv, és egy 
    M=(Q,Σ,δ,q<sub>0</sub>​,F) összefüggő automata, amely ezt a nyelvet felismeri, akkor létezik egy M′ automata, amely M homomorf képe, és ez az M′ is felismeri L-t.

- Legyen L ⊆ Σ∗ egy tetszőleges felismerhető nyelv és tekintsük az
  ML = (Σ<sup>∗</sup>/ρ<sub>L</sub>, Σ, δ<sub>L</sub>, ε/ρ<sub>L</sub>, L/ρ<sub>L</sub>) automatát, ahol ρ<sub>L</sub> az L szintaktikus jobbkongruenciája és minden x ∈ Σ∗ esetén δL(x/ρ<sub>L</sub>, a) = xa/ρ<sub>L</sub>.
  
  - **Lemma:** M = (Q, Σ, δ, q<sub>0</sub>, F ) pedig tetszőleges összefüggő automata, amelyik L-et ismeri fel. Akkor M<sub>L</sub> az M homomorf képe.

**Tétel**. Legyen L ⊆ Σ<sup>∗</sup> egy felismerhető nyelv. Akkor

1) M<sub>L</sub> az L-et felismerő minimális állapotszámú automata.
2) Az L-et felismerő minimális automata izomorfizmus erejéig egyértelműen meghatá-
   rozott.

**Következmény**. Legyen L ⊆ Σ<sup>∗</sup> egy felismerhető nyelv és legyen K<sub>L</sub> = {M |
M automata és L(M ) = L}. Egy M<sub>0</sub> automata akkor és csak akkor minimális K<sub>L</sub>-ben,
ha minden K<sub>L</sub>-beli automata összefüggő részének homomorf képe.

#### A minimális állapotszámú automata algoritmikus meghatározása

##### Kongruencia Definíciója Automatákon

- **Kongruencia (ρ):** Egy reláció, ami biztosítja, hogy ha két állapot (p és q) között fennáll a reláció, akkor minden bemeneti szimbólum (a ∈ Σ) esetén az állapotokból kiinduló átmenetek eredménye is ezen relációban áll. Emellett a kongruencia azt is megköveteli, hogy ha két állapot ekvivalens, akkor vagy mindkettő elfogadó állapot, vagy egyik sem az.

- **Faktorautomata (M/ρ):** Az eredeti automata (M) egy olyan változata, amely az ekvivalenciaosztályokat egyesítve kezeli az állapotokat. Az új automata állapotai az eredeti állapotok ekvivalenciaosztályai, az átmenetifüggvényt és az elfogadó állapotokat az ekvivalenciaosztályoknak megfelelően definiálják újra.

##### Kongruencia Alapú Minimalizálás

A minimalizálás folyamata arra épül, hogy az eredeti automata (M) egy megfelelő kongruenciája alapján készítik el a faktorautomatát (M/ρ). Ezáltal az eredeti nyelvet felismerő, de kevesebb állapotú automata jön létre.

##### Homomorfizmus és Kongruencia

- **Homomorfizmus Tétel (Lemma 2.20):** Ha ρ egy kongruenciareláció az M automata felett, akkor az M/ρ faktorautomata homomorf képe az M automatának, ami azt jelenti, hogy struktúrájában és működésében megegyezik az eredetivel, de egyszerűsített formában.
- **Fordított Állítás:** Ha egy M' automata az M automata homomorf képe, akkor létezik egy olyan ρ kongruencia az M-en, amelyre M/ρ izomorf M'-vel.

##### ρM Kongruencia

- **Definíció (2.22):** Egy kongruencia a Q állapothalmazon, amelyet úgy határozunk meg, hogy két állapot ekvivalens, ha minden lehetséges bemeneti szóra ugyanazokat az elfogadó vagy nem elfogadó állapotokba vezető átmeneteket produkálják.
- **Ekvivalencia más megközelítésből:** Meghatározható úgy is, hogy két állapot ekvivalens, ha azokból kiindulva azonos nyelvet ismernek fel.

##### Minimális Automata

- **Tétel (2.24):** Ha az L nyelvet felismerő M automata összefüggő (azaz minden állapot elérhető a kezdőállapottól), akkor az M/ρM faktorautomata az L nyelvet felismerő minimális állapotszámú automata. Ez az automata a lehető legkisebb számú állapottal képes felismerni az L nyelvet.

#### Algoritmus (egyszerűen leírva)

##### 1. Kezdeti felosztás

Először felosztjuk az automatát két állapotcsoportra: az elfogadó állapotokra és a nem elfogadó állapotokra. Ez a kezdeti felosztás kialakítja az algoritmus alapját.

##### 2. Finomítás

Ezt követően a felosztást finomítjuk. Ha bármely szimbólumra két állapot különböző csoportokba vezet, azokat külön csoportokba soroljuk. Ez a lépés addig ismétlődik, amíg a felosztás stabil nem lesz, azaz további finomítás már nem lehetséges.

##### 3. Átmenetifüggvény újradefiniálása

Az újonnan létrehozott állapotcsoportok alapján újra kell definiálni az átmenetifüggvényt, amely az eredeti automata átmeneteit tükrözi, de már az új, minimalizált állapothalmazon.

##### 4. Az új automatának tesztelése

Az algoritmus végén az új, minimalizált automata tesztelése történik meg, hogy megbizonyosodjunk arról, hogy azonos nyelvet ismer fel, mint az eredeti automata.

Példa: [Minimization of DFA (Example 2) - YouTube](https://www.youtube.com/watch?v=ex9sPLq5CRg&ab_channel=NesoAcademy)

#### Algoritmus

![](assets/2024-05-12-16-35-04-image.png)

##### Bemenet

- **M = (Q, Σ, δ, q0, F)**: Egy determinisztikus véges automata, ahol:
  - **Q** az állapotok halmaza,
  - **Σ** az ábécé (bemeneti szimbólumok halmaza),
  - **δ** az átmenetifüggvény,
  - **q0** a kezdőállapot,
  - **F** az elfogadó állapotok halmaza.

##### Kimenet

- **ρ<sub>M</sub>**: A Q állapothalmaz feletti kongruenciareláció, amely az állapotok olyan csoportosítását adja meg, amelyek közötti átmenetek és elfogadó tulajdonságok azonosak maradnak.

##### Lépések

1. **Inicializáció (ρ<sub>0</sub>):** Kezdetben a ρ<sub>0</sub> relációt úgy állítjuk be, hogy két állapot, p és q, akkor van ρ0 relációban, ha mindkettő elfogadó vagy mindkettő nem elfogadó. Ez alapvetően a végső állapotok szerinti elsődleges csoportosítást jelenti.

2. **Iteratív Finomítás (ρ<sub>i</sub>+1):** Ezt követően iteratív lépésekben finomítjuk a relációt:
   
   - Minden iterációban (ρ<sub>i</sub>+1-nek meghatározása) a p és q állapotok közötti kapcsolatot úgy vizsgáljuk, hogy p és q az előző iterációban, ρ<sub>i</sub>-ben ekvivalensek voltak, és minden lehetséges bemeneti szimbólumra, a ∈ Σ-ra, a δ(p, a) és δ(q, a) által elért állapotok is ρi relációban állnak.

3. **Konvergencia Vizsgálata:** Az algoritmus akkor áll le, amikor a ρi reláció nem változik tovább, azaz ρ<sub>i</sub> = ρ<sub>i</sub>+1. Ez azt jelenti, hogy további finomítás már nem lehetséges, és a reláció stabilizálódott.

##### Terminálás és Korrektség

- **Terminálás:** Az algoritmus mindig megáll, mivel a relációk száma véges, és minden iterációban a reláció szigorodik vagy változatlan marad.
- **Korrektség:** A Lemma 2.26 biztosítja, hogy az algoritmus a megfelelő ρ<sub>M</sub> relációt számolja ki, azaz megtalálja azon állapotekvivalenciákat, amelyek fenntartása mellett az automata ugyanazt a nyelvet ismeri fel.

## 2. Parikh tétele és következményei.

![](assets/2024-05-17-23-05-48-image.png)

![](assets/2024-05-17-23-08-56-image.png)

![](assets/2024-05-17-23-09-17-image.png)

![](assets/2024-05-17-23-09-46-image.png)

![](assets/2024-05-17-23-10-16-image.png)

![](assets/2024-05-17-23-10-43-image.png)

![](assets/2024-05-17-23-11-18-image.png)

![](assets/2024-05-17-23-11-46-image.png)

## Lineáris programozás alkalmazásai

##### Bevezető

*Példa:*

Az operációkutatás feladatának szemléltetéséhez tekintsük a következő gyakorlati
problémát. Adott egy műhely, amely asztalokat, székeket és szekrényeket gyárt. A
gyártás során kétféle anyagot használnak fel, egyfajta lemezt és egyfajta deszkát.
Ezek korlátozott mennyiségben állnak rendelkezésre.
A feladat: olyan termékösszetétel meghatározása, amely mellett a műhely nyeresége
maximális.
Ehhez egy matematikai modellt konstruálhatunk. Jelölje
𝑥<sub>1</sub>, 𝑥<sub>2</sub>, 𝑥<sub>3</sub> a gyártásra kerülő asztalok, székek, szekrények számát,
𝑙<sub>1</sub>, 𝑙<sub>2</sub>, 𝑙<sub>3</sub> egy asztal, egy szék, egy szekrény készítéséhez szükséges lemezek számát,
𝑑<sub>1</sub>, 𝑑<sub>2</sub>, 𝑑<sub>3</sub> egy asztal, egy szék, egy szekrény készítéséhez szükséges deszkák
számát,
𝑐<sub>1</sub>, 𝑐<sub>2</sub>, 𝑐<sub>3</sub> egy asztal, egy szék, egy szekrény gyártásából származó nyereséget,
𝑙, 𝑑 a rendelkezésre álló lemezek és deszkák számát.
A tekintett probléma egy úgynevezett optimumszámítási modellel írható le. Amely
matematikai szempontból egy feltételes szélsőérték feladat

![](assets/2024-05-18-11-42-06-image.png)

##### 1.2 A modellalkotás elemei

A vizsgálat tárgyát képező tevékenységet felbontjuk véges sok, úgynevezett elemi
tevékenységre. Elemi tevékenységen a teljes tevékenység azt a pontosan körülhatárolt
részét értjük, amelyet tovább bontani már nem szándékozunk. Jelölje az elemi
tevékenységeket 𝐸<sub>1</sub>, . . . , 𝐸<sub>𝑛</sub>

Minden egyes 𝐸<sub>𝑖</sub> elemi tevékenységhez rendeljünk hozzá egy 𝑥<sub>𝑖</sub> valós változót, amely
azt reprezentálja, hogy 𝐸<sub>𝑖</sub> milyen mértékben vesz részt a teljes tevékenységben. Az 𝒙<sub>𝒊</sub>
változót az 𝐸<sub>𝑖</sub> elemi tevékenység szintjének, **intenzitásának** nevezzük. Példánkban a legyártandó termékek száma az illető elemi tevékenység intenzitása,
amelyeket az (𝑥<sub>1</sub>, 𝑥<sub>2</sub>, 𝑥<sub>3</sub>) vektorral írhatjuk le.

***Feltétel***: a döntési változókra vonatkozó  egyenletek vagy egyenlőtlenségek, amelyek korlátozzák azok lehetséges  értékeit.

***Lehetséges megoldás:*** egyrészt az 𝑥<sub>𝑖</sub> változókra (𝑖 = 1, . . . , 𝑛), másrészt az (𝑥<sub>1</sub>, ..., 𝑥<sub>𝑛</sub>), vektorváltozóra vonatkozó feltételeket kell meghatározni. Egy (<u>𝑥</u><sub>1</sub>, . . . , <u>𝑥</u><sub>n</sub>) valós
vektort a feladat lehetséges megoldásának nevezünk, ha 𝑥 az intenzitásértékekre
vonatkozó összes, az előzőekben meghatározott feltételt kielégíti. A lehetséges
megoldások halmazát a továbbiakban 𝐿-lel fogjuk jelölni.

***Célfüggvény:*** Fogalmazzuk meg ezt a célt, azaz adjunk meg egy olyan 𝑧: 𝐿 → V valós függvényt, amely a lehetséges megoldások "értékét", "jóságát" jellemzi a kitűzött cél szempontjából. A függvényt célfüggvénynek nevezzük.1.3 Az optimumszámítási modellekkel megadott matematikai feladatok megoldására

##### 1.3 Az optimumszámítási modellekkel megadott matematikai feladatok megoldására

𝐿 halmazon keressük a célfüggvény szélsőértékét. Maximumkeresés esetén
maximumfeladatról, minimumkeresésnél minimumfeladatról beszélünk.

Maximum feladatnál egy maximumhelyet optimális megoldásnak, a maximum értékét
pedig optimumnak nevezzük. (Ugyanezen elnevezéseket használjuk minimum feladat
esetén is.) Tehát 𝐱̅ ∈ 𝐿 optimális megoldása egy maximum feladatnak, ha 𝑧(𝐱̅ ) ≥ 𝑧(𝐱)
teljesül bármely 𝐱 ∈ 𝐿 lehetséges megoldásra, és ebben az esetben az optimum 𝑧(𝐱̅ ).

##### 2.2. A lineáris programozás általános feladata, standard feladat

# 

##### Áttekintés

A lineáris programozási feladat célja egy lineáris függvény maximumának vagy minimumának meghatározása adott lineáris feltételek mellett. Ezek a feltételek egyenlőségek vagy egyenlőtlenségek formájában jelennek meg. Mivel minden maximum probléma átalakítható egy minimum problémává (és fordítva), a továbbiakban csak minimum problémákkal foglalkozunk.

##### Minimum feladat formája

A lineáris programozási feladatok általános formája a következő:

$$
\begin{aligned}
& a_{11}x_1 + \dots + a_{1m}x_m \leq b_1 \\
& \vdots \\
& a_{k1}x_1 + \dots + a_{km}x_m \leq b_k \\
& a_{(k+1)1}x_1 + \dots + a_{(k+1)m}x_m = b_{k+1} \\
& \vdots \\
& a_{l1}x_1 + \dots + a_{lm}x_m = b_l \\
& a_{(l+1)1}x_1 + \dots + a_{(l+1)m}x_m \geq b_{l+1} \\
& \vdots \\
& a_{n1}x_1 + \dots + a_{nm}x_m \geq b_n \\
& \alpha + c_1x_1 + \dots + c_mx_m = z \rightarrow \min
\end{aligned}

$$

##### Mátrixos formában

Mátrixos és vektoros alakban a feladat a következőképpen írható fel:
$
\begin{aligned}
& A_1x \leq b^{(1)} \\
& A_2x = b^{(2)} \\
& A_3x \geq b^{(3)} \\
& \alpha + cx = z(x) \rightarrow \min
\end{aligned}
$
ahol $ A_1 $, $A_2 $, $A_3$ mátrixok, és $ b^{(1)} $, $ b^{(2)} $, $ b^{(3)} $ vektorok, valamint $ c $ a célfüggvény együtthatóit tartalmazza.

- $ A_1 $ mátrix: Ez a mátrix a $\leq$ típusú egyenlőtlenségek együtthatóit tartalmazza.
  
  Például, ha a feltételek a következők:
  
  $\begin{aligned}
   2x_1 + 3x_2 &\leq 5 \\
   4x_1 + x_2 &\leq 11
   \end{aligned}$
  
  akkor az ( A_1 ) mátrix:
  
  $A_1 = \begin{pmatrix}
   2 & 3 \\
   4 & 1
   \end{pmatrix}$
  
  és a ( b^{(1)} ) vektor:
  
  $b^{(1)} = \begin{pmatrix}
   5 \\
   11
   \end{pmatrix}$

- Többi ugyanígy, csak $\geq$ és $=$ tartamató feltételekkel

##### Vektor és mátrix méretek

Az egyes vektorokat és mátrixokat külön nem jelöljük meg sor- vagy oszlopvektorként, mivel a kontextusból ez egyértelmű. Például $ c = (c_1, ..., c_m) $ és $ x $ oszlopvektor, amelynek komponensei $ x_1, ..., x_m $. Az $ A_1 $ mátrix például $ k \times m $ méretű.

##### Feltételek normalizálása

Ha a feladatban az egyenlőségek vagy egyenlőtlenségek jobb oldala negatív, akkor ezeket megszorozhatjuk $-1$-gyel, hogy a feltételrendszer pozitív legyen. Ezáltal a feltételrendszerhez tartozó lehetséges megoldások halmaza nem változik, és a két feladat optimális megoldása megegyezik.

##### Nemnegatív változók bevezetése

A változók $ u $ és $ v $ nemnegatív különbségével újraírhatjuk a feladatot:
$
\begin{aligned}
& A_1(u - v) \leq b^{(1)} \\
& A_2(u - v) = b^{(2)} \\
& A_3(u - v) \geq b^{(3)} \\
& u \geq 0, v \geq 0 \\
& \alpha + c(u - v) = \tilde{z}(u, v) \rightarrow \min
\end{aligned}
$
Ez a formálás lehetővé teszi a lineáris programozási feladat megoldását nemnegatív változók használatával, ami egyszerűsíti a megoldási módszerek alkalmazását.

##### Eljárás a Standard Feladatra Való Visszavezetésre

1. lépés. Ha a megoldandó feladat maximum feladat, akkor szorozzuk meg a célfüggvényt −1-gyel, és keressük ennek az új célfüggvénynek a minimumát.
2. lépés. Ha szerepel negatív mennyiség a jobboldalon, akkor szorozzuk meg a megfelelő egyenlőséget vagy egyenlőtlenséget −1-gyel.
3. lépés. Ha szerepelnek olyan változók a feladatban, amelyekre nincs előírva
   nemnegativitási feltétel, akkor helyettesítsük rendre ezeket a változókat két nemnegatív változó különbségével.
4. lépés. Minden egyes egyenlőtlenség baloldalához adjunk hozzá illetve vonjunk ki egy nemnegatív változót attól függően, hogy a tekintett egyenlőtlenségben ≤ illetve ≥ szerepel, és változtassuk az egyenlőtlenségeket egyenlőségekre.

Két standard feladatot ekvivalensnek nevezünk, ha a lehetséges megoldások halmazai egybeesnek, és ezen a közös L halmazon a két célfüggvény megegyezik.

***Standard alak:***

$\begin{aligned}
& Ax = b \\
& x \geq 0 \\
& \alpha + cx = z(x) \rightarrow \min
\end{aligned}$

**Kanonikus alak:**

$\begin{aligned}
& A_1x \leq b^{(1)} \\
& A_2x = b^{(2)} \\
& A_3x \geq b^{(3)} \\
& x \geq 0 \\
& \alpha + cx = z(x) \rightarrow \min
\end{aligned}$

##### Szimplex Algoritmus

A szimplex algoritmus a lineáris programozási feladatok megoldására használt eljárás, amelyet George B. Dantzig fejlesztett ki. Az algoritmus lépésről lépésre javítja a célfüggvény értékét, amíg el nem éri az optimális megoldást. Az alábbiakban részletesen bemutatom a szimplex algoritmus lépéseit:

##### 1. lépés: Optimális megoldás ellenőrzése

- **Feltétel:** Ha a kanonikus alakú feladat célfüggvénye nem tartalmaz negatív együtthatót, akkor a bázismegoldás már optimális.
- **Teendő:** Ha nincs negatív együttható a célfüggvényben, az eljárás véget ér, és a jelenlegi megoldás optimális. Ha van negatív együttható, folytatjuk a 2. lépéssel.

##### 2. lépés: Belépő változó kiválasztása

- **Feltétel:** Vegyük a célfüggvény negatív együtthatói közül a legkisebbet (legnagyobb abszolút értékű negatív együttható). Jelölje $ c_j $ ezt az együtthatót.
- **Teendő:** 
  - Ha minden $ a_{rj} \leq 0 $ (ahol $ r = 1, ..., n $), akkor a célfüggvény alulról nem korlátos, és az eljárás véget ér, mert nincs optimális megoldás. 
  - Ellenkező esetben folytassuk a 3. lépéssel.

##### 3. lépés: Kilépő változó kiválasztása és generáló elem meghatározása

- **Feltétel:** Határozzuk meg a következő hányadosok minimumát: $ \min \{ b_r / a_{rj} : a_{rj} > 0, 1 \leq r \leq n \} $. Jelölje $ b_{k1} / a_{k1j}, ..., b_{ks} / a_{ksj} $ a minimummal egyenlő értékeket.
- **Teendő:** 
  - Válasszuk a legkisebb sorindexű $ a_{ktj} $ elemet generáló elemként (ahol $ t = 1, ..., s $).
  - Hajtsuk végre az alábbi átalakításokat:
    - Az $ r_k $ egyenlet új formája: $ r_k' = \frac{1}{a_{kj}} r_k $
    - Az összes többi egyenlet új formája: $ r_i' = r_i - \frac{a_{ij}}{a_{kj}} r_k $ (ahol $ 1 \leq i \leq n, i \neq k $)
    - A célfüggvény új formája: $ z' = z - \frac{c_j}{a_{kj}} r_k $
  - Folytassuk az eljárást az 1. lépéssel a kapott új kanonikus alakú feladattal.

**Lehetséges kanonikus alakú feladat:**

Egy standard feladatot lehetséges kanonikus alakú feladatnak nevezünk, ha sor- és oszlopcserékkel, valamint a változók átjelölésével az alábbi formában írható fel:

$\begin{aligned}
& x_1 + a_{1, n+1}x_{n+1} + \ldots + a_{1, n+m}x_{n+m} = b_1 \\
& x_2 + a_{2, n+1}x_{n+1} + \ldots + a_{2, n+m}x_{n+m} = b_2 \\
& \vdots \\
& x_n + a_{n, n+1}x_{n+1} + \ldots + a_{n, n+m}x_{n+m} = b_n \\
& x_j \geq 0 \quad (j = 1, \ldots, n + m), \quad b_i \geq 0 \quad (i = 1, \ldots, n) \\
& \alpha + c_{n+1}x_{n+1} + \ldots + c_{n+m}x_{n+m} = z(x) \rightarrow \min
\end{aligned}
$

Mitől lesz lehetséges kanonikus alakú?

1. **Egyenletek szerkezete**: Minden egyenletben a $ x_i $ változók különállóan szerepelnek az $ a_{i, n+1}x_{n+1}, \ldots, a_{i, n+m}x_{n+m} $ kifejezésekkel együtt. Ez azt jelenti, hogy a bal oldalon minden egyenlet egy változót tartalmaz az  $ x_1, x_2, \ldots, x_n $ közül, és minden ilyen változó együtthatója 1.

2. **Nemnegativitási feltételek**: Az összes változóra ($ x_j $) és az egyenletek jobb oldali értékeire ($ b_i $) nemnegativitási feltételek vonatkoznak.

3. **Célfüggvény**: A célfüggvény $ \alpha + c_{n+1}x_{n+1} + \ldots + c_{n+m}x_{n+m} $ formában van felírva, ahol a $ c $ együtthatók a célfüggvény együtthatói.

#### Példa átalakításra

Tegyük fel, hogy van egy standard lineáris programozási feladatunk:
$
\begin{aligned}
& 2x_1 + 3x_2 + x_3 = 5 \\
& x_1 + 2x_2 + 4x_3 = 6 \\
& x_1, x_2, x_3 \geq 0 \\
& z = x_1 + 4x_2 + 3x_3 \rightarrow \min
\end{aligned}
$

Ahhoz, hogy ezt lehetséges kanonikus alakú feladattá alakítsuk, szükség lehet sor- és oszlopcserékre, valamint a változók átjelölésére. Tegyük fel, hogy a jelenlegi formát át tudjuk alakítani úgy, hogy az egyenletek bal oldalán lévő változók mindegyikének együtthatója 1 legyen, és ezek különállóan szerepeljenek.

Az átalakítás után a lehetséges kanonikus alakú feladat így nézhet ki:

$\begin{aligned}
& x_1 + \frac{3}{2}x_2 + \frac{1}{2}x_3 = \frac{5}{2} \\
& x_2 + \frac{1}{2}x_1 + 2x_3 = 3 \\
& x_1, x_2, x_3 \geq 0 \\
& z = x_1 + 4x_2 + 3x_3 \rightarrow \min
\end{aligned}
$

**Bázisváltozó:** az egyenletek bal oldalán lévő változók

**Nem bázis változók:** a célfüggvényben lévő változók

**Degenerált bázismegoldás:** a bázisváltozók közük legalább az egyiknek értéke 0

##### Részletes Példa

![](assets/2024-05-18-22-02-27-image.png)

![](assets/2024-05-18-22-02-51-image.png)

![](assets/2024-05-18-22-03-30-image.png)

![](assets/2024-05-18-22-03-44-image.png)

![](assets/2024-05-18-22-03-59-image.png)

Magyarázat a $+9/2$-re a jobb oldalon: $-((2/2)*-(7/2))$. Minden lépésnél a jobb oldalt is figyelembe kell venni!

![](assets/2024-05-18-22-04-27-image.png)

![](assets/2024-05-18-22-05-20-image.png)

# 3. Dualitás, duális szimplex algoritmus. Egészértékű programozás

### Dualitás

A "dualizmus" rész részletesen tárgyalja a lineáris programozási feladatok közötti kapcsolatot. Minden lineáris programozási feladathoz hozzárendelhető egy másik, úgynevezett duális feladat, amely a következő tulajdonságokkal rendelkezik:

1. A duális feladat ugyanazokat a paramétereket tartalmazza, mint az eredeti (prímál) feladat.
2. A duális feladat duálisa megegyezik az eredeti feladattal.

##### Prímál és Duál Feladatok

A prímál feladat általános alakja:
$ Ax \leq b, \quad x \geq 0 $
$ cx = z(x) \to \max $

A hozzá tartozó duális feladat:
$ yA \geq c, \quad y \geq 0 $
$ yb = w(y) \to \min $

##### Dualitási Tételek

- **Gyenge dualitási tétel:** Ha $ x$ a prímál feladat lehetséges megoldása és $ y $ a duális feladat lehetséges megoldása, akkor $ z(x) \leq w(y) $.
- **Erős dualitási tétel:** Ha bármelyik feladatnak (prímál vagy duál) létezik optimális megoldása, akkor mindkettőnek létezik, és az optimumértékek megegyeznek.
- **Komplementaritási tétel:** $ x $ és $ y $ akkor és csak akkor optimális megoldások, ha $ y_i (b_i - \sum a_{it}x_t) = 0 $ minden $ i $-re és $ x_t (\sum a_{it} y_i - c_t) = 0 $ minden $ t $-re.

##### Következmények

- Ha a duális feladat célfüggvénye alulról nem korlátos, akkor a prímál feladatnak nincs lehetséges megoldása.
- A szimplex módszer használatával a prímál feladat megoldásának utolsó iterációjában kiolvasható a duális feladat egy optimális megoldása.

##### Példa primál és duál párra

A prímál feladat:
$ x_1 + x_2 \leq 5 $
$ x_1 + 3x_2 \leq 7 $
$ x \geq 0 $
$ 2x_1 + x_2 \to \max \]

A duális feladat:
$ y_1 + y_2 \geq 2 $
$ y_1 + 3y_2 \geq 1 $
$ y \geq 0 $
$ 5y_1 + 7y_2 \to \min $

A fenti példák és tételek bemutatják, hogy a lineáris programozásban a prímál és duális feladatok hogyan kapcsolódnak egymáshoz, és hogyan lehet ezeket felhasználni optimális megoldások megtalálására.

##### Komplementaritási tétel használata ellenőrzésre

![](assets/2024-05-19-17-34-56-image.png)

Kiegészítés:

$\begin{aligned}
2(2) - 6(4) + 2(0) + 7(0) + 3(7) + 8(0) &= 4 - 24 + 0 + 0 + 21 + 0 = 1 \\
-3(2) - 1(4) + 4(0) - 3(0) + 1(7) + 2(0) &= -6 - 4 + 0 - 0 + 7 + 0 = -3 \quad (*) \\
8(2) - 3(4) + 5(0) - 2(0) + 2(0) &= 16 - 12 + 0 - 0 + 0 = 4 \\
4(2) + 8(0) + 7(0) - 1(7) + 3(0) &= 8 + 0 + 0 - 7 + 0 = 1 \\
5(2) + 2(4) - 3(0) + 6(0) - 2(7) - 1(0) &= 10 + 8 - 0 + 0 - 14 - 0 = 4 \quad (*) \\
\end{aligned}$

Megjegyzés: a primál feladat 1., 2. és 3. sorai lettek transzponálva a duális feladathoz, mivel az $x$ vektorban (a tippelt megoldásban) azok az értékek nem nullák

![](assets/2024-05-19-17-41-26-image.png)

Megjegyzés: nem feltétlen kell elég az $y_2=0$ feltétel.

**Mikor lehet érdemes áttérni a duális feladatra és azt megoldani?**

- Tapasztalati megfigyelés. A szimplex algoritmus megoldása során az iterációszám a sorok (korlátozó feltételek) 𝑛 számával arányos. Így, ha egyébként más nem motivál minket, választhatjuk a kevesebb sorból álló (kevesebb korlátozó feltételt tartalmazó) feladatot.

- Ha primál feladatban negatív jobboldalak vannak, és kétfázisú szimplex módszert kellene használni, a duális feladatban meg nem, ez is indokolhatja, hogy inkább a duál feladat megoldását választjuk.

- Ha új sorokat (korlátozó feltételeket) kell hozzáadni a primál feladat feltételrendszeréhez. Egy gyakorlati feladatnál ez nem ritka, hogy menet közben új feltételeket kell hozzávenni az LP-hez.

##### Árnyékár

A **dualitás** gazdasági értelmezése során a primál probléma egy gyártási terv modellje, ahol m terméket állítanak elő n erőforrás felhasználásával. A cél a profit maximalizálása az erőforrások korlátozott rendelkezésre állása mellett. 

###### Primál Probléma

A primál probléma a következő egyenletekből áll:

- $ A x \leq b $
- $ x \geq 0 $
- $ z = c^T x \rightarrow \max $

###### Duális Probléma

A duális probléma ehhez kapcsolódva:

- $ A^T y \geq c $
- $ y \geq 0 $
- $ b^T y = w(y) \rightarrow \min $

###### Árnyékár (Marginal Price)

Az árnyékár, más néven marginális ár, egy erőforrás értékét jelenti a gyártó számára, és kifejezi, hogy mennyivel nő a profit, ha egy egységgel növeljük az adott erőforrás mennyiségét. Ezt Paul Samuelson nevezte el árnyékárnak, és ez a primál-duál optimális megoldások közötti kapcsolat révén értelmezhető.

###### Gazdasági Következmények

- Az árnyékár az az ár, amelyet a gyártó maximálisan megfizethet egy erőforrásért.
- Ha az erőforrás piaci ára alacsonyabb, mint az árnyékár, érdemes megvásárolni azt a termelés bővítéséhez.
- Ha a piaci ár magasabb, akkor érdemes eladni az erőforrást vagy csökkenteni a termelést.

###### Érzékenységvizsgálat

Az érzékenységvizsgálat elemzi, hogy az LP feladat paramétereinek változása hogyan befolyásolja az optimális megoldást és az optimális értéket. Ez különösen fontos lehet új tevékenységek bevezetésekor vagy meglévő paraméterek módosításakor.

###### Fontos Megjegyzések

- Az árnyékár fogalma csak addig érvényes, amíg az adott bázis optimális marad.
- Az optimális megoldás szerkezete és értékei változhatnak a paraméterek változásával.

### Duális szimplex algoritmus

A duális szimplex algoritmus olyan típusú feladatok megoldására alkalmazható, amelyek az alábbi formában adottak:
$ E y + A x = b, \, x \geq 0, \, y \geq 0 \, (c \geq 0) $
$ c^T x = z \rightarrow \min $

**Lépések**:

1. **Első lépés**: Ha a feladat egyenleteinek jobboldalai nemnegatívak, az eljárás véget ér (STOP1), a feladat bázismegoldása optimális megoldás.

2. **Második lépés**: Válasszuk ki a negatív $ b_t $-k minimumát (a jobboldalon), és jelölje $ b_k $ a minimummal megegyező $ b_t $-k közül a legkisebb indexűt. Ha $ a_{ks} \geq 0 \, (s = 1, \ldots, m) $, az eljárás véget ér (STOP2), mivel a feladatnak nincs lehetséges megoldása. Ellenkező esetben a harmadik lépés következik.

3. **Harmadik lépés**: Ha $ \min \left\{ \frac{c_s}{-a_{ks}} \colon a_{ks} < 0, \, 1 \leq s \leq m \right\} = \frac{c_{j1}}{-a_{kj1}} = \ldots = \frac{c_{jr}}{-a_{kjr}} $, akkor válasszuk az $ a_{kjt} $ elemek közül a legkisebb oszlopindexűt generáló elemnek, majd hajtsuk végre az előírt átalakításokat (képen lentebb). Az új feladattal folytassuk az eljárást az első lépéssel (GOTO 1).
   
   ![](assets/2024-05-19-22-10-27-image.png)
   
   ![](assets/2024-05-19-22-09-23-image.png)

#### Példa

![](assets/2024-05-19-22-12-03-image.png)

![](assets/2024-05-19-22-12-50-image.png)

![](assets/2024-05-19-22-13-08-image.png)

**Algoritmus előnyei:**

1. **Jobboldali vektorral szembeni rugalmasság**: Az algoritmus alkalmazható olyan esetekben is, amikor a jobboldali $ b $ vektor nemnegativitása nincs biztosítva, hanem a célfüggvény-együtthatók $ c $ vektorának nemnegativitása a kritérium.

2. **Optimális megoldás leolvasása**: A duális szimplex algoritmus végén kapott szimplex táblázatból közvetlenül leolvasható az eredeti feladat optimális megoldása, mivel a szimplex táblázatok csak elrendezési és előjelbeli különbségeket mutatnak.

3. **Kétfázisú módszer helyett egyszerűbb megoldás**: Bizonyos esetekben, például amikor a (3.2.1) primál feladatban negatív jobboldali elemek vannak, a kétfázisú szimplex módszer alkalmazása helyett a duális szimplex algoritmus egyszerűbb megoldást kínál.

4. **Iterációszám csökkentése**: Tapasztalati megfigyelések szerint a szimplex algoritmus iterációszáma arányos a sorok (korlátozó feltételek) számával. Ha a primál feladatnak több korlátozó feltétele van, mint a duál feladatnak, akkor érdemes lehet a duál feladatot megoldani, amely kevesebb iterációt igényel.

### Egészértékű programozás, Gomory-módszer (cutting plane method – metsző sík módszer, Ralph Gomory – 1958)

#### Az alapfeladat és relaxációja

Az egészértékű programozás (ILP - Integer Linear Programming) lineáris programozási változatával foglalkozik a dokumentum. Az alábbi típusú feladatokat vizsgálja:

![](assets/2024-05-19-22-45-07-image.png)

Feltételezzük, hogy $\mathbf{A}$, $\mathbf{b}$, $\mathbf{c}$, és $\alpha$ egész számok, $\mathbf{b} \geq 0$, és a lehetséges megoldások halmaza korlátos.

#### Gomory-módszer

A Gomory-módszer egy metszési eljárás, amelynek célja az ILP feladat megoldása a következő módon:

1. **Relaxáció:** A probléma egészértékűségi feltételének elhagyása után oldjuk meg a relaxált LP feladatot. Ha az optimális megoldás egész, akkor ez az ILP megoldása is.
2. **Metszési síkok bevezetése:** Ha a relaxált LP megoldása nem egész, akkor további feltételekkel bővítjük a feladatot. Ezeket a feltételeket metszési síkoknak nevezik, amelyek nem vágnak le egész megoldásokat.
3. **Iteráció:** A metszési síkokat addig adjuk hozzá, amíg az aktuális relaxált feladat optimális megoldása egész lesz.

#### Gomory-féle metszési eljárás lépései:

1. **Előkészítő rész:** Oldjuk meg a relaxált feladatot a szimplex algoritmussal. Ha az optimális megoldás egész, akkor vége az eljárásnak. Ellenkező esetben az iterációs eljárás következik.
2. **Iterációs rész:** Vegyük az első olyan egyenletet, amelyben a bázisváltozó nem egész. Ebből az egyenletből képezzünk egyenlőtlenséget, és vegyük ennek a Gomory-metszetét. Szorozzuk az egyenlőtlenséget −1-gyel, és vezessünk be egy új változót. Az így kapott egyenlettel bővítsük a feladatot, majd oldjuk meg a duális szimplex algoritmussal. Ha az optimális megoldás egész, akkor vége az eljárásnak. Ellenkező esetben folytatjuk az iterációt.

#### Példa az eljárásra:

Az egyik példában, amikor a szimplex táblázat egy változója nem egész, például $ x_2 $, a következő metszési feltételt kapjuk:

$x_2 - \frac{1}{2}u_1 + \frac{1}{2}y_2 \geq \frac{1}{2}
$

Az iteráció során ezeket a feltételeket bevezetve és a duális szimplex algoritmust alkalmazva végül egy egész megoldáshoz jutunk.

#### Hátrányok:

- Nagy iterációs lépésszám, amely a feladat méreteitől függően növekszik.
- A feladat méretének növekedése minden egyes lépésben.
- Számítástechnikai nehézségek, mint például a kerekítési hibák, amelyek az együtthatók egész vagy nem egész voltának eldöntését komplikálják.

A Gomory-módszer jelentős hozzájárulás az egészértékű programozás területén, különösen a metszési síkok módszerének kidolgozása révén.

# 4. Hozzárendelési és szállítási feladat

## Hozzárendelési feladat

A hozzárendelési feladat egy speciális egészértékű lineáris programozási probléma, amely számos gyakorlati alkalmazással rendelkezik. A legismertebb feladat a munkák optimális kiosztása adott számú dolgozó és ugyanennyi munka között, ahol minden dolgozó különböző költségekkel tudja elvégezni a feladatokat. A cél, hogy minden dolgozó pontosan egy munkát kapjon, az összes munkát kiosszák, és a munkavégzés összköltsége minimális legyen.

#### Formális Modell

Jelölések:

- $ n $ a dolgozók száma.
- $ c_{ij} $ az $ i $-edik dolgozó által végzett $ j $-edik munka költsége.
- $ x_{ij} = \begin{cases} 
  1, & \text{ha az } i \text{-edik dolgozó hajtja végre a } j \text{-edik munkát,} \\
  0, & \text{különben.}
  \end{cases} $

#### Észrevételek

- Minden dolgozó pontosan egy munkát fog végrehajtani, és minden munka kiosztásra kerül.
- A probléma megoldásai olyan 0 és 1 elemekből álló mátrixok, amelyek minden sora és oszlopa pontosan egy 1-est tartalmaz.
- Az ilyen mátrixok száma $ n! $, ami biztosítja, hogy mindig létezik optimális megoldás.
- A feladat költségmátrixa $ C $, amelyet $ H(C) $-vel jelölünk.

#### Magyar Módszer

A magyar módszer H. W. Kuhn által 1955-ben publikált algoritmus, amely lényegesen hatékonyabb a lehetséges mátrixok előállításánál és vizsgálatánál. Kuhn algoritmusa Egerváry Jenő és König munkáján alapul, akik a páros gráfok maximális párosítási problémáit vizsgálták.

#### Iterációs Eljárás

A magyar módszer iterációs eljárásának célja egy olyan mátrixsorozat előállítása, amely rendelkezik a következő tulajdonságokkal:

1. $ C \sim C(0) $

2. $ C(t) \sim C(t+1) $ minden $ t = 0, \ldots, k-1 $

3. $ C(t) \geq 0 $ minden $ t = 0, \ldots, k $

4. $ C(k) $-ban ki van jelölve egy $ n $-elemű független 0-rendszer.
- Egy mátrix valamely sorát (oszlopát) kötött sornak (oszlopnak) nevezzük, ha
  mellette (felette) egy „+” jel áll.

- A mátrix valamely elemét szabad elemnek nevezzük, ha nincs semmiféle jellel
  ellátva, és sem a sora, sem az oszlopa nincsen lekötve.

- Speciálisan, ha az illető (szabad) elem 𝟎, akkor szabad 𝟎-ról beszélünk.

- Végül használni fogjuk a 𝐂 ≥ 𝟎 jelölést, ha a C mátrix minden eleme nemnegatív.

A $ \mathbf{C} \sim \mathbf{D} $ jelölés azt jelenti, hogy a $\mathbf{C}$ és $\mathbf{D}$ mátrixok ekvivalensek. Két mátrix ekvivalens, ha léteznek olyan $\alpha_i$ (sor állandók) és $\beta_j$ (oszlop állandók) valós számok, amelyek kielégítik a következő feltételt minden $ 1 \leq i \leq n $ és $ 1 \leq j \leq m $ indexpárra:

$ c_{ij} = d_{ij} + \alpha_i + \beta_j $

Ez azt jelenti, hogy a $\mathbf{C}$ mátrix elemei az $\mathbf{D}$ mátrix elemeiből úgy állíthatók elő, hogy hozzáadunk egy-egy állandót minden sor és minden oszlop elemeihez.

### Alkalmazás

Az ekvivalencia reláció $( \mathbf{C} \sim \mathbf{D} )$ használata lehetővé teszi, hogy a hozzárendelési feladat különböző költségmátrixokkal is megoldható legyen, ugyanazon eljárás alapján. Az ekvivalencia segít az optimalizálási folyamatban, mivel egyszerűsíthetjük a mátrixot anélkül, hogy megváltoztatnánk az eredeti probléma megoldását.

#### Lépések

1. Előkészítés: Minden sorból és oszlopból vonjuk ki a minimum értéket, hogy $ C(0) $-t kapjuk.
2. Iteráció: 
   - Független 0-rendszert jelölünk ki.
   - Ha nincs elég független 0, akkor redukciós lépést alkalmazunk.
   - Megállás akkor, ha az \( n \) elemű független 0-rendszer kialakul.

![](assets/2024-05-20-14-18-46-image.png)

![](assets/2024-05-20-14-36-06-image.png)

![](assets/2024-05-20-14-36-18-image.png)

**Példa:**

![](assets/2024-05-20-14-39-05-image.png)

![](assets/2024-05-20-14-39-23-image.png)

![](assets/2024-05-20-14-39-37-image.png)

![](assets/2024-05-20-14-39-49-image.png)

![](assets/2024-05-20-14-40-01-image.png)

![](assets/2024-05-20-14-40-15-image.png)

![](assets/2024-05-20-14-40-28-image.png)

## Szállítási feladat

A szállítási probléma egy klasszikus optimalizálási probléma, amelynek célja a termékek egy vagy több forrásból egy vagy több célba történő szállításának költségminimalizálása. A feladat során figyelembe kell venni a források kapacitásait és a célok igényeit, valamint a szállítási költségeket.

A feladat megoldása lineáris programozási módszerekkel történik, és gyakran használnak különböző algoritmusokat, mint például a szimplex módszert vagy a speciális szállítási algoritmusokat, hogy megtalálják a legkisebb költséggel járó megoldást.

A feltöltött képen egy példafeladat látható. Nézzük meg részletesen ezt a példát:

### Példafeladat

A Powercónak 3 erőműtelepe van, amelyek 4 város szükségletét látják el. Az egyes erőművek adott mennyiségű (kWh) elektromos energiát képesek szolgáltatni. Adott az egyszerre megjelenő csúcsfogyasztási igény ezekben a városokban. 1 millió kWh áram szállítása egy erőműből egy városba a távolságuktól függ.

#### Adatok:

- 1. erőmű: 35 millió kWh
- 2. erőmű: 50 millió kWh
- 3. erőmű: 40 millió kWh

#### Városok csúcsigényei (millió kWh):

- 1. város: 45
- 2. város: 20
- 3. város: 30
- 4. város: 30

#### Szállítási költségek (1 millió kWh-ra, adott városba):

| Honnan/Város | 1. város | 2. város | 3. város | 4. város |
| ------------ | -------- | -------- | -------- | -------- |
| 1. erőmű     | 8        | 6        | 10       | 9        |
| 2. erőmű     | 9        | 12       | 13       | 7        |
| 3. erőmű     | 14       | 9        | 16       | 5        |

#### Feladat

Adjuk meg egy lineáris programozási feladatot (LP), ami minimalizálja a költséget, és a városok csúcsigényeit kielégíti!

### Matematikai Formuláció

#### Döntési változók

Legyen $ x_{ij} $ az a mennyiség, amelyet az $ i $-edik erőműből az $ j $-edik városba szállítanak.

#### Célfüggvény

Minimalizáljuk a teljes szállítási költséget:
$ \text{Minimize} \quad \sum_{i=1}^{3} \sum_{j=1}^{4} c_{ij} x_{ij} $
ahol $ c_{ij} $ az egységnyi költség az $ i $-edik erőműből az $ j $-edik városba szállítani.

#### Korlátok

1. Az erőművek kapacitásának korlátai:
   $ \sum_{j=1}^{4} x_{ij} \leq \text{Erőmű}_i \quad \forall i $
- 1. erőmű: $ x_{11} + x_{12} + x_{13} + x_{14} \leq 35 $

- 2. erőmű: $x_{21} + x_{22} + x_{23} + x_{24} \leq 50$

- 3. erőmű: $x_{31} + x_{32} + x_{33} + x_{34} \leq 40$
2. A városok igényeinek kielégítése:
   $\sum_{i=1}^{3} x_{ij} = \text{Város}_j \quad \forall j$
- 1. város: $ x_{11} + x_{21} + x_{31} = 45$

- 2. város: $x_{12} + x_{22} + x_{32} = 20$

- 3. város: $x_{13} + x_{23} + x_{33} = 30$

- 4. város: $x_{14} + x_{24} + x_{34} = 30$
3. Nemnegativitási feltételek:
    $x_{ij} \geq 0 \quad \forall i, j$ 

Ezekkel a korlátokkal és célfüggvénnyel megadható a szállítási probléma lineáris programozási modellje.

![](assets/2024-05-20-15-09-54-image.png)

- Kétfázisú szimplex módszerrel megoldható, de degenerált a feladat a sok 0 miatt, így egyszerűbb módszer is adható.

- Ez lesz a disztribúciós módszer, vagy más néven szállítási szimplex módszer.

**Disztribúciós módszer**

A disztribúciós módszer, más néven a MODI (Modified Distribution) módszer, egy hatékony algoritmus a szállítási problémák optimalizálására. A módszer a kezdeti megoldás optimalizálását célozza, hogy elérjük a minimális költséget. A disztribúciós módszer a szállítási táblázatban történő allokációk elosztásának módosításával dolgozik.

### Lépések a Disztribúciós módszerhez

1. **Kezdeti megoldás meghatározása**:
   
   - Használjunk egy kezdeti megoldási módszert, mint például az Északi-sarkpont módszer, a Legkisebb költség módszer vagy a Vogel-approximitás módszer, hogy meghatározzuk a kezdeti alapvető megoldást.

2. **Potenciálok (u és v értékek) kiszámítása**:
   
   - A potenciálok $u_i$ és $v_j$ értékek segítségével kiszámítjuk az egyes cellák csökkentett költségeit. Kezdjük egy tetszőleges $u_i$ vagy $v_j$ értékkel, általában 0 -val.
   - Az összes potenciál értéket úgy kell meghatározni, hogy a foglalt cellák esetén teljesüljön a $ u_i + v_j = c_{ij} $ egyenlet, ahol $c_{ij}$ az adott cella költsége.

3. **Csökkentett költségek ($\Delta_{ij}$) kiszámítása**:
   
   - A csökkentett költséget a következőképpen számoljuk ki minden üres cellára: $ \Delta_{ij} = c_{ij} - (u_i + v_j) $.
   - Ha minden $\Delta_{ij} \geq 0$, akkor a jelenlegi megoldás optimális.

4. **Optimalizációs lépések végrehajtása**:
   
   - Ha van olyan cella, ahol $\Delta_{ij} < 0$, akkor egy zárt hurkot (loopot) keresünk, amely az üres cellából indul és visszatér oda.
   - Az egyes irányokban váltakozó \(+\) és \(-\) jelekkel végrehajtjuk a szükséges módosításokat, hogy csökkentsük a költségeket.

5. **Új megoldás kiszámítása**:
   
   - Frissítjük az allokációkat a zárt hurok mentén és újra számoljuk a potenciálokat.
   - Ismételjük meg a csökkentett költségek számítását és ellenőrizzük az optimalitást.

6. **Iteráció folytatása**:
   
   - A fenti lépéseket addig ismételjük, amíg minden $\Delta_{ij} \geq 0$ nem lesz, jelezve, hogy elértük az optimális megoldást.

### Példa a disztribúciós módszer alkalmazására

A feltöltött kép alapján a következő kezdeti megoldást kaphatjuk a Vogel-approximitás módszerrel:

#### Kezdeti megoldás (példa)

|          | 1. város | 2. város | 3. város | 4. város | Készlet |
| -------- | -------- | -------- | -------- | -------- | ------- |
| 1. erőmű | 20       | 0        | 0        | 15       | 35      |
| 2. erőmű | 25       | 20       | 0        | 5        | 50      |
| 3. erőmű | 0        | 0        | 30       | 10       | 40      |
| Igény    | 45       | 20       | 30       | 30       |         |

### Potenciálok kiszámítása

Legyen $ u_1 = 0 $.

- $ u_1 + v_1 = 8 $ ⇒ $ v_1 = 8 $
- $ u_1 + v_4 = 9 $ ⇒ $ v_4 = 9 $
- $ u_2 + v_1 = 9 $ ⇒ $ u_2 = 1 $
- $ u_2 + v_2 = 12 $ ⇒ $ v_2 = 11 $
- $ u_2 + v_4 = 7 $ ⇒ $ v_4 = 6 $ (de $ v_4 $ már 9, így ellenőrizzük az összes potenciált)
- $ u_3 + v_3 = 16 $ ⇒ $ u_3 = -3 $
- $ u_3 + v_4 = 5 $ ⇒ $ v_4 = 8 $ (javítjuk: $ v_4 = 9 $)

### Csökkentett költségek

Kiszámoljuk az $\Delta_{ij}$-ket, majd megkeressük a legkisebb $\Delta_{ij}$-t, és frissítjük az allokációt a zárt hurok alapján.

Ez a folyamat folytatódik addig, amíg minden csökkentett költség nem lesz nem negatív. Az így kapott megoldás lesz a költségminimalizáló megoldás.

A disztribúciós módszer segítségével tehát megtalálhatjuk a legolcsóbb szállítási tervet a kezdeti megoldás optimalizálásával.

![](assets/2024-05-20-15-23-52-image.png)

![](assets/2024-05-20-15-24-08-image.png)

![](assets/2024-05-22-21-05-47-image.png)

![](assets/2024-05-22-21-06-03-image.png)

![](assets/2024-05-22-21-07-10-image.png)

![](assets/2024-05-22-21-08-34-image.png)

# 5. Generikus programozás, sablonok, kifejezés sablonok, metaprogramozás.

[Generics in C++ 1 - Templates Introduction | Modern Cpp Series - YouTube](https://www.youtube.com/watch?v=S2OFJe73fxA&ab_channel=MikeShah)

### Generikus programozás

A generika az az ötlet, hogy a típusok (Integer, String, ... stb. és a felhasználó által definiált típusok) paraméterei lehetnek metódusoknak, osztályoknak és interfészeknek. Például olyan osztályok, mint a tömb, map, stb., amelyek a generikumok segítségével nagyon hatékonyan használhatók. Bármilyen típushoz használhatjuk őket.

A generikus programozás módszerét a kód hatékonyságának növelése érdekében hajtják végre. A generikus programozás lehetővé teszi a programozó számára, hogy általános algoritmust írjon, amely minden adattípussal működik. Ez kiküszöböli a különböző algoritmusok létrehozásának szükségességét, ha az adattípus egész szám, karakterlánc vagy karakter.

Az általános programozás előnyei a következők:

- Kód újrafelhasználhatósága

- Függvény overload elkerülése

- Egyszer megírt függvény többször és több esetben is használható.

A generikus programozás a C++-ban sablonok segítségével valósítható meg. A sablon egy egyszerű és mégis nagyon hatékony eszköz a C++-ban. Az egyszerű ötlet az adattípus paraméterként való átadása, így nem kell ugyanazt a kódot írni különböző adattípusokhoz. Például egy szoftvercégnek szüksége lehet sort() funkcióra különböző adattípusokhoz. Ahelyett, hogy több kódot írnánk és karbantartanánk, írhatunk egy sort()-t, és paraméterként átadhatjuk az adattípust. 

A compiler fogja a kódot generálni

### Sablonok (Templates)

A sablonok olyan mechanizmusok, amelyek lehetővé teszik a generikus kód írását. Két fő típusa van:

1. **Függvény sablonok (Function Templates):**
   Ezek lehetővé teszik, hogy függvényeket írjunk típusparaméterekkel. Így egyetlen függvény definíció számos különböző típusú adatot képes kezelni.
   
   ```cpp
   template<typename T>
   T max(T a, T b) {
       return (a > b) ? a : b;
   }
   ```

2. **Osztály sablonok (Class Templates):**
   Ezek lehetővé teszik, hogy osztályokat írjunk típusparaméterekkel. Így egyetlen osztály definíció különböző típusú adattagokat és tagfüggvényeket tartalmazhat.
   
   ```cpp
   template<typename T>
   class Stack {
   private:
       std::vector<T> elems;
   public:
       void push(T const& elem);
       void pop();
       T top() const;
   };
   ```
   
   ### Sablonspecializáció (Template Specialization)
   
   A sablonspecializáció lehetővé teszi, hogy egy általános sablonhoz speciális viselkedést definiáljunk bizonyos típusokhoz. Ez hasznos lehet, ha az általános eset nem működik megfelelően bizonyos típusoknál.
   
   #### Teljes Specializáció (Full Specialization)
   
   Ez azt jelenti, hogy egy sablon minden paraméterére meghatározunk egy konkrét implementációt.
   
   ```cpp
   template <>
   class Pair<bool> {
   private:
       bool first, second;
   public:
       Pair(bool a, bool b) : first(a), second(b) {}
       bool getFirst() const { return first; }
       bool getSecond() const { return second; }
   
       bool bothTrue() const { return first && second; }
   };
   ```
   
   #### Részleges Specializáció (Partial Specialization)
   
   Ez azt jelenti, hogy egy sablon egyes paramétereire meghatározunk egy konkrét implementációt, de a többi paraméter általános marad.
   
   ```cpp
   template <typename T>
   class Array {
       // Általános implementáció
   };
   
   template <typename T>
   class Array<T*> {
       // Pointer típusokhoz specifikus implementáció
   };
   ```
   
   #### Traits
   
   - Típus-függő deklarációk egybecsomagolása
   
   - Típusokat és értékeket lehet egymáshoz rendelni
     különböző összefüggésekben
   
   - A kód tisztább és karbantarthatóbb marad
   
   ![](assets/2024-05-23-22-22-24-image.png)
   
   - **Viz osztály**:
     
     - Definiál egy `Viz` nevű struktúrát.
     - Barátként definiálja az `operator<<` függvényt, amely lehetővé teszi, hogy az `ostream` objektumra kiírjuk a "viz" szöveget, amikor egy `Viz` típusú objektumot írunk ki. (többi osztály ugyanígy)
   
   ![](assets/2024-05-23-22-23-00-image.png)
   
   ![](assets/2024-05-23-22-23-21-image.png)
   
   Typedef: meglévő típusnak új nevet ad
   
   ![](assets/2024-05-23-22-23-40-image.png)
   
   **typedef typename Traits::ital_tipus ital_tipus**: Ez a typedef a `Traits` osztályban definiált `ital_tipus` típusra mutat, amely a szereplő kedvenc italának típusát határozza meg.
   
   #### Policy
   
   - Funkcionalitás hozzárendelése sablon argumentumhoz
   
   - Kliens programozók személyre szabhatják a sablon osztályunkat
   
   ![](assets/2024-05-23-22-56-11-image.png)
   
   ![](assets/2024-05-23-22-56-28-image.png)
   
   #### Curiously recurring template pattern
   
   - Közös ősosztály helyett „szokatlan módon ismétlődő” saját ősosztály
   
   - Jim Coplien nevéhez fűződik
   
   ![](assets/2024-05-23-23-06-19-image.png)
   
   ![](assets/2024-05-23-23-07-26-image.png)
   
   ![](assets/2024-05-23-23-08-31-image.png)
   
   **CountedClass** és **CountedClass2** két különböző típusú osztály, amelyek mindegyike a `Counted` sablonból származik. Mindkettő saját számlálóval rendelkezik, mivel különböző típusok.

### Kifejezés sablonok (Expression Templates)

A kifejezés sablonok egy speciális technika, amely optimalizálja a sablonalapú kódot, különösen a numerikus számítások terén. Lehetővé teszik a kifejezések reprezentálását és értékelését anélkül, hogy szükségtelen ideiglenes objektumokat hoznánk létre. Ez javítja a teljesítményt azáltal, hogy a kifejezéseket csak egyszer értékeljük ki.

Például, a lineáris algebrai műveletek során:

```cpp
template<typename T>
class Matrix {
    // ...
};

template<typename T>
Matrix<T> operator+(Matrix<T> const& lhs, Matrix<T> const& rhs) {
    // Kifejezés sablonokat használva a matrix összeadás optimalizálható
}
```

Sure, I'd be happy to explain expression templates in C++ in detail.

### What are Expression Templates?

Expression templates are a C++ programming technique used to improve the performance of mathematical expressions involving operator overloading, especially in the context of linear algebra libraries. They allow the compiler to optimize out temporary objects that would otherwise be created during the evaluation of complex expressions.

### Why Use Expression Templates?

1. **Performance**: By avoiding the creation of intermediate temporary objects, expression templates can significantly reduce the overhead associated with multiple operations. This is particularly important in scientific computing and numerical applications where performance is critical.

2. **Readability and Maintainability**: They allow developers to write mathematical expressions in a natural and readable form without sacrificing performance.

### Basic Concept

Consider a simple example where you have a vector class with overloaded operators for addition and multiplication:

```cpp
#include <vector>

class Vector {
    std::vector<double> data;
public:
    Vector(size_t size) : data(size) {}

    // Overloaded operator for vector addition
    Vector operator+(const Vector& other) const {
        Vector result(data.size());
        for (size_t i = 0; i < data.size(); ++i) {
            result.data[i] = data[i] + other.data[i];
        }
        return result;
    }

    // Overloaded operator for scalar multiplication
    Vector operator*(double scalar) const {
        Vector result(data.size());
        for (size_t i = 0; i < data.size(); ++i) {
            result.data[i] = data[i] * scalar;
        }
        return result;
    }

    double& operator[](size_t index) { return data[index]; }
    const double& operator[](size_t index) const { return data[index]; }
};
```

Using this class, an expression like `a + b + c` would create multiple temporary `Vector` objects, resulting in unnecessary memory allocations and copies.

### Introducing Expression Templates

Expression templates address this issue by constructing an abstract syntax tree (AST) of the expression at compile time and evaluating the entire expression in a single pass.

#### Step 1: Define Expression Template Classes

First, we define template classes to represent different kinds of expressions:

```cpp
template <typename L, typename R>
class AddExpr {
    const L& lhs;
    const R& rhs;
public:
    AddExpr(const L& lhs, const R& rhs) : lhs(lhs), rhs(rhs) {}

    double operator[](size_t i) const {
        return lhs[i] + rhs[i];
    }

    size_t size() const { return lhs.size(); }
};

template <typename Vec, typename Scalar>
class MulExpr {
    const Vec& vec;
    Scalar scalar;
public:
    MulExpr(const Vec& vec, Scalar scalar) : vec(vec), scalar(scalar) {}

    double operator[](size_t i) const {
        return vec[i] * scalar;
    }

    size_t size() const { return vec.size(); }
};
```

#### Step 2: Modify the Vector Class

Next, we modify the `Vector` class to return expression templates instead of `Vector` objects for operator overloads:

```cpp
class Vector {
    std::vector<double> data;
public:
    Vector(size_t size) : data(size) {}

    template <typename Expr>
    Vector(const Expr& expr) : data(expr.size()) {
        for (size_t i = 0; i < data.size(); ++i) {
            data[i] = expr[i];
        }
    }

    template <typename R>
    AddExpr<Vector, R> operator+(const R& other) const {
        return AddExpr<Vector, R>(*this, other);
    }

    MulExpr<Vector, double> operator*(double scalar) const {
        return MulExpr<Vector, double>(*this, scalar);
    }

    double& operator[](size_t index) { return data[index]; }
    const double& operator[](size_t index) const { return data[index]; }
};
```

#### Step 3: Using Expression Templates

Now, when you write an expression like `a + b + c`, it will construct an AST and evaluate the expression in a single pass without creating intermediate `Vector` objects:

```cpp
int main() {
    Vector a(10), b(10), c(10);

    // Fill vectors with some values
    for (size_t i = 0; i < 10; ++i) {
        a[i] = i;
        b[i] = i * 2;
        c[i] = i * 3;
    }

    Vector result = a + b + c;

    for (size_t i = 0; i < 10; ++i) {
        std::cout << result[i] << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

### Key Points

1. **Template Metaprogramming**: Expression templates rely heavily on template metaprogramming to construct the AST and defer evaluation until the entire expression is known.

2. **Lazy Evaluation**: By constructing an expression tree, the evaluation of the expression is deferred until necessary, allowing the compiler to optimize the entire expression as a whole.

3. **Flexibility**: The technique can be extended to handle more complex expressions, including those involving different types of operations and combinations of scalars and vectors.

### Conclusion

Expression templates are a powerful technique in C++ that enable the efficient evaluation of complex expressions involving overloaded operators. They leverage template metaprogramming to construct and evaluate expressions at compile time, eliminating the need for temporary objects and improving runtime performance. This approach is widely used in high-performance computing libraries, particularly those dealing with linear algebra and numerical computations.

### Metaprogramozás

A metaprogramozás olyan programozási technika, amely lehetővé teszi a programok számára, hogy programokat írjanak vagy manipuláljanak. C++-ban a metaprogramozás általában sablonok használatával történik, és gyakran a fordítási időben történő számításokat és optimalizációkat jelent.

#### Template Metaprogramozás (TMP)

A TMP technika segítségével számításokat végezhetünk a fordítási idő alatt. Ez lehetővé teszi az optimalizált kód generálását anélkül, hogy futásidőben kellene számításokat végezni. Például a faktoriális számítása TMP segítségével:

```cpp
template<int N>
struct Factorial {
    static const int value = N * Factorial<N - 1>::value;
};

template<>
struct Factorial<0> {
    static const int value = 1;
};

int main() {
    std::cout << Factorial<5>::value << std::endl; // 120
}
// azért static értékek hogy pédányosítás nélkül 
// is hozzáférhessen a fordító
```

A C++11 óta számos új eszköz és technika érhető el a metaprogramozáshoz, például a variadic sablonok, constexpr, és a template aliasok, amelyek megkönnyítik és erőteljesebbé teszik a metaprogramozást.

Ezek a technikák együttesen lehetővé teszik a C++ számára, hogy nagyon rugalmas és hatékony kódot írjunk, amely különböző típusú adatokat és számításokat képes kezelni fordítási és futásidőben egyaránt.

# 5. Standard Template Library megvalósítása és használata: adatfolyamok, manipulátorok, generikus algoritmusok, predikátumok, függvény objektumok, generikus konténerek és iterátorok.

Az STL (Standard Template Library) a C++ programozási nyelv egyik alapvető könyvtára, amely széles körben használt adatstruktúrákat és algoritmusokat biztosít. Az STL célja, hogy újrafelhasználható, típusfüggetlen komponenseket kínáljon, amelyek lehetővé teszik a programozók számára, hogy hatékony és könnyen karbantartható kódot írjanak. Az STL három fő összetevője a következő:

1. **Konténerek (Containers):**
   
   - A konténerek olyan adattárolók, amelyek különböző típusú adatokat képesek tárolni. Az STL-ben számos konténer található, amelyek különböző adatstruktúrákat valósítanak meg, mint például:
     - `vector`: Dinamikus méretű tömb.
     - `list`: Kétirányú láncolt lista.
     - `deque`: Duplán végigjárható sor.
     - `set` és `multiset`: Rendezett halmaz és többszörösen rendezett halmaz.
     - `map` és `multimap`: Kulcs-érték párokat tartalmazó konténerek.
     - `unordered_set` és `unordered_map`: Hash-tábla alapú halmazok és asszociatív konténerek.

2. **Iterátorok (Iterators):**
   
   - Az iterátorok olyan objektumok, amelyek lehetővé teszik a konténerek elemeinek bejárását. Az iterátorok a pointerekhez hasonlóan működnek, és az STL-ben számos típusú iterátor található, mint például:
     - `input iterator`: Csak olvasási hozzáférést biztosít a konténer elemeihez.
     - `output iterator`: Csak írási hozzáférést biztosít.
     - `forward iterator`: Egyirányú bejárást tesz lehetővé.
     - `bidirectional iterator`: Kétirányú bejárást tesz lehetővé.
     - `random access iterator`: Véletlenszerű hozzáférést tesz lehetővé, hasonlóan a pointerekhez.

3. **Algoritmusok (Algorithms):**
   
   - Az algoritmusok a konténerek elemeinek feldolgozására szolgáló műveletek. Az STL-ben számos beépített algoritmus található, amelyek különböző műveleteket valósítanak meg, mint például:
     - Keresés: `find`, `binary_search`.
     - Rendezés: `sort`, `partial_sort`, `nth_element`.
     - Halmazműveletek: `merge`, `union`, `intersection`.
     - Átalakítások: `transform`, `replace`.
     - Felhalmozás: `accumulate`, `inner_product`.

Az STL használata jelentősen növelheti a kód hatékonyságát és olvashatóságát, mivel a programozók a jól bevált adatstruktúrák és algoritmusok újrafelhasználásával koncentrálhatnak a probléma specifikus részleteire, anélkül, hogy újra kellene írniuk az alapvető műveleteket.

### Predikátumok

- Másoláskor szükség lehet arra, hogy csak azokat az elemeket másoljuk át, amelyek megfelelnek bizonyos követelményeknek

- Sok algoritmusnál lehetőség van átadni egy predikátumot, amely egy elemről eldönti, hogy kell-e

- Predikátum: Olyan függvény, amely logikai értéket ad vissza

- Pl.: Kicserélni egy sorozatban azokat az elemeket, amelyek nagyobbak 15-nél
  
  **Példa:**
  
  Feltételes csere - replace_if
  
  ```cpp
  #include <algorithm>
  #include <iterator>
  #include <iostream>
  using namespace std;
  // predikátum
  bool gt15(int x) {
      return x > 15;
  }
  int main() {
      int a[] = {10, 20, 30};
      const size_t S = sizeof a / sizeof a[0];
      replace_if(a, a+S, gt15, 3);
      copy(a, a+S, ostream_iterator<int>(cout," "));
      cout << endl;
      return 0;
  } // 10 3 3
  ```

### Függvény objektumok

- Function objects

- Az előző példákban a gt15 függvény használata eléggé korlátozott
  
  - Pl. szükség lehet gt20-ra vagy gt25-re, ...
  
  - Sok függvényt kellene írni
  
  - Minden értéknek ismertnek kellene lennie fordítási időben (nem lehet pl. újabb paraméterben átadni, mert csak egy értéket fogadhatnak a predikátum függvények)

- A megoldás a függvény objektumok használata
  
  - Olyan osztály, amely megvalósítja a függvényhívás operator-t
  
  ```cpp
  #include <algorithm>
  #include <iterator>
  #include <iostream>
  using namespace std;
  // függvény objektum
  class gt_n {
      int ertek;
  public:
      gt_n(int i) : ertek(i) {}
  
      bool operator()(int x) {
          return x > ertek;
      }
  };
  int main() {
      int a[] = {10, 20, 30};
      const size_t S = sizeof a / sizeof a[0];
      int b[S];
      int* endb = remove_copy_if(a, a+S, b, gt_n(15));
      int* beginb = b;
      copy(beginb, endb, ostream_iterator<int>(cout," "));
      cout << endl;
      return 0;
  } 
  ```

### Függvény objektum adapterek

- Function object adapters

- Az STL tartalmaz egyszerű, hasznos függvény objektumokat

- Ezek együttes használatával összetett predikátumok is készíthetők

- Függvény objektum adapterek segítségével kombinálhatóak a predikátumok

- Valójában speciális függvény sablonok

### Fgv. obj. adapter példa

- Függvény objektum
  
  - greater – igaz, ha az első argumentuma > második

- Függvény objektum adapter kell, mert unáris (egy paraméterű) predikátumra van szükség
  
  - bind2nd – sablonfüggvény, használja a függvényobjektumot a második paraméteren (binder2nd objektumot készít)
  
  - binder2nd – függvényobjektum, amely eltárolja a bind2nd
    két paraméterét
  
  ```cpp
  #include <iostream>
  #include <algorithm>
  #include <functional>
  #include <iterator>
  using namespace std; 
  
  int main() {
      int a[] = {10, 20, 30};
      const int S = sizeof a / sizeof a[0];
      remove_copy_if(a, a+S, ostream_iterator<int>(cout," "), 
                      bind2nd(greater<int>(),15));
      cout << endl;
      return 0;
  } //10
  ```
  
  Ez a sor az `algorithm` könyvtár `remove_copy_if` függvényét használja:
  
  ```cpp
  remove_copy_if(a, a+S, ostream_iterator<int>(cout," ")
                  bind2nd(greater<int>(), 15));
  ```
  
  - `a, a+S`: az `a` tömb elemeinek tartományát adja meg.
  - `ostream_iterator<int>(cout," ")`: egy kimeneti iterátort hoz létre, amely a `cout`-ra ír, és szóközt tesz az elemek közé.
  - `bind2nd(greater<int>(), 15)`: ez a kifejezés egy bináris függvényt alakít át egy egyváltozós függvénnyé, amely a `greater<int>()` (nagyobb) műveletet használja és rögzíti a `15`-ös értéket a második operandusként.
  
  A `remove_copy_if` tehát minden olyan elemet, amely nagyobb, mint `15`, kihagy, és a többi elemet (10) kimásolja a `cout`-ra. Az eredmény a `10` lesz, mivel csak az nem nagyobb, mint `15`.

![](assets/2024-05-25-17-27-36-image.png)

### Adaptálható függvény objektumok

- Az STL függvény objektum adapterek feltételezik, hogy a függvény objektumok definiálják a következő típusokat
  
  - Unáris függvény objektumok esetében
    
    - argument_type
    
    - result_type
  
  - Bináris függvény objektumok esetében
    
    - first_argument_type
    
    - second_argument_type
    
    - result_type
  
  ```cpp
  template<class Arg, class Result>
  struct unary_function {            
      typedef Arg argument_type;
      typedef Result result_type;
  };
  template<class Arg1, class Arg2, class Result>
  struct binary_function {
      typedef Arg1 first_argument_type;
      typedef Arg2 second_argument_type;
      typedef Result result_type;
  };
  // fuggveny objektum
  template<class T>
  struct greater : binary_function<T, T, bool> {
      bool operator()(const T& x, const T& y) const {return (x > y);}
  };
  ```
  
  ![](assets/2024-05-25-18-00-41-image.png)

### Függvény pointer adapterek

- Sok STL algoritmus predikátumot vár paraméterül

- Ezek lehetnek
  
  - Függvény pointerek (Olyan pointerek, amelyek egy normál C++ függvényre mutatnak)
  
  - Függvény objektumok (Olyan objektumok, amelyek definiálnak egy `operator()` függvényt, így használhatók úgy, mintha függvények lennének.)

- Függvény pointerek esetében nem használhatók a függvény objektumokhoz készített adapterek
  
  - mert feltételezik a megfelelő típusdefiníciók meglétét
  
  - Másszóval, az adapterek, mint például a `binder2nd`, feltételezik, hogy a predikátum típus tartalmaz bizonyos típusdefiníciókat (pl. `first_argument_type`, `second_argument_type`, `result_type`), amelyeket a `unary_function` és `binary_function` sablonok biztosítanak.

- ptr_fun() – adapter átalakítja a függvény pointereket függvény objektumokká

### Manipulátorok

Az STL (Standard Template Library) manipulátorai olyan függvények vagy objektumok, amelyek a stream-ekkel (például `std::cout`, `std::cin`) való munka során használhatók a formázás és egyéb műveletek elvégzésére. Ezek a manipulátorok megkönnyítik az adatbevitelt és -kiírást, valamint a formázási beállítások módosítását a stream-eken keresztül.

### Alapvető manipulátorok az STL-ben

#### 1. Formázási manipulátorok

- **std::endl**: Újsor karaktert ír ki és üríti a stream-et.
  
  ```cpp
  std::cout << "Hello, World!" << std::endl;
  ```

- **std::setw(n)**: Beállítja a következő kiírandó adat szélességét n karakterre. Ezt a manipulátort az `<iomanip>` fejléccel kell használni.
  
  ```cpp
  #include <iomanip>
  std::cout << std::setw(10) << 123 << std::endl;
  ```

- **std::setfill(c)**: Beállítja a kitöltő karaktert (alapértelmezett a szóköz).
  
  ```cpp
  std::cout << std::setfill('*') << std::setw(10) << 123 << std::endl;
  ```

- **std::setprecision(n)**: Beállítja a lebegőpontos számok pontosságát n számjegyre.
  
  ```cpp
  #include <iomanip>
  std::cout << std::setprecision(4) << 3.14159265 << std::endl;
  ```

#### 2. Állapot manipulátorok

- **std::fixed**: Beállítja a lebegőpontos számok fixpontos formátumát.
  
  ```cpp
  std::cout << std::fixed << std::setprecision(2) << 3.14159265 << std::endl;
  ```

- **std::scientific**: Beállítja a lebegőpontos számok tudományos (exponenciális) formátumát.
  
  ```cpp
  std::cout << std::scientific << 123.45 << std::endl;
  ```

- **std::boolalpha**: Beállítja, hogy a logikai értékeket szöveges formában (true/false) írja ki.
  
  ```cpp
  std::cout << std::boolalpha << true << std::endl;
  ```

- **std::noboolalpha**: Visszaállítja a logikai értékek numerikus kiírását (1/0).
  
  ```cpp
  std::cout << std::noboolalpha << true << std::endl;
  ```

#### 3. Bit- és számrendszer manipulátorok

- **std::hex**: Hexadecimális formátumra állítja a számok kiírását.
  
  ```cpp
  std::cout << std::hex << 255 << std::endl; // kiírja: ff
  ```

- **std::oct**: Oktális formátumra állítja a számok kiírását.
  
  ```cpp
  std::cout << std::oct << 255 << std::endl; // kiírja: 377
  ```

- **std::dec**: Decimális formátumra állítja a számok kiírását.
  
  ```cpp
  std::cout << std::dec << 255 << std::endl; // kiírja: 255
  ```

### Példa a manipulátorok használatára

Az alábbi példa bemutatja néhány gyakori manipulátor használatát:

```cpp
#include <iostream>
#include <iomanip>

int main() {
    int num = 255;
    double pi = 3.14159265;

    // Alapértelmezett kiírás
    std::cout << "Alapértelmezett: " << num << ", " << pi << std::endl;

    // Hexadecimális kiírás
    std::cout << "Hexadecimális: " << std::hex << num << std::endl;

    // Oktális kiírás
    std::cout << "Oktális: " << std::oct << num << std::endl;

    // Visszaállítás decimálisra
    std::cout << std::dec;

    // Pontosság beállítása
    std::cout << "Pi pontossággal (5 tizedesjegy): " << std::setprecision(5) << pi << std::endl;

    // Szélesség és kitöltő karakter beállítása
    std::cout << "Szélesség 10, kitöltő '*': " << std::setfill('*') << std::setw(10) << num << std::endl;

    // Boolalpha használata
    std::cout << "Boolalpha: " << std::boolalpha << true << ", " << false << std::endl;

    return 0;
}
```

Az STL manipulátorai rendkívül hasznosak a stream-ek formázásában és kezelésében. Lehetővé teszik az adatok kiírásának és beolvasásának finomhangolását, legyen szó szélesség, pontosság, formátum vagy egyéb beállításokról. Ezek a manipulátorok megkönnyítik a kód olvashatóságát és karbantarthatóságát, mivel világosan jelzik, hogyan kell az adatokat kezelni a stream-eken keresztül.

![](assets/2024-05-25-18-17-43-image.png)

![](assets/2024-05-25-18-18-00-image.png)

### Generikus konténerek

Az STL (Standard Template Library) generikus konténerei a C++ egyik legerősebb és leggyakrabban használt eszközei, amelyek lehetővé teszik különböző típusú elemek tárolását és kezelését egységes módon. A generikus konténerek sablonként vannak megvalósítva, így rugalmasan alkalmazhatók bármilyen adattípusra. Az STL konténerei több különböző típusú tárolási és hozzáférési modellt kínálnak.

### Főbb konténertípusok

1. **Szekvenciális konténerek**:
   Ezek a konténerek az elemeket egy adott sorrendben tárolják.
   
   - **std::vector**:
     Dinamikus tömb, amelynek mérete futásidőben változtatható. Gyors hozzáférést biztosít az elemekhez indexelés segítségével.
     
     ```cpp
     #include <vector>
     std::vector<int> vec = {1, 2, 3, 4, 5};
     vec.push_back(6);
     ```
   
   - **std::deque**:
     Kétszeresen kapcsolt lista és tömb kombinációja, amely lehetővé teszi az elemek hozzáadását és eltávolítását mindkét végéről.
     
     ```cpp
     #include <deque>
     std::deque<int> deq = {1, 2, 3, 4, 5};
     deq.push_front(0);
     deq.push_back(6);
     ```
   
   - **std::list**:
     Duplán láncolt lista, amely hatékony beszúrást és törlést biztosít bárhol a listában, de lassú hozzáférést index alapján.
     
     ```cpp
     #include <list>
     std::list<int> lst = {1, 2, 3, 4, 5};
     lst.push_back(6);
     lst.push_front(0);
     ```
   
   - **std::array**:
     Fix méretű tömb, amely futásidőben nem változtatható.
     
     ```cpp
     #include <array>
     std::array<int, 5> arr = {1, 2, 3, 4, 5};
     ```

2. **Asszociatív konténerek**:
   Ezek a konténerek kulcs-érték párok alapján tárolják az elemeket és gyors keresést biztosítanak.
   
   - **std::set**:
     Egyedi elemek rendezetlen halmaza, amelyben minden elem csak egyszer szerepelhet.
     
     ```cpp
     #include <set>
     std::set<int> myset = {1, 2, 3, 4, 5};
     myset.insert(6);
     ```
   
   - **std::map**:
     Kulcs-érték párokat tartalmazó rendezetlen halmaz, ahol minden kulcs egyedi.
     
     ```cpp
     #include <map>
     std::map<int, std::string> mymap;
     mymap[1] = "one";
     mymap[2] = "two";
     ```
   
   - **std::multiset**:
     Egyedi elemek rendezett halmaza, amelyben az elemek többször is előfordulhatnak.
     
     ```cpp
     #include <set>
     std::multiset<int> mymultiset = {1, 2, 2, 3, 4, 5};
     ```
   
   - **std::multimap**:
     Kulcs-érték párokat tartalmazó rendezetlen halmaz, ahol a kulcsok többször is előfordulhatnak.
     
     ```cpp
     #include <map>
     std::multimap<int, std::string> mymultimap;
     mymultimap.insert({1, "one"});
     mymultimap.insert({1, "uno"});
     ```

3. **Unordered konténerek**:
   Ezek a konténerek hash tábla alapúak és gyors keresést biztosítanak, de az elemek sorrendje nem meghatározott.
   
   - **std::unordered_set**:
     Egyedi elemek rendezetlen halmaza, amely hash táblát használ.
     
     ```cpp
     #include <unordered_set>
     std::unordered_set<int> myunorderedset = {1, 2, 3, 4, 5};
     myunorderedset.insert(6);
     ```
   
   - **std::unordered_map**:
     Kulcs-érték párokat tartalmazó rendezetlen halmaz, amely hash táblát használ.
     
     ```cpp
     #include <unordered_map>
     std::unordered_map<int, std::string> myunorderedmap;
     myunorderedmap[1] = "one";
     myunorderedmap[2] = "two";
     ```
   
   - **std::unordered_multiset**:
     Egyedi elemek rendezetlen halmaza, ahol az elemek többször is előfordulhatnak és hash táblát használ.
     
     ```cpp
     #include <unordered_set>
     std::unordered_multiset<int> myunorderedmultiset = {1, 2, 2, 3, 4, 5};
     ```
   
   - **std::unordered_multimap**:
     Kulcs-érték párokat tartalmazó rendezetlen halmaz, ahol a kulcsok többször is előfordulhatnak és hash táblát használ.
     
     ```cpp
     #include <unordered_map>
     std::unordered_multimap<int, std::string> myunorderedmultimap;
     myunorderedmultimap.insert({1, "one"});
     myunorderedmultimap.insert({1, "uno"});
     ```

### Konténerek használata

A generikus konténerek használatának fő előnyei:

- **Típusbiztonság**: A konténerek típusbiztosak, így a kompiláció során ellenőrzik az adattípusokat.
- **Újrahasznosíthatóság**: A konténerek sablonként vannak megvalósítva, így újrahasznosíthatók különböző adattípusokkal.
- **Hatékonyság**: Az STL konténerek hatékony adatkezelést biztosítanak, beleértve a gyors hozzáférést, beszúrást és törlést.

### Példa a különböző konténerek használatára

```cpp
#include <iostream>
#include <vector>
#include <list>
#include <set>
#include <map>
#include <unordered_set>
#include <unordered_map>

int main() {
    // Vector
    std::vector<int> vec = {1, 2, 3, 4, 5};
    vec.push_back(6);
    for (int v : vec) std::cout << v << " ";
    std::cout << std::endl;

    // List
    std::list<int> lst = {1, 2, 3, 4, 5};
    lst.push_back(6);
    lst.push_front(0);
    for (int l : lst) std::cout << l << " ";
    std::cout << std::endl;

    // Set
    std::set<int> myset = {1, 2, 3, 4, 5};
    myset.insert(6);
    for (int s : myset) std::cout << s << " ";
    std::cout << std::endl;

    // Map
    std::map<int, std::string> mymap;
    mymap[1] = "one";
    mymap[2] = "two";
    for (const auto& p : mymap) std::cout << p.first << " -> " << p.second << " ";
    std::cout << std::endl;

    // Unordered Set
    std::unordered_set<int> myunorderedset = {1, 2, 3, 4, 5};
    myunorderedset.insert(6);
    for (int us : myunorderedset) std::cout << us << " ";
    std::cout << std::endl;

    // Unordered Map
    std::unordered_map<int, std::string> myunorderedmap;
    myunorderedmap[1] = "one";
    myunorderedmap[2] = "two";
    for (const auto& up : myunorderedmap) std::cout << up.first << " -> " << up.second << " ";
    std::cout << std::endl;

    return 0;
}
```

### Iterátorok

Az STL (Standard Template Library) iterátorai olyan objektumok, amelyek lehetővé teszik az elemek bejárását és manipulálását különböző konténerekben egységes módon. Az iterátorok az STL alapvető komponensei, mivel azok segítségével az algoritmusok függetlenek maradnak a konténer konkrét típusától.

### Iterátorok típusai

Az iterátorok több különböző kategóriába sorolhatók, mindegyik saját jellemzőkkel és használati módokkal rendelkezik.

1. **Input iterátorok**
   
   - Egyszeri olvasást tesznek lehetővé az elemekről.
   - Példa: bejárás egy bemeneti adatfolyam (input stream) esetén.
   - Előírás: csak előre léptethetők, és nem lehet őket másolni (nem feltétlenül).

2. **Output iterátorok**
   
   - Egyszeri írást tesznek lehetővé az elemekre.
   - Példa: írás egy kimeneti adatfolyam (output stream) esetén.
   - Előírás: csak előre léptethetők, és nem lehet őket másolni (nem feltétlenül).

3. **Forward iterátorok**
   
   - Kombinálják az input és output iterátorok tulajdonságait.
   - Lehetővé teszik az elemek többszöri olvasását és írását.
   - Példa: egyszerű összefűzött lista (singly linked list).
   - Előírás: másolhatók és több lépésben előre léptethetők.

4. **Bidirectional iterátorok**
   
   - Lehetővé teszik az előre és hátra léptetést.
   - Példa: kétszeresen összefűzött lista (doubly linked list).
   - Előírás: előre és hátra is léptethetők.

5. **Random access iterátorok**
   
   - Lehetővé teszik a véletlenszerű hozzáférést az elemekhez.
   - Példa: dinamikus tömb (vector).
   - Előírás: minden iterátor művelet támogatott, beleértve az indexelést és az előre-hátra léptetést.

### Iterátorok használata

Az iterátorok használata az STL-ben alapvető fontosságú a konténerek elemeinek bejárásához és manipulálásához. Az iterátorokkal végzett műveletek szintaktikailag hasonlóak a pointerekkel végzett műveletekhez.

#### Példa: std::vector iterátor használata

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> vec = {1, 2, 3, 4, 5};

    // Iterátor használata az elemek bejárásához
    for (std::vector<int>::iterator it = vec.begin(); it != vec.end(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

#### Példa: std::list iterátor használata

```cpp
#include <iostream>
#include <list>

int main() {
    std::list<int> lst = {1, 2, 3, 4, 5};

    // Iterátor használata az elemek bejárásához
    for (std::list<int>::iterator it = lst.begin(); it != lst.end(); ++it) {
        std::cout << *it << " ";
    }
    std::cout << std::endl;

    return 0;
}
```

### Iterátorok műveletei

Az iterátorok több alapvető műveletet támogatnak, amelyek segítségével bejárhatók és manipulálhatók a konténerek elemei:

- **Dereferálás**: Az iterátor által mutatott elem elérése.
  
  ```cpp
  *it = 10; // Az iterátor által mutatott elem értékének beállítása 10-re
  ```

- **Inkrementálás**: Az iterátor előre léptetése.
  
  ```cpp
  ++it; // Az iterátor előre léptetése a következő elemre
  ```

- **Dekrementálás**: Az iterátor visszaléptetése (bidirectional és random access iterátorok esetén).
  
  ```cpp
  --it; // Az iterátor visszaléptetése az előző elemre
  ```

- **Összehasonlítás**: Az iterátorok összehasonlítása (pl. egyenlőség).
  
  ```cpp
  if (it == vec.end()) { /* ... */ }
  ```

- **Indexelés**: Véletlenszerű hozzáférés az elemekhez (random access iterátorok esetén).
  
  ```cpp
  it += 3; // Az iterátor előreléptetése három elemmel
  int val = it[2]; // Az iterátortól számított második elem elérése
  ```

### Speciális iterátorok

Az STL tartalmaz néhány speciális iterátort is, amelyek különleges feladatokat látnak el:

- **std::istream_iterator**: Bemeneti adatfolyam iterátor.
  
  ```cpp
  std::istream_iterator<int> in_iter(std::cin);
  ```

- **std::ostream_iterator**: Kimeneti adatfolyam iterátor.
  
  ```cpp
  std::ostream_iterator<int> out_iter(std::cout, " ");
  ```

- **std::reverse_iterator**: Fordított iterátor, amely az elemeket fordított sorrendben járja be.
  
  ```cpp
  std::reverse_iterator<std::vector<int>::iterator> r_it = vec.rbegin();
  ```

- **std::back_insert_iterator**: Beszúró iterátor, amely elemeket szúr be egy konténer végére.
  
  ```cpp
  std::back_insert_iterator<std::vector<int>> back_it(vec);
  ```

- **std::front_insert_iterator**: Beszúró iterátor, amely elemeket szúr be egy konténer elejére.
  
  ```cpp
  std::front_insert_iterator<std::list<int>> front_it(lst);
  ```

- **std::insert_iterator**: Beszúró iterátor, amely elemeket szúr be egy konténer adott helyére.
  
  ```cpp
  std::insert_iterator<std::set<int>> insert_it(myset, myset.begin());
  ```

### Összefoglalva

Az iterátorok az STL egyik legfontosabb komponensei, amelyek lehetővé teszik a konténerek elemeinek egységes kezelését és bejárását. Az iterátorok különböző típusai és műveletei rugalmasságot biztosítanak a programozóknak, hogy hatékonyan és biztonságosan dolgozhassanak különböző adatstruktúrákkal. Az iterátorok használata az STL algoritmusokkal együtt erőteljes eszközt biztosít a C++ programozásban.