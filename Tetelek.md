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

# Képfeldolgozás haladóknak

# 7. Morfológiai műveletek többszintű képekre; Vázkijelölés: távolság-transzformáció, vékonyítás, Voronoi-váz.

## Morfológiai műveletek kétszintű képekre

**<u>Matematikai morfológia:</u>** eszköztár a képfeldolgozáshoz és a képanalízishez, halmazelméleti módszer geometriai struktúrák kvantitatív leírásához. A módszer kifejlesztői G. Matheron és J. Serra.

A morfológiai műveletek bemenete egy ponthalmaz (pl. egy kép fekete pontjainak halmaza) és egy elemi minta, a szerkesztőelem (structuring element).

A szerkesztőelem szerepe és használata a konvolúciós
maszkéhoz (convolution kerner) hasonlítható.

![](assets/2024-05-25-22-19-20-image.png)

Segédműveletek: tükrözés és eltolás

![](assets/2024-05-25-22-24-32-image.png)

![](assets/2024-05-25-22-24-50-image.png)

![](assets/2024-05-25-22-29-04-image.png)

## Morfológiai műveletek többszintű képekre

### Dilatáció Többszintű Képekre Lapostetejű Szerkesztőelemmel

#### Definíció

A dilatáció egy olyan morfológiai művelet, amelynek célja az objektumok növelése a képen. Szürkeárnyalatos képeknél a dilatáció során minden pixel értékét a környezetében lévő pixelek maximumával helyettesítjük, egy lapostetejű szerkesztőelem segítségével. A lapostetejű szerkesztőelem minden pontja azonos súllyal rendelkezik, azaz nincs belső struktúrája vagy magassága.

#### Működési Elv

A dilatáció során a lapostetejű szerkesztőelem meghatározott területen belül minden egyes pixel környezetében keressük a maximum értéket, és ezzel helyettesítjük az adott pixel értékét.

#### Matematikai Leírás

Legyen $ I(x, y) $ a bemeneti szürkeárnyalatos kép, és $ B $ a lapostetejű szerkesztőelem. A dilatáció $ I $ képen $ B $ szerkesztőelemmel az alábbi módon történik:

$ (I \oplus B)(x, y) = \max_{(s, t) \in B} \{ I(x-s, y-t) \} $

Ez azt jelenti, hogy minden $ (x, y) $ pontban a kimeneti kép értéke a bemeneti kép azon pontjainak maximuma lesz, amelyek a szerkesztőelem $ B $ által meghatározott területen belül vannak.

#### Példa

Tegyük fel, hogy van egy szürkeárnyalatos kép, ahol az egyes pixelek értékei 0 és 255 között változnak (8 bites képek). Ha a szerkesztőelem egy 3x3-as négyzet, akkor a dilatáció során minden egyes pixel értéke a 3x3-as ablakban lévő pixelek maximum értékével lesz helyettesítve.

1. **Bemeneti Kép:**
   
   ```
   50 50 50
   50 100 50
   50 50 50
   ```

2. **Szerkesztőelem:** 3x3-as négyzet

3. **Dilatáció Után:**
   
   ```
   100 100 100
   100 100 100
   100 100 100
   ```

A középső pixel értéke 100, amely a maximum a 3x3-as ablakban, és ez a maximum érték kiterjed a környező pixelekre is.

#### Alkalmazások

1. **Lyukak Kitöltése:** A dilatáció kitöltheti a kis lyukakat és réseket az objektumokban.
2. **Zaj Eltávolítása:** A kis zajos pontokat eltünteti azáltal, hogy a környező világosabb értékekkel helyettesíti őket.
3. **Objektumok Méretének Növelése:** Az objektumok méretének növelése és kiterjesztése a képen.

#### Vizualizáció

A dilatáció eredményeként a kép világosabb területei kiterjednek, és az objektumok szélei eltolódnak. A kép simább lesz, és a kis lyukak kitöltődnek.

### Példák és Illusztrációk

1. **Bemeneti Kép:** Egy szürkeárnyalatos kép, ahol különböző intenzitású területek vannak.
2. **Szerkesztőelem:** Egy 3x3-as vagy 5x5-ös négyzet vagy más alakzat.
3. **Dilatált Kép:** A dilatáció után a kép világosabb területei kiterjednek, és a sötétebb területek csökkennek.

### Alkalmazás Képfeldolgozási Feladatokban

1. **Előkészítő Lépés:** A dilatációt gyakran használják előkészítő lépésként más képfeldolgozási feladatok előtt, például az objektumok detektálása és azonosítása.
2. **Képszegmentálás:** A dilatáció segíthet a képszegmentálásban az objektumok jobb elkülönítésében és az egymástól távol lévő objektumok kiemelésében.
3. **Formaelemzés:** Az objektumok alakjának és méretének elemzésében segít, különösen, ha fontos a lyukak és zajok eltávolítása.

### Összefoglaló

A dilatáció többszintű (szürkeárnyalatos) képeknél lapostetejű szerkesztőelemmel egy hatékony művelet, amely kiterjeszti a világosabb területeket és eltávolítja a kis lyukakat és zajokat. Ez a technika különösen hasznos a képfeldolgozásban, ahol fontos az objektumok simítása, kiterjesztése és a zaj eltávolítása.

![](assets/2024-05-26-01-37-43-image.png)

![](assets/2024-05-26-01-38-00-image.png)

### Erózió Többszintű Képekre Lapostetejű Szerkesztőelemmel

#### Definíció

Az erózió egy olyan morfológiai művelet, amelynek célja az objektumok csökkentése a képen. Szürkeárnyalatos képeknél az erózió során minden pixel értékét a környezetében lévő pixelek minimumával helyettesítjük, egy lapostetejű szerkesztőelem segítségével. A lapostetejű szerkesztőelem minden pontja azonos súllyal rendelkezik, azaz nincs belső struktúrája vagy magassága.

#### Működési Elv

Az erózió során a lapostetejű szerkesztőelem meghatározott területen belül minden egyes pixel környezetében keressük a minimum értéket, és ezzel helyettesítjük az adott pixel értékét.

#### Matematikai Leírás

Legyen $ I(x, y) $ a bemeneti szürkeárnyalatos kép, és $ B $ a lapostetejű szerkesztőelem. Az erózió $ I $ képen $ B $ szerkesztőelemmel az alábbi módon történik:

$ (I \ominus B)(x, y) = \min_{(s, t) \in B} \{ I(x+s, y+t) \} $

Ez azt jelenti, hogy minden $ (x, y) $ pontban a kimeneti kép értéke a bemeneti kép azon pontjainak minimuma lesz, amelyek a szerkesztőelem $ B $ által meghatározott területen belül vannak.

#### Példa

Tegyük fel, hogy van egy szürkeárnyalatos kép, ahol az egyes pixelek értékei 0 és 255 között változnak (8 bites képek). Ha a szerkesztőelem egy 3x3-as négyzet, akkor az erózió során minden egyes pixel értéke a 3x3-as ablakban lévő pixelek minimum értékével lesz helyettesítve.

1. **Bemeneti Kép:**
   
   ```
   100 100 100
   100 150 100
   100 100 100
   ```

2. **Szerkesztőelem:** 3x3-as négyzet

3. **Erózió Után:**
   
   ```
   100 100 100
   100 100 100
   100 100 100
   ```

A középső pixel értéke 150, de a 3x3-as ablakban a minimum érték 100, így minden pixel értéke 100 lesz az erózió után.

#### Alkalmazások

1. **Zaj Eltávolítása:** Az erózió eltávolíthatja a kis világos zajos pontokat a képből.
2. **Struktúrák Finomítása:** Az objektumok széleinek finomítása és a kis kiálló részek eltávolítása.
3. **Objektumok Méretének Csökkentése:** Az objektumok méretének csökkentése és a finom részletek eltávolítása.

#### Vizualizáció

Az erózió eredményeként a kép sötétebb területei kiterjednek, és az objektumok szélei visszahúzódnak. A kép simább lesz, és a kis világos zajok eltűnnek.

### Példák és Illusztrációk

1. **Bemeneti Kép:** Egy szürkeárnyalatos kép, ahol különböző intenzitású területek vannak.
2. **Szerkesztőelem:** Egy 3x3-as vagy 5x5-ös négyzet vagy más alakzat.
3. **Erodált Kép:** Az erózió után a kép sötétebb területei kiterjednek, és a világosabb területek csökkennek.

### Alkalmazás Képfeldolgozási Feladatokban

1. **Előkészítő Lépés:** Az eróziót gyakran használják előkészítő lépésként más képfeldolgozási feladatok előtt, például az objektumok detektálása és azonosítása.
2. **Képszegmentálás:** Az erózió segíthet a képszegmentálásban az objektumok jobb elkülönítésében és az egymástól távol lévő objektumok kiemelésében.
3. **Formaelemzés:** Az objektumok alakjának és méretének elemzésében segít, különösen, ha fontos a zajok eltávolítása és a struktúrák finomítása.

### Összefoglaló

Az erózió többszintű (szürkeárnyalatos) képeknél lapostetejű szerkesztőelemmel egy hatékony művelet, amely kiterjeszti a sötétebb területeket és eltávolítja a kis világos zajokat. Ez a technika különösen hasznos a képfeldolgozásban, ahol fontos az objektumok finomítása, csökkentése és a zaj eltávolítása.

### Dilatáció Többszintű Képekre Nem Lapostetejű Szerkesztőelemmel

- Ha a szerkesztőelem továbbra is csak egy ponthalmaz, tartomány, akkor
  lapostetejű (flat topped) szerkesztőelemről és operátorokról beszélünk

- Ha a szerkesztőelemhez tartozó pontoknak értéke, intenzitása is van (többszintű
  miniképeknek tekinthetők), akkor a szerkesztőelem és a művelet nem-lapostetejű
  (non-flat topped). Megjegyezzük, hogy a lapostetejű szerkesztőelem egy olyan
  nem-lapostetejűnek tekinthető, ahol a szerkesztőelem valamennyi pontjának 0 az értéke.

#### Definíció

A dilatáció többszintű képekre nem lapostetejű szerkesztőelemmel egy olyan morfológiai művelet, amelynek célja az objektumok kiterjesztése a képen. A nem lapostetejű szerkesztőelem különböző értékekkel rendelkezik, amelyek hozzáadódnak a kép pixeleinek értékeihez, lehetővé téve a finomabb és specifikusabb morfológiai műveleteket.

#### Működési Elv

A dilatáció során a nem lapostetejű szerkesztőelem meghatározott területen belül minden egyes pixel környezetében keressük az összeadott értékek maximumát (a pixel értéke és a szerkesztőelem értéke), és ezzel helyettesítjük az adott pixel értékét.

#### Matematikai Leírás

Legyen $ I(x, y) $ a bemeneti szürkeárnyalatos kép, és $ B(s, t) $ a nem lapostetejű szerkesztőelem. A dilatáció $ I $ képen $ B $ szerkesztőelemmel az alábbi módon történik:

$ (I \oplus B)(x, y) = \max_{(s, t) \in B} \{ I(x-s, y-t) + B(s, t) \} $

Ez azt jelenti, hogy minden $ (x, y) $ pontban a kimeneti kép értéke a bemeneti kép és a szerkesztőelem azon pontjainak összegének maximuma lesz, amelyek a szerkesztőelem $ B $ által meghatározott területen belül vannak.

![](assets/2024-05-26-02-14-16-image.png)

### Erózió Többszintű Képekre Nem Lapostetejű Szerkesztőelemmel

#### Definíció

Az erózió többszintű képekre nem lapostetejű szerkesztőelemmel egy olyan morfológiai művelet, amelynek célja az objektumok csökkentése és a finom struktúrák eltávolítása a képen. A nem lapostetejű szerkesztőelem különböző értékekkel rendelkezik, amelyek kivonódnak a kép pixeleinek értékeiből, lehetővé téve a finomabb és specifikusabb morfológiai műveleteket.

#### Működési Elv

Az erózió során a nem lapostetejű szerkesztőelem meghatározott területen belül minden egyes pixel környezetében keressük az összeadott értékek minimumát (a pixel értéke mínusz a szerkesztőelem értéke), és ezzel helyettesítjük az adott pixel értékét.

#### Matematikai Leírás

Legyen $ I(x, y) $ a bemeneti szürkeárnyalatos kép, és $ B(s, t) $ a nem lapostetejű szerkesztőelem. Az erózió $ I $ képen $ B $ szerkesztőelemmel az alábbi módon történik:

$ (I \ominus B)(x, y) = \min_{(s, t) \in B} \{ I(x+s, y+t) - B(s, t) \} $

Ez azt jelenti, hogy minden $ (x, y) $ pontban a kimeneti kép értéke a bemeneti kép és a szerkesztőelem azon pontjainak különbségének minimuma lesz, amelyek a szerkesztőelem $ B $ által meghatározott területen belül vannak.

#### Példa

Tegyük fel, hogy van egy szürkeárnyalatos kép, ahol az egyes pixelek értékei 0 és 255 között változnak (8 bites képek). Ha a szerkesztőelem egy 3x3-as négyzet, amely különböző értékekkel rendelkezik, akkor az erózió során minden egyes pixel értéke a 3x3-as ablakban lévő pixelek és a szerkesztőelem értékeinek minimum különbségével lesz helyettesítve.

1. **Bemeneti Kép:**
   
   ```
   150 150 150
   150 200 150
   150 150 150
   ```

2. **Szerkesztőelem (3x3-as négyzet, nem lapostetejű):**
   
   ```
   0 0 0
   0 10 0
   0 0 0
   ```

3. **Erózió Után:**
   
   ```
   140 140 140
   140 140 140
   140 140 140
   ```

A középső pixel értéke 200, amelyből kivonjuk a szerkesztőelem középső értékét 10, így a minimális érték 140 lesz, és ez az érték kiterjed a környező pixelekre is.

#### Alkalmazások

1. **Finom Struktúrák Eltávolítása:** Nem lapostetejű szerkesztőelemekkel finomabb és specifikusabb struktúrák eltávolíthatók.
2. **Zaj Eltávolítása:** Az erózió eltávolíthatja a kis világos zajos pontokat a képből.
3. **Objektumok Méretének Csökkentése:** Az objektumok méretének csökkentése és a finom részletek eltávolítása.
4. **Struktúrák Finomítása:** Az objektumok széleinek finomítása és a kis kiálló részek eltávolítása.

#### Vizualizáció

Az erózió eredményeként a kép sötétebb területei kiterjednek, és az objektumok szélei visszahúzódnak. A kép simább lesz, és a kis világos zajok eltűnnek. A nem lapostetejű szerkesztőelem különböző értékei miatt az erózió finomabban és specifikusabban történik.

### Példák és Illusztrációk

1. **Bemeneti Kép:** Egy szürkeárnyalatos kép, ahol különböző intenzitású területek vannak.
2. **Szerkesztőelem:** Egy 3x3-as vagy 5x5-ös négyzet különböző értékekkel.
3. **Erodált Kép:** Az erózió után a kép sötétebb területei kiterjednek, és a világosabb területek csökkennek, a szerkesztőelem értékeinek megfelelően.

### Alkalmazás Képfeldolgozási Feladatokban

1. **Előkészítő Lépés:** Az eróziót gyakran használják előkészítő lépésként más képfeldolgozási feladatok előtt, például az objektumok detektálása és azonosítása.
2. **Képszegmentálás:** Az erózió segíthet a képszegmentálásban az objektumok jobb elkülönítésében és az egymástól távol lévő objektumok kiemelésében.
3. **Formaelemzés:** Az objektumok alakjának és méretének elemzésében segít, különösen, ha fontos a zajok eltávolítása és a struktúrák finomítása.

### Összefoglaló

Az erózió többszintű (szürkeárnyalatos) képeknél nem lapostetejű szerkesztőelemmel egy hatékony művelet, amely kiterjeszti a sötétebb területeket és finomabban eltávolítja a kis világos zajokat. Ez a technika különösen hasznos a képfeldolgozásban, ahol fontos az objektumok finomítása, csökkentése és a zaj eltávolítása, a szerkesztőelem különböző értékeinek segítségével.

![](assets/2024-05-26-02-14-29-image.png)

### Nyitás (Opening)

#### Definíció

A nyitás egy összetett morfológiai művelet, amely az erózió és dilatáció egymást követő alkalmazásából áll. A nyitás célja az objektumok simítása, a kis zajok eltávolítása, valamint a vékony nyúlványok és szűk szorosok eltávolítása az objektumokból.

#### Működési Elv

A nyitás egy bináris vagy szürkeárnyalatos képen az alábbi lépésekből áll:

1. **Erózió (Erosion):** Először alkalmazunk egy eróziót a bemeneti képre, amely eltávolítja az objektumok külső rétegeit.
2. **Dilatáció (Dilation):** Az eróziót követően dilatációt alkalmazunk a megmaradt objektumokra, hogy visszaállítsuk az objektumok méretét az eredeti állapotukhoz hasonlóan, de a kis zajok és nyúlványok nélkül.

#### Matematikai Leírás

Legyen $ A $ a bemeneti halmaz (az objektum pixelei) és $ B $ a szerkesztőelem. A nyitás $ A $ halmazon $ B $ szerkesztőelemmel az alábbi módon történik:
$ A \circ B = (A \ominus B) \oplus B $
ahol $ \ominus $ jelöli az eróziót és $ \oplus $ a dilatációt.

#### Példa

Tegyük fel, hogy van egy bináris kép, ahol az objektumok fekete pixelek. Ha a szerkesztőelem egy 3x3-as négyzet, akkor a nyitás során:

1. **Erózió:** A 3x3-as négyzet szerkesztőelem minden olyan pixelt eltávolít, amely nem illeszkedik teljesen a fekete pixelekre. Az objektumok szélei összehúzódnak, és a kis zajok eltűnnek.
2. **Dilatáció:** A maradék objektumokat kibővítjük ugyanazzal a 3x3-as négyzettel, hogy visszaállítsuk az objektumok méretét, de a zajok és vékony nyúlványok nélkül.

#### Alkalmazások

1. **Zaj Eltávolítása:** A nyitás eltávolítja a kis zajokat és elszigetelt pontokat a képből.
2. **Határok Simítása:** Az objektumok határainak simítása, ami segít az objektumok jobb elkülönítésében.
3. **Vékony Nyúlványok Eltávolítása:** A vékony nyúlványok és szűk szorosok eltávolítása, amelyek nem részei az objektumok fő struktúrájának.

### Zárás (Closing)

#### Definíció

A zárás egy összetett morfológiai művelet, amely a dilatáció és erózió egymást követő alkalmazásából áll. A zárás célja az objektumok simítása, a kis lyukak és rések kitöltése, valamint az objektumok összekapcsolása.

#### Működési Elv

A zárás egy bináris vagy szürkeárnyalatos képen az alábbi lépésekből áll:

1. **Dilatáció (Dilation):** Először alkalmazunk egy dilatációt a bemeneti képre, amely kibővíti az objektumokat és kitölti a kis lyukakat.
2. **Erózió (Erosion):** A dilatációt követően eróziót alkalmazunk a kibővített objektumokra, hogy visszaállítsuk az objektumok méretét az eredeti állapotukhoz hasonlóan, de a kitöltött lyukakkal és összekapcsolt részekkel.

#### Matematikai Leírás

Legyen $ A $ a bemeneti halmaz (az objektum pixelei) és $ B $ a szerkesztőelem. A zárás $ A $ halmazon $ B $ szerkesztőelemmel az alábbi módon történik:
$ A \bullet B = (A \oplus B) \ominus B $
ahol $ \oplus $ jelöli a dilatációt és $ \ominus $ az eróziót.

#### Példa

Tegyük fel, hogy van egy bináris kép, ahol az objektumok fekete pixelek. Ha a szerkesztőelem egy 3x3-as négyzet, akkor a zárás során:

1. **Dilatáció:** A 3x3-as négyzet szerkesztőelem minden fekete pixel köré egy 3x3-as négyzetet helyez, kibővítve az objektumokat és kitöltve a kis lyukakat.
2. **Erózió:** A kibővített objektumokat visszacsökkentjük az erózióval, hogy az objektumok mérete visszaálljon az eredeti állapotukhoz hasonlóan, de a kitöltött lyukakkal és összekapcsolt részekkel.

#### Alkalmazások

1. **Lyukak Kitöltése:** A zárás kitölti az objektumokon belüli kis lyukakat és rések.
2. **Határok Simítása:** Az objektumok határainak simítása, ami segít az objektumok jobb elkülönítésében.
3. **Objektumok Összekapcsolása:** A zárás összekapcsolja a közeli objektumokat, amelyek között kis távolságok vagy rések vannak.

### Morfológiai Szűrés (Morphological Filtering)

#### Definíció

A morfológiai szűrés olyan technika, amely a morfológiai műveletek (például nyitás és zárás) kombinációját használja a képek zajcsökkentésére és az objektumok struktúrájának kiemelésére. A morfológiai szűrés célja a kép tartalmának javítása, hogy a fontos struktúrák jobban felismerhetők és elemezhetők legyenek.

#### Működési Elv

A morfológiai szűrés általában a nyitás és zárás egymás utáni alkalmazásából áll:

1. **Nyitás (Opening):** Az erózió és dilatáció egymást követő alkalmazásával a nyitás eltávolítja a kis zajokat és simítja az objektumok határait.
2. **Zárás (Closing):** A dilatáció és erózió egymást követő alkalmazásával a zárás kitölti a kis lyukakat és réseket, valamint összekapcsolja a közeli objektumokat.

#### Matematikai Leírás

Legyen $ A $ a bemeneti halmaz (az objektum pixelei) és $ B $ a szerkesztőelem. A morfológiai szűrés során az alábbi műveleteket alkalmazzuk:

1. **Nyitás (Opening):**
   $ A \circ B = (A \ominus B) \oplus B $

2. **Zárás (Closing):**
   $ A \bullet B = (A \oplus B) \ominus B $

A morfológiai szűrés eredménye általában a nyitás és zárás kombinációja:
$ A_{filtered} = (A \circ B) \bullet B $

#### Példa

Tegyük fel, hogy van egy bináris kép, ahol az objektumok fekete pixelek, és zaj is jelen van a képen. Ha a szerkesztőelem egy 3x3-as négyzet, akkor a morfológiai szűrés során:

1. **Nyitás:** Az erózió és dilatáció alkalmazásával eltávolítjuk a kis zajokat és simítjuk az objektumok határait.
2. **Zárás:** A dilatáció és erózió alkalmazásával kitöltjük a kis lyukakat és összekapcsoljuk a közeli objektumokat.

#### Alkalmazások

1. **Zaj Eltávolítása:** A morfológiai szűrés segít eltávolítani a kis zajokat a képből, miközben megőrzi az objektumok struktúráját.

2. **Határok Simítása:** Az objektumok határainak simítása, ami segít a jobb objektumfelismerésben.

3. *

4. **Struktúrák Kiemelése:** A fontos struktúrák kiemelése és a felesleges részletek eltávolítása.

#### Vizualizáció

A morfológiai szűrés eredménye egy tisztább és strukturáltabb kép lesz, ahol a zaj eltávolításra kerül, és az objektumok határai simábbak, a lyukak kitöltve maradnak.

### Alkalmazás Képfeldolgozási Feladatokban

1. **Előkészítő Lépés:** A morfológiai szűrést gyakran használják előkészítő lépésként más képfeldolgozási feladatok előtt, mint például az objektumok detektálása és azonosítása.
2. **Formaelemzés:** Az objektumok alakjának és méretének elemzésében segít, különösen, ha fontos a zaj eltávolítása és a struktúrák kiemelése.
3. **Képszegmentálás:** A morfológiai szűrés segíthet a képszegmentálásban az objektumok jobb elkülönítésében és az egymástól távol lévő objektumok kiemelésében.

### Dualitás Képfeldolgozásban

#### Definíciók és Jelölések

- **$ A $**: Eredeti kép vagy halmaz.
- **$ S $**: Szerkesztőelem (structuring element).
- **$ A^C $**: Az $ A $ halmaz komplementere, amely tartalmazza az összes olyan pontot, amely nem része $ A $-nak.
- **$ \hat{S} $**: Az $ S $ szerkesztőelem tükrözött változata, amely tartalmazza az összes $ (u, v) $ pontot, ahol $ (-u, -v) \in S $.

#### Morfológiai Műveletek

1. **Dilatáció ($ \oplus $)**:
   A dilatáció célja az objektumok növelése és a lyukak kitöltése. Egy adott szerkesztőelem segítségével az objektumok környezetében lévő pixelek is az objektum részévé válnak.

2. **Erózió ($ \ominus $)**:
   Az erózió célja az objektumok csökkentése és a zaj eltávolítása. Csak azok a pixelek maradnak az objektumban, amelyek környezetükben is teljesen benne vannak a szerkesztőelem által meghatározott formában.

#### Dualitás Tétel

A dualitás tétel kimondja, hogy egy művelet alkalmazása egy halmazra (vagy képre) és annak komplementerére fordított sorrendben ugyanolyan eredményt ad, mint a dual művelet alkalmazása az eredeti halmaz komplementerére. A tétel matematikai formában az alábbi egyenletekben jelenik meg:

1. **Erózió és Dilatáció Dualitása**:
   $
   A \ominus S = (A^C \oplus \hat{S})^C
   $
   Az erózió egy halmazra (vagy képre) egyenértékű a komplementer halmaz dilatációjával a tükrözött szerkesztőelemmel, majd a komplementer képzésével.

2. **Nyitás és Zárás Dualitása**:
   $
   A \circ S = (A^C \bullet \hat{S})^C
   $
   A nyitás egy halmazra (vagy képre) egyenértékű a komplementer halmaz zárásával a tükrözött szerkesztőelemmel, majd a komplementer képzésével.

#### Példák és Alkalmazások

1. **Zaj Eltávolítása és Kitöltés**:
   A nyitás eltávolítja a kis zajokat, míg a zárás kitölti a kis lyukakat. A dualitás elvét alkalmazva ezeket a műveleteket egyszerűen kifejezhetjük egymás komplementereként.

2. **Alakfelismerés és Képszegmentálás**:
   A morfológiai műveletek és azok dualitása segítenek az objektumok és a háttér jobb elkülönítésében, valamint az objektumok alakjának felismerésében.

3. **Topológiai Jellemzők Kiemelése**:
   A dualitás lehetővé teszi, hogy különböző topológiai jellemzőket emeljünk ki a képeken, például az összefüggőséget és a formákat, különböző morfológiai műveletek kombinálásával.

### Összefoglaló

A dualitás a morfológiai képfeldolgozásban egy alapvető elv, amely lehetővé teszi, hogy az eróziót és dilatációt, valamint a nyitást és zárást egymás dual műveleteiként értelmezzük. Ez az elv segít a képek zajcsökkentésében, az objektumok simításában, a lyukak kitöltésében és a struktúrák elemzésében.

![](assets/2024-05-26-10-58-00-image.png)

### Morfológiai Gradiens

#### Definíció

A morfológiai gradiens egy olyan művelet, amely a kép objektumainak határait emeli ki. Ez a művelet a dilatáció és az erózió közötti különbséget számítja ki, amely kiemeli az objektumok peremeit.

#### Működési Elv

A morfológiai gradiens kiszámításához először dilatációt, majd eróziót végzünk a képen ugyanazzal a szerkesztőelemmel, és a két eredményt kivonjuk egymásból.

#### Matematikai Leírás

Legyen $ I $ a bemeneti kép és $ B $ a szerkesztőelem. A morfológiai gradiens az alábbi módon számítható:

$ \text{Gradient}(I) = (I \oplus B) - (I \ominus B) $

ahol:

- $ \oplus $ a dilatáció
- $ \ominus $ az erózió

#### Példa

Tegyük fel, hogy van egy bináris vagy szürkeárnyalatos kép. A morfológiai gradiens kiemeli az objektumok határait, így azok jobban láthatóak lesznek.

#### Alkalmazások

1. **Éldetektálás:** Az objektumok peremének azonosítása a képen.
2. **Képszegmentálás:** Segít az objektumok elkülönítésében a háttértől.
3. **Textúraelemzés:** A textúrák finom részleteinek kiemelése.

### Morfológiai Laplace-transzformáció

#### Definíció

A morfológiai Laplace-transzformáció a morfológiai gradiens továbbfejlesztése, amely egyfajta második derivált a képen. Ez a művelet az objektumok belső és külső határait emeli ki, és segít a finom részletek detektálásában.

#### Működési Elv

A morfológiai Laplace-transzformációhoz először kiszámítjuk a morfológiai gradiens dilatált és erodált változatának különbségét.

#### Matematikai Leírás

Legyen $ I $ a bemeneti kép és $ B $ a szerkesztőelem. A morfológiai Laplace-transzformáció az alábbi módon számítható:

$ \text{Laplace}(I) = (I \oplus B) + (I \ominus B) - 2I $

ahol:

- $ \oplus $ a dilatáció
- $ \ominus $ az erózió

#### Példa

Tegyük fel, hogy van egy szürkeárnyalatos kép. A morfológiai Laplace-transzformáció kiemeli az objektumok határait és a finom részleteket, így azok jobban láthatóak lesznek.

#### Alkalmazások

1. **Éldetektálás:** Finom élek és részletek detektálása a képen.
2. **Képszegmentálás:** Segít az objektumok pontosabb elkülönítésében.
3. **Struktúraelemzés:** Az objektumok belső és külső határainak kiemelése.

### Morfológiai Éldetektálás

#### Definíció

A morfológiai éldetektálás olyan technika, amely a morfológiai műveletek segítségével azonosítja az éleket és határokat a képeken. Ez a technika a morfológiai gradiens és a Laplace-transzformáció kombinációját használja.

#### Működési Elv

A morfológiai éldetektálás során először morfológiai gradiens vagy Laplace-transzformációt alkalmazunk a képre, majd az eredményt felhasználva az élek és határok detektálására koncentrálunk.

#### Példa

1. **Morfológiai Gradiens Alapú Éldetektálás:**
   $
   \text{Edges}(I) = \text{Gradient}(I)
   $

2. **Morfológiai Laplace-transzformáció Alapú Éldetektálás:**
   $
   \text{Edges}(I) = \text{Laplace}(I)
   $

#### Alkalmazások

1. **Objektumok Határainak Meghatározása:** Az objektumok pontos határainak azonosítása.
2. **Textúraelemzés:** Finom textúrák és részletek kiemelése.
3. **Képszegmentálás:** Az élek és határok segítségével az objektumok pontosabb elkülönítése a háttértől.

### Összefoglaló

- **Morfológiai Gradiens:** A dilatáció és az erózió különbsége, amely az objektumok határait emeli ki.
- **Morfológiai Laplace-transzformáció:** A morfológiai gradiens továbbfejlesztése, amely az objektumok belső és külső határait emeli ki.
- **Morfológiai Éldetektálás:** A morfológiai gradiens és Laplace-transzformáció technikáit használja az élek és határok detektálására.

Ezek a technikák hatékony eszközök a képfeldolgozásban, amelyek segítenek az objektumok határainak és finom részleteinek azonosításában, a zaj eltávolításában és a képszegmentálásban.

![](assets/2024-05-26-11-01-33-image.png)

### Top-Hat Transzformáció (Csúcsdetektor)

#### Definíció

A top-hat transzformáció egy morfológiai művelet, amely kiemeli a kép világos objektumait egy sötétebb háttér előtt. Ez a művelet különösen hasznos a kis, fényes struktúrák detektálásában, mint például csúcsok vagy foltok.

#### Típusai

Két fő típusa van a top-hat transzformációnak:

1. **White Top-Hat (Fehér Top-Hat):** A nyitási transzformáció és az eredeti kép különbsége.
2. **Black Top-Hat (Fekete Top-Hat):** A zárási transzformáció és az eredeti kép különbsége.

#### Matematikai Leírás

- **White Top-Hat (Fehér Top-Hat):**
  $
  \text{White Top-Hat}(I) = I - (I \circ B)
  $
  ahol $ I $ a bemeneti kép, $ B $ a szerkesztőelem, és $ \circ $ a nyitás.

- **Black Top-Hat (Fekete Top-Hat):**
  $
  \text{Black Top-Hat}(I) = (I \bullet B) - I
  $
  ahol $ I $ a bemeneti kép, $ B $ a szerkesztőelem, és $ \bullet $ a zárás.

#### Működési Elv

1. **Fehér Top-Hat:**
   
   - Először alkalmazzuk a nyitási transzformációt a képre, amely eltávolítja a kis, fényes objektumokat.
   - Ezután kivonjuk az eredeti képből a nyitási transzformáció eredményét, így a kis, fényes objektumok kiemelkednek.

2. **Fekete Top-Hat:**
   
   - Először alkalmazzuk a zárási transzformációt a képre, amely kitölti a kis, sötét lyukakat.
   - Ezután kivonjuk az eredeti képet a zárási transzformáció eredményéből, így a kis, sötét objektumok kiemelkednek.

#### Alkalmazások

1. **Csúcsdetektálás:** Kis, fényes objektumok detektálása sötétebb háttér előtt.
2. **Képszegmentálás:** Objektumok jobb elkülönítése a háttértől.
3. **Textúraelemzés:** Finom textúrák és részletek kiemelése.

### Well-Hat Transzformáció (Völgydetektor)

#### Definíció

A well-hat transzformáció (völgydetektor) a top-hat transzformáció ellentéte, és a kép sötét objektumait emeli ki egy világosabb háttér előtt. Ez a művelet hasznos a kis, sötét struktúrák detektálásában, mint például völgyek vagy lyukak.

#### Matematikai Leírás

A well-hat transzformáció alapja a top-hat transzformáció, de az eredmények ellentétesek:

- **Well-Hat Transzformáció:**
  $
  \text{Well-Hat}(I) = (I \bullet B) - (I \circ B)
  $
  ahol $ I $ a bemeneti kép, $ B $ a szerkesztőelem, $ \bullet $ a zárás, és $ \circ $ a nyitás.

#### Működési Elv

- A well-hat transzformáció során először alkalmazzuk a nyitási transzformációt, majd a zárási transzformációt a képre.
- A két transzformáció eredményeinek különbségét vesszük, így a sötét objektumok kiemelkednek.

#### Alkalmazások

1. **Völgydetektálás:** Kis, sötét objektumok detektálása világosabb háttér előtt.
2. **Képszegmentálás:** Sötét objektumok jobb elkülönítése a világos háttértől.
3. **Struktúraelemzés:** Finom, sötét struktúrák és részletek kiemelése.

![](assets/2024-05-26-11-28-35-image.png)

## Vázkijelölés

**Váz (skeleton):** A váz egy gyakran alkalmazott régió-alapú alakleíró jellemző, mely leírja az objektumok általános formáját.

### <u>Távolság-transzformáció</u>

A távolság-transzformáció (distance transform) egy fontos módszer a képfeldolgozásban, különösen a vázkijelölés (skeletonization) során. Ez a módszer a bináris képeken működik, ahol a képpontok kétféle értéket vehetnek fel: 0-t (háttérpont) vagy 1-et (objektumpont). A távolság-transzformáció során minden objektumpont (1-es értékű képpont) helyére az adott pont és a legközelebbi háttérpont (0-s értékű képpont) közötti távolság kerül.

### A távolság-transzformáció folyamata:

1. **Bemenet**: Egy bináris kép, ahol a képpontok vagy 0-k (háttérpontok), vagy 1-ek (objektumpontok).

2. **Kimenet**: Egy távolságtérkép (distance map), amely nem bináris, és amelynek elemei a legközelebbi háttérponttól való távolságokat tartalmazzák.

### Távolságmértékek:

- **d4-távolság (Manhattan-távolság)**: Csak a vízszintes és függőleges irányú lépések engedélyezettek. Két pont közötti távolság az őket összekötő utak minimális hossza.
- **d8-távolság (Chessboard-távolság)**: Vízszintes, függőleges és átlós irányú lépések is engedélyezettek. Két pont közötti távolság az őket összekötő utak minimális hossza.
- **Chamfer-távolságok**: Ezek racionális számokkal közelítik az euklideszi távolságot, ahol az elmozdulások a távolsági maszkok véges súlyú elemeinek irányában engedélyezettek. Egy út költsége a benne szereplő élek/elmozdulások súly-összege. Két pont chamfer-távolsága az őket összekötő utak minimális költsége.

### Távolságtérkép számítása chamfer-távolságokra:

- A távolságtérkép chamfer-távolságokra kiszámítható lineáris időben (O(n) komplexitással, ahol n a képpontok száma) tetszőleges dimenzióban.

### Távolság-transzformáció lépései:

1. **Előfeldolgozás**: A kiindulási bináris képen a tulajdonság-pontok legyenek a háttérpontok.
2. **Távolságtérkép generálása**: Valamely távolságfogalom szerint, például d4, d8 vagy chamfer-távolságok.
3. **Lokális maximumhelyek, hegygerincek detektálása**: Ezek a távolságtérképen azonosíthatók, és gyakran a vázpontok helyeit jelölik ki.

### Példák:

- **Távolságtérkép számítása d4-távolság szerint**:
  
  - Csak a vízszintes és függőleges szomszédok számítanak.
  - A távolságtérkép elemei az adott pont és a legközelebbi háttérpont közötti Manhattan-távolságot tartalmazzák.

- **Távolságtérkép számítása chamfer-távolságokra**:
  
  - Előre- és visszafelé pásztázással számítják ki a távolságtérképet.
  - Az algoritmus a távolsági maszkok alapján engedélyezi az elmozdulásokat, és a költségeket összegzi az úthossz minimalizálására.

### A távolságtérkép érzékenysége:

- A távolságtérkép érzékeny a kiindulási kép zajára és a határpontok egyenetlenségeire, ezért gyakran szükséges valamilyen zajcsökkentési vagy előfeldolgozási lépés.

### Alkalmazások:

- **Vázkijelölés**: A távolságtérkép segítségével meghatározhatók az objektum középpontjai, amelyek a vázat alkotják.
- **Orvosi képfeldolgozás**: Az orvosi képek elemzésében, például csőszerű struktúrák (erek, légutak) középvonalának meghatározásában használják.

A távolság-transzformáció tehát egy hatékony eszköz a bináris képek elemzésére és az objektumok általános formájának leírására, különösen a vázkijelölés során.

![](assets/2024-05-26-19-05-44-image.png)

![](assets/2024-05-26-18-12-02-image.png)

### <u>Voronoi-váz</u>

A Voronoi-diagram egy hatékony módszer a vázkijelöléshez, amelyet a térbeli struktúrák elemzésére és reprezentálására használnak. A Voronoi-diagramot gyakran alkalmazzák a geometriai objektumok határpontjainak elemzésére, hogy meghatározzák az objektum belső szerkezetét, azaz a vázat.

### Voronoi-diagram alapjai:

1. **Definíció**: 
   
   - A Voronoi-diagram az m-dimenziós euklideszi tér egy felosztása n generálópont (vagy seed point) körül. Az egyes régiók, vagy cellák, azokból a pontokból állnak, amelyek közelebb vannak az adott generálópontjukhoz, mint bármely más generálópont.

2. **Tulajdonságok**:
   
   - A Voronoi-diagram egyértelmű és a sík minden pontját lefedi.
   - Minden Voronoi-cellának zárt, konvex alakja van.
   - A Voronoi-cellák csak közös éleiken érintkeznek.

### Voronoi-diagram használata a vázkijelölésben:

1. **Generálópontok kiválasztása**:
   
   - Az objektum határán egyenletesen mintavételezett pontok szolgálnak generálópontokként a Voronoi-diagram létrehozásához.

2. **Voronoi-diagram generálása**:
   
   - A generálópontok köré Voronoi-cellákat hoznak létre, amelyek lefedik az egész teret.

3. **Vázkijelölés**:
   
   - Ha a határpontok sűrűsége megfelelő, a Voronoi-diagram belső (a határt nem metsző) éleinek egyesítése a vázhoz konvergál. Ez azt jelenti, hogy az objektum belsejében található Voronoi-élek alkotják a vázat.

### Algoritmusok:

1. **Pont-beszúró módszer**:
   
   - Adott egy Voronoi-diagram k generálóponttal. A (k+1)-edik pont beszúrásakor megkeressük azt a cellát, amelybe a pont esik, majd újrarajzoljuk azt és a szomszédos cellákat. Ennek időigénye O(n).

2. **Oszd meg és uralkodj módszer**:
   
   - Két Voronoi-diagram összefűzése lineáris időben történik, az időigény O(n·logn). Az eljárás a generálópontok x-koordináta szerinti rendezésével kezdődik.

3. **Pásztázó egyeneses módszer**:
   
   - A generálópontok befoglaló téglalapját felülről lefelé pásztázzuk egy egyenessel, amely parabolaívekből álló partvonalat hoz létre. Az eljárás időigénye O(n·logn).

### Példák:

- **2D Voronoi-diagram**:
  
  - A generálópontok a síkban helyezkednek el, és a Voronoi-cellák határozzák meg az objektum vázát.

- **3D Voronoi-diagram**:
  
  - A generálópontok térben helyezkednek el, és a Voronoi-cellák térbeli szerkezeteket alkotnak, amelyeket a vázkijelölés során használnak.

### Alkalmazások:

- **Orvosi képfeldolgozás**:
  - A Voronoi-diagramokat gyakran használják az orvosi képeken látható csőszerű struktúrák (erek, légutak) vázkijelölésére. Ezek az eljárások segítenek az anatómiai szerkezetek pontosabb elemzésében és modellezésében.

### Voronoi-diagram és a vázkijelölés kritériumai:

- A Voronoi-diagram alapú vázkijelölés megfelel a következő kritériumoknak:
  - **Pont vékony**: A váz egy pont vékony.
  - **Objektum közepén helyezkedik el**: A váz az objektum közepén található.
  - **Geometriai transzformációk invarianciája**: A váz invariáns a legfontosabb geometriai transzformációkkal szemben.
  - **Topológia megőrzése**: A váz megőrzi a kiindulási objektum topológiáját.

### Tulajdonságok

- „Hibrid”: az input (a mintavételezett határpontok halmaza) diszkrét, az output folytonos elemekből áll.

- A közelítés pontossága és a vázban szereplő elemek száma erősen függ a
  mintavételezéstől.

- A nagyszámú lényegtelen részlet eltávolítására váztisztítás/regularizáció
  szükséges.
  
  - A vázat alkotó szegmensek (Voronoi élek) többféle fontossági mérték szerint osztályozhatók és eltávolíthatók a lényegtelennek ítéltek.

A Voronoi-diagram tehát egy hatékony és sokoldalú módszer a vázkijelölésre, különösen akkor, ha az objektum határpontjai sűrűn és egyenletesen mintavételezettek.

![](assets/2024-05-26-18-21-44-image.png)

![](assets/2024-05-26-18-22-22-image.png)

### Vékonyítás

A vékonyítás (thinning) egy iteratív képfeldolgozási technika, amely a bináris képeket redukálja egy vékonyabb, egyszerűsített vázszerű struktúrává, miközben megőrzi az eredeti objektum topológiai és geometriai jellemzőit. A vékonyítás célja az objektumok csontvázának (vázának) meghatározása.

### Vékonyítás alapjai:

1. **Definíció**:
   
   - A vékonyítás egy olyan folyamat, amely során a bináris képeken lévő objektumokat iteratív módon redukálják egy vékony vonalra vagy pontra, ami reprezentálja az objektum középtengelyét.

2. **Célok**:
   
   - Megőrizni az objektum topológiai szerkezetét.
   - Megőrizni az objektum geometriai formáját.
   - Elérni egy pont vékony struktúrát.

### Vékonyítási eljárások:

1. **Iteratív redukció**:
   
   - Az iteratív redukció során a képpontokat lépésről lépésre eltávolítják a képből, miközben biztosítják, hogy a folyamat megőrizze az objektum topológiai tulajdonságait.

2. **Irányszekvenciális algoritmus**:
   
   - Az algoritmus nyolc különböző irányból (S, SE, E, SW, N, NW, W, NE) vizsgálja a képpontokat és törli azokat, amelyek megfelelnek bizonyos törlési maszkoknak.
     
     ![](assets/2024-05-26-19-02-34-image.png)
     
     A többi irányhoz tartozó maszkok megkaphatók az előzőekből elforgatással.

3. **Saito és Toriwaki algoritmusa**:
   
   - Az algoritmus euklidészi távolságtérkép számításával kezdődik, majd iteratívan törli a minimális távolságértékű határpontokat a hat főirányból.

4. **Gong és Bertrand algoritmusa**:
   
   - Ez az algoritmus 6 irányból vékonyít, és a középfelszín kivonására szolgál.

### Kritériumok a vékonyítási eljárásokhoz:

1. **Pont vékony**:
   
   - A váz egy pont vékony, vagyis az objektum középtengelye egy pixel szélességű.

2. **Középen elhelyezkedő**:
   
   - A váz az objektum közepén helyezkedik el, reprezentálva az objektum szimmetriáját. - nem biztos

3. **Invariáns a geometriai transzformációkra**:
   
   - A váz legyen invariáns az eltolásra, forgatásra és uniform skálázásra. - nem biztos

4. **Topológia megőrzése**:
   
   - A váz megőrzi az eredeti objektum topológiai szerkezetét, beleértve az összefüggőséget és az esetleges lyukakat.

### Példák a vékonyításra:

- **2D vékonyítás**:
  
  - A kiindulási bináris képet iteratív lépésekben redukálják egy középvonallá. Minden iteráció során az algoritmus a képpontokat vizsgálja és törli azokat, amelyek megfelelnek a törlési kritériumoknak.

- **3D vékonyítás**:
  
  - A 3D képeken a vékonyítás célja a középfelszín meghatározása. Ez magában foglalja a térbeli objektumok redukálását egy olyan felszínre, amely az objektum belsejét reprezentálja.

### Vékonyítás alkalmazásai:

1. **Karakter- és szimbólumfelismerés**:
   
   - Egzotikus karakterek és szimbólumok felismerésére használják, mint például a japán aláírások.

2. **Aláírás- és kézírásfelismerés**:
   
   - Az aláírások és kézírások azonosítására, ahol a vékonyított kép alapján végpontok és elágazási pontok detektálhatók.

3. **Ujj- és tenyérlenyomat azonosítás**:
   
   - A vékonyított képek segítenek az ujjlenyomatok és tenyérlenyomatok jellemzőinek azonosításában.

4. **Raszter-vektor konverzió**:
   
   - A vonalrajzok és térképek digitalizálására és vektoros formátumba való átalakítására használják, ahol a vékonyított kép alapját képezi a vektorizálásnak.

5. **Orvosi képfeldolgozás**:
   
   - A 3D orvosi képeken a csőszerű struktúrák (például vérerek és légutak) középvonalának meghatározására használják.

### Összefoglalás:

A vékonyítás hatékony módszer a vázkijelölésre, amely az objektumok egyszerűsített, mégis informatív reprezentációját nyújtja. Az iteratív eljárások és speciális algoritmusok biztosítják, hogy a vázak megőrizzék az eredeti objektumok topológiai és geometriai tulajdonságait, miközben minimalizálják a struktúrák bonyolultságát.

![](assets/2024-05-26-19-00-52-image.png)

# On-line algorimtusok

# 8. A versenyképességi elemzés alapfogalmai. Az on-line lapozás (paging) és ládapakolás (bin packing) problémák.

### Alapfogalmak

1. **Online algoritmusok**: Az online algoritmusok olyan algoritmusok, amelyek bemenete darabokban érkezik (ez a daraboltság problémától függően változik), és minden egyes bemeneti darab után visszavonhatatlan döntést kell hozniuk, mielőtt a következő bemeneti darabot megkapnák. Minden döntéssorozathoz társul egy nem negatív értékkel rendelkező költség, amelyet az algoritmus minimalizálni próbál.

2. **Versenyképesség**: Mivel egy ilyen algoritmus nem tud mindig optimális döntéssorozatot előállítani, a versenyképesség egy olyan mérték, amely megmutatja, hogy az online algoritmus által generált sorozat költsége legfeljebb hány szorosa az optimális megoldás költségének.

3. **Formális definíció**:
   
   - **Bemenet**: A probléma bemenete általában egy $\sigma = (\sigma_1, \ldots, \sigma_n)$ kéréssorozat.
   - **Megoldások halmaza**: Minden egyes $\sigma$ esetén van egy $S(\sigma)$ megoldáshalmaz, ahol minden megoldásnak van egy nem negatív valós költsége $C(\tau)$, ahol $\tau \in S(\sigma)$.
   - **Offline optimális költség**: Az offline optimális költség $\text{Opt}(\sigma)$ az $\sigma$ bemenet minimális költségű megoldása: $\text{Opt}(\sigma) = \min \{ C(\tau) : \tau \in S(\sigma) \}$.

4. **Deterministic online algoritmus**: Egy determinisztikus online algoritmus $A$ nem látja a jövőt, és minden egyes bemeneti darab után ($\sigma_1, \ldots, \sigma_{i+1}$) egy új lépést ($\tau_{i+1}$) kell számítania úgy, hogy az $\tau_{i+1} = A(\sigma_1, \ldots, \sigma_{i+1})$ legyen, ahol $A(\sigma)$ az $A$ algoritmus által generált akciósorozat a $\sigma$ bemenetre. Minden $\sigma$ esetén $A(\sigma) \in S(\sigma)$ kell, hogy legyen (azaz az $A$ mindig érvényes megoldást kell, hogy generáljon).

5. **Versenyképességi arány**: Az algoritmus $A$ c-versenyképes, ha minden lehetséges bemeneti sorozatra $\sigma$ teljesül, hogy $\frac{C(A(\sigma))}{\text{Opt}(\sigma)} \leq c$.

### Lapozás (paging)

A lapozás vagy paging problémában két pozitív egész szám paraméterünk van, n és k.
Feltehetjük, hogy 1 < k < n. A k paraméter a cache mérete, az n pedig a lemez mérete (azt jelenti hogy n féle input lehet).

Az inputban mindig valamelyik oldalát (page-ét) kérjük a lemeznek. Ha az adott oldal benne van a cache-ben, akkor nincs mit tennünk, ekkor a válasz 0. Ha nincs a cache-ben, de még nincs tele a cache, akkor egységnyi költségért berakhatjuk a cache-be az adott oldalt, ez szintén a 0 válasz. Ha a cache tele van, és egy olyan oldalt kérünk, ami nincs a cache-ben, akkor egységnyi költségért valamely oldalt ki kell dobnunk a cache-ből, és a helyére betölteni a kívánt oldalt. Ha a p oldalt dobjuk ki a cache-ből, akkor az algoritmus válasza p lesz.

**Algoritmusok (online):**

- ***LFU*** (least frequently used): a legkevesebbet használt page-et dobjuk ki

- ***FIFO*** (first in first out): a legrégebben bekerült page-et dobjuk ki,

- ***LRU*** (least recently used): a legrégebben használt oldalt dobjuk ki,

- ***LIFO*** (last in first out): a legutoljára betöltött/használt oldalt dobjuk ki.

**Offline algoritmus:**

- ***LFD*** (longest forward distance): azt dobjuk ki, amit a jövőben a legkésőbb fogunk újra lekérni. Ez optimális megoldást ad.

Sem az *LFU* sem a *LIFO* nem versenyképesek. A legjobb online algoritmusok erre a
problémára k-versenyképesnél nem lehetnek jobbak.

Az *LRU* és a *FIFO* + a "marking" algoritmusok k-versenyképesek.

**Marking algoritmus:**

- Először csak simán feltöltjük a cache-t

- minden cache-ben lévő oldal lehet jelölt vagy nem jelölt, a cache feltöltés után megjelölünk minden elemet

- ha jön p-re egy request, akkor
  
  - ha p benne van a cache-ben, akkor megjelöljük, és továbbmegyünk
  
  - ha nincs, akkor ha minden elem be van jelölve, letöröljük az összes
    jelölést, és mivel van legalább egy nem jelölt oldal, valamelyiket
    kiválasztjuk valamilyen algoritmus alapján, kidobjuk, betöltjük p-t, és
    megjelöljük.

![](assets/2024-05-26-23-16-51-image.png)

**Ládapakolás (bin-packing)**

A ládapakolási algoritmus inputja az a1, … , an sorozat, ahol 0 < ai < 1. Ezeket a számokat az érkező itemek méretének tekintjük, és a célunk ezeket az itemeket egységnyi méretű ládákba pakolni úgy, hogy minél kevesebb ládát használunk.

Ennél a problémánál az aszimptotikus versenyképességi hányadost vizsgáljuk, vagyis az
érdekel minket, hogy ha az optimum költsége a végtelenbe tart, akkor mennyi lesz a
versenyképességi hányados.

- Abszolút versenyképesség
  
  - Az abszolút versenyképesség egy általános, konkrétabb formája a versenyképességnek. Egy algoritmus abszolút versenyképes, ha létezik egy olyan állandó $c$, amelyre minden lehetséges bemeneti sorozatra igaz, hogy az online algoritmus költsége legfeljebb $c$-szerese az optimális offline algoritmus költségének.
    
    Formálisan, egy online algoritmus $A$ abszolút $c$-versenyképes, ha minden lehetséges $\sigma$ bemenetre:
    $ \frac{C(A(\sigma))}{\text{Opt}(\sigma)} \leq c $
    ahol $C(A(\sigma))$ az $A$ algoritmus által elért költség $\sigma$ bemenetre, és $\text{Opt}(\sigma)$ az optimális offline algoritmus költsége ugyanarra a bemenetre.

- Aszimptotikus versenyképesség
  
  - Az aszimptotikus versenyképesség egy lazább és hosszú távú megközelítés a versenyképesség mérésére. Egy algoritmus aszimptotikusan $c$-versenyképes, ha létezik egy $c$ és egy konstans $b$, amelyre minden lehetséges $\sigma$ bemenetre igaz, hogy az online algoritmus költsége legfeljebb $c$-szerese az optimális költségnek, egy konstans $b$ hozzáadásával.
    
    Formálisan, egy online algoritmus $A$ aszimptotikusan $c$-versenyképes, ha létezik egy $c$ és egy $b$, hogy minden lehetséges $\sigma$ bemenetre:
    $ C(A(\sigma)) \leq c \cdot \text{Opt}(\sigma) + b $
    
    Ez azt jelenti, hogy az algoritmus teljesítménye a nagy bemeneti méretekre nézve legfeljebb $c$-szerese az optimális algoritmus teljesítményének, némi konstans eltéréssel, ami a kisebb bemeneteknél jelentős lehet, de a nagy bemeneteknél már kevésbé.

Nincs olyan online algoritmus, aminek az aszimptotikus versenyképességi hányadosa jobb lenne, mint 4/3 a ládapakolási problémára.

<u>Algoritmusok:</u>

- **NF** (next fit): egy láda van nyitva, addig pakolunk bele, amíg az érkező itemek
  beleférnek, ha nem fér bele ami jön, akkor lezárjuk, és új ládát nyitunk, ez 2-versenyképes,

- **HARMONIC(k)**: k láda van nyitva, mindegyiknek megvan, hogy mekkora
  méretű itemeket pakolunk bele, mindegyik kategóriából csak egy van nyitva, ha
  betelik, nyitunk egy új olyan kategóriájú ládát, ez max 1.69103 versenyképes,

- **BF** (best fit): sosem csukunk be egy ládát, abba a ládába rakjuk az érkező itemet, amelyikben a legkisebb maradék helyet hagyja, ez 1.7-versenyképes,

- **FF** (first fit): az érkező itemet az első olyan ládába rakjuk, amelyikbe belefér.

A ládapakolásnak van 2d-s változata, a strip packing.

# 9. On-line ütemezés (scheduling) és k-szerver problémák

### **On-line ütemezés**

Az online ütemezés problémánál van $m$ gépünk, és ezekre kell ütemeznünk jobokat. Minden jobnak van egy processing time-ja, a $\sigma$-ban (szigmában) ezeket kapjuk meg. A válaszunk egy inputra a gép sorszáma, amelyre a munkát ütemezzük. A célunk az ún. makespan minimalizálása, vagyis, hogy az összes munkát a lehető leghamarabb befejezzük.

A $0 \le p_i$ a job költsége

A makespant $L^*$-al jelöljük.

Optimum alsó korlátai:

- $ \frac{\sum p_i}{m} \le L^*$

- $\max p_i \le L^*$

LISTA algoritmus az érkező munkát a legkisebb töltésű gépre ütemezi (egyenlőség
esetén a legkisebb indexűre). A LISTA algoritmus pontosan $(2 - \frac{1}{m})$-versenyképes.

![](assets/2024-05-28-13-33-51-image.png)

#### On-line ütemezés független gépek esetén

Mindegyik gépen különböző sebességgel végződik el a job (tehát egy job-hoz $m$ db költség tartozik)

Optimum alsó korlátai:

- $L^*$ biztos nagyobb vagy egyenlő mint az összes jobhoz tartozó költségek közül a legkisebb

- $ \frac{\sum_i \min_j p_i,j}{m}  \le L^*$ , tehát a költségek minimumának összege per a gépek számánál biztos nagyobb egyenlő az $L^*$

Itt a LISTA algoritmus: arra a gépre tesszük a $\sigma_i$-t, amelynél $load(j)+p_i,j$ minimális. Független gépeknél pontosan $m$-kompetitív

![](assets/2024-05-28-14-55-37-image.png)

#### On-line ütemezés összefüggő gépekre

Minden géphez tartozik egy $v$ sebesség is, ami miatt $load(j)= \frac{\sum_{\tau_i=j}p_i}{v_j}$ , tehát a gépen lévő loadot még a géphez tartozó $v$ sebességgel is el kell osztani.

Itt a LISTA algoritmus: arra a gépre ütemezzük a jobot amin így a legkisebb lesz a $load$ (több ilyen esetén a legkisebb indexűt azok közül), versenyképessége $\Theta(\log m)$ (theta)

($c_1 \log m \leq f(m) \leq c_2 \log m$, pontosabb mint $\Omicron$)

Optimum alsó korlátai:

- $\frac{\sum p_i}{\sum v_j} \le L^*$

- $\frac{\max p_i}{\max v_j} \le L_*$

![](assets/2024-05-28-16-22-38-image.png)

#### On-line ütemezés idő modell

A munkáknak feldolgozási idejük és érkezési idejük van. Egy munkát nem kezdhetünk el az érkezési ideje előtt. Nincs olyan online det. alg. aminek az idő modellre 4/3-nál jobb versenyképességi hányadosa lenne (1.3473-ra is meg lehet mutatni).

Optimum alsó korlátai:

- $\max(p_i+t_i) \le L^*$

- $\frac{\sum p_i}{m} \le L^*$

Az INTV algoritmus:

- gyűjtögető fázis: várunk addig, amíg minden gép leüresedik, közben gyűjtjük a munkákat, amik érkeznek,

- szétosztó fázis: az aktuális időpillanatban elérhető összes munkát optimálisan
  ütemezzük a gépekre.

- $2$ versenyképes

- ez már 3 gépre is NP nehéz

![](assets/2024-05-28-16-43-44-image.png)

Online LPT:

- addig vár amíg lesz szabad gép és arra a leghosszabb jobot ütemezi be

- $3/2$ versenyképes

INTV+A algoritmus:

- INTV-t számolunk, de az offline algoritmust (az összevárt elemek elosztását) az A algoritmus számítja

- Tétel: ha az A algoritmus $\alpha$ approximál, akkor INTV+A algoritmus egy $2\alpha$-versenyképes online algoritmus
  
  - sima INTV algoritmusnál $\alpha=1$ (mivel optimális), ezért lesz 2 versenyképes
  
  - Sidenote:
    
    - Egy 2-approximációs algoritmus garantálja, hogy az általa talált 
      megoldás költsége legfeljebb kétszerese az optimális megoldás 
      költségének. (offline problémákra használják)
    
    - Egy 3-versenyképes algoritmus garantálja, hogy az általa talált megoldás
       költsége legfeljebb háromszorosa az optimális offline megoldás 
      költségének.

INTV+LPT (longest processing time) algoritmus:

- INTV, de amikor gépekre osztjuk a munkákat akkor azokat először $p_i$ szerint csökkenő sorrendbe rendezzük, ezeket LIST algoritmussal optimalizáljuk
  
  - LIST algoritmus 2 versenyképes

- Állítás: LPT alg $4/3$ approximál => INTV+LPT 8/3 versenyképes

### K-szerver probléma

Van $M$ metrikus terünk

- pontok egy $M$ halmaza + egy $d(x,y)$ $M^2 \rarr \R_0^+$ (nem negatív, valós) távolságfüggvény

- távolságfüggvény:
  
  - $d(x,x)=0$, önmagától 0 távolságra van mindenki
  
  - $d(x,y) > 0$, ha $x \ne y$
  
  - $d(x,y)$ = $d(y,x)$
  
  - $d(x,y) + d(y,z) \ge d(x,z)$ 

Szerverkonfiguráció: $C \sube M$, multihalmaz (lehet egy ponton több szerver), $C$ elemszáma $k$

-  Pl: $k=3$, $M = \R$ (valós számegyenes)
  
  - Példa konfigurációk: {0,0,2}, {1,2,4}

Kezdeti konfiguráció: $C_0$

Cél hogy megjelenik egy request, rámozgassuk az egyik szervert

$d(C,C')$ : minimális $C$-$C'$ közti $d$-vel súlyozott párosítás súlya

- Pl: $M=R$, $k=3$
  
  - {0,0,2} -> {1,3,5}
    ![](assets/2024-05-29-00-12-26-image.png)

![](assets/2024-05-29-00-14-14-image.png)

Cél: a legolcsóbban a megfelelő konfigurációba vinni a szervereket (úgy hogy kiszolgáljon mindent amit kell)

![](assets/2024-05-29-00-17-42-image.png)

A legközelebbi szerver mozgatása nem versenyképes.

Gyenge versenyképesség: az $A$ algoritmus gyengén c-komptetitív, ha minden $C_0$-hoz $\exist \beta $ konstans, melyre $\forall \sigma$-ra: $c(A(\sigma) \le c*opt(\sigma)+\beta$.

- abszolút versenyképesség gyenge is, $\beta=0$

- ha gyenge => ha $opt(\sigma) \rarr \inf$ akkor $\frac{c(A(\sigma)}{opt(\sigma)} \le \frac{c*opt(\sigma)+\beta}{opt(\sigma)} \rarr c$

- aszimptotikus versenyképességgel szemben $\beta$ csak konstans lehet

Egy algoritmus "lusta" ha minden lépésben legfeljebb egy szervert mozgat.

Állítás: minden algoritmus lustává tehető.

A lapozás (paging) majdnem ugyanaz mint a k-szerver probléma uniform téren (maximum távolság egy, minimum távolság 0 ha ugyabba megy).

- ebből következik, hogy az uniform térre nincs k kompetitívnél jobb online algoritmus (ha $|M| \ge k+1$) 

Tétel: ha $|M| \ge k+1$, akkor nincs olyan determinisztikus online algoritmus, mely jobb lenne mint gyengén k-versenyképes

#### Double Coverage (DC) algoritmus

$M = \R$, $d(x,y)=|x-y|$ (számegyenes)

DC:

- ha $C$ a konfig és $p \in \R$ a kérés 
  
  - ha $p \in C$, akkor done
  
  - ha $p < \min C$, akkor $\min C$-t mozgatjuk (bal legszélső)
  
  - ha $p > \max C$, akkor $\max C$-t mozgatjuk (jobb legszélső)
  
  - ha $x < p < y$,    $x,y \in C$,    $(x,y) \cap C = \empty$ (szorosan az $x$ és $y$ között van,  nincs más szerver abban az intervallumban)
    
    - legyen $x \rarr x+d$,   $y \rarr y-d$, ahol $d:= \min(|x-p|,|y-p|)$ 
  
  - nem lazy algoritmus! (de lazyvé lehet tenni)
    
    - ha mindig csak azt mozgatnánk oda ami a nem lazy változatában odaérne

- DC egyenesen gyengén $k$ versenyképes

#### Work Function Algorithm (WFA)

- **Definíció**:
  Az algoritmus célja, hogy gyenge k-versenyképes legyen bármely metrikus térben. Az algoritmus minden bemeneti szekvencia minden prefixére kiszámítja az offline optimális költséget. Legyen $ w_t(C) $ az offline optimális költség, amellyel az első $ t $ kérést kiszolgáljuk és a konfiguráció $ C $-ben végzünk.

- **Költségszámítás**:
  A $ w_t(C) $ költséget indukcióval számítjuk ki $ t $-re:
  
  - $ w_0(C_0) = 0 $ és minden $ C \neq C_0 $ esetén $ w_0(C) = \infty $.
  - Ha a $ t $-dik kérés $ p $, és $ p \notin C $, akkor $ w_t(C) = \infty $.
  - Ellenkező esetben: 
    $
    w_t(C) = \min_{C'} \{ w_{t-1}(C') + d(C', C) \}
    $
    ahol $ d(C', C) $ a $ C' $ és $ C $ konfigurációk közötti távolság.

### Példa

A metrikus tér pontjai 0, 2 és 5, és a távolság függvénye $ d(x, y) = |x - y| $. Az induló szerver konfiguráció $ \{0, 5\} $, a kérési szekvencia pedig 2, 0, 2.

#### Táblázat az optimális költségekről

A táblázat az $ w_t(C) $ költségeket mutatja $ t = 0, 1, 2, 3 $ esetén a különböző konfigurációkhoz:

$
\begin{array}{c|c|c|c}
 & \{0, 2\} & \{0, 5\} & \{2, 5\} \\
\hline
0 & \infty & 0 & \infty \\
1 & 2 & \infty & 2 \\
2 & 2 & 3 & 4 \\
3 & 4 & 6 & 6 \\
\end{array}
$

- **Számítások**:
  Például $ w_2(\{0, 5\}) $ kiszámítása: az előző sorban $ \{0, 2\} $ költsége 3, a $ \{0, 2\} $-ből $ \{0, 5\} $-be történő áthelyezés költsége 3, összesen 6. A $ \{2, 5\} $-ből $ \{0, 5\} $-be történő áthelyezés költsége 2, összesen 4. Így a minimum $ w_2(\{0, 5\}) = 4 $.

### Algoritmus működése

Az algoritmus lusta algoritmusként működik:

- Ha a $ t $-dik kérés $ p $ és $ p $ nincs a jelenlegi konfigurációban $ C $, akkor kiválasztja azt a szervert $ q $-t, amely a $ p $-t szolgálja ki, és minimalizálja a költséget:
  $
  w_t(C - \{q\} + \{p\}) + d(q, p)
  $

### Példa az algoritmus működésére a 2, 0, 2 kérési szekvencián

- **Kezdeti konfiguráció**: $ \{0, 5\} $
  
  - Kérés: 2
    - Ha 0-tól mozgunk 2-re: $ w_1(\{2, 5\}) + d(0, 2) = 2 + 2 = 4 $
    - Ha 5-től mozgunk 2-re: $ w_1(\{0, 2\}) + d(5, 2) = 3 + 3 = 6 $
    - Tehát választjuk a 0-t, és a konfiguráció $ \{2, 5\} $ lesz.

- **Következő kérés: 0**
  
  - Ha 2-ről mozgunk 0-ra: $ w_2(\{0, 5\}) + d(2, 0) = 4 + 2 = 6 $
  - Ha 5-ről mozgunk 0-ra: $ w_2(\{2, 0\}) + d(5, 0) = 3 + 5 = 8 $
  - Tehát választjuk a 2-t, és a konfiguráció $ \{0, 5\} $ lesz.

- **Következő kérés: 2**
  
  - Ha 0-ról mozgunk 2-re: $ w_3(\{2, 5\}) + d(0, 2) = 6 + 2 = 8 $
  - Ha 5-ről mozgunk 2-re: $ w_3(\{0, 2\}) + d(5, 2) = 3 + 3 = 6 $
  - Tehát választjuk az 5-öt, és a konfiguráció $ \{0, 2\} $ lesz.

A work function algoritmus $(2k − 1)$-versenyképes bármilyen metrikus térre, és sok esetben $k$-versenyképes.

# Gépi tanulási módszere

# 10. Gépi tanuláshoz kapcsolódó alapfogalmak: jellemzőkinyerés, a dimenzionalitás átka, no free lunch tétel, Occam borotvája, általánosítás és túltanulás, a tanulás hibájának mérése.

### Jellemzőkinyerés

- Az optimális jellemzőkészlet nyilván feladatfüggő

- Ideális esetben a feladatot ismerő szakember mondja meg

- De a gyakorlatban mégis sokszor az informatikusra marad

- Jó jellemzőkészlet: minél relevánsabb és minél kevesebb jellemző

- A nem releváns jellemzők bevétele nehezíti a tanulást

### Dimenzionalitás átka

- a sok jellemző megnehezíti a tanulást
  
  - Jellemzők száma = jellemzőtér dimenziószáma
  
  - Magasabb dimenziószámú térben nehezebb tanulni
  
  - Ritkábbak az adatpontok (a magasabb dimenzió miatt)
  
  - Több jellemző => sokkal több tanítópélda kell
    
    - a modell paraméterszámát és a tanítás idejét is fölöslegesen növelik
  
  - A felesleges jellemzők zajok, félrevezethetik a tanító algoritmust

- Általában kézileg próbáljuk a legjobb jellemzőket kiválasztani (“manual”, “hand-crafted” stb.)

- A jellemzőtér transzformálással is redukálható
  
  - Az új jellemzők a régi jellemzők valamilyen kombinálásával állnak elő
  
  - Általában egyúttal a dimenziószámot is redukáljuk (az új tér dimenziószáma kisebb, mint a régié)

### "No free lunch" tétel

- Nincs olyan univerzális tanulóalgoritmus, ami minden feladaton jobb, mint a többi
  
  - Az optimális tanulóalgoritmus mindig a feladattól függ
  
  - Minden tanulóalgoritmushoz lehet olyan feladatot találni, amin jól működik, és olyat is, amin rosszul

- Egy másik megfogalmazás: az „összes lehetséges feladatra” nézve  az összes tanulóalgoritmus átlagos teljesítménye ugyanakkora
  
  - Nem az „összes lehetséges feladatra” kell megoldást keresnünk, csak egy típusra
  
  - Gépi tanulási adatbázisok: gépi tanulási algoritmusok széles körű, objektív összehasonlítására szolgálnak („benchmark”)
    
    - Pl: UCI Machine Learning Repository

### "Occam borotvája"

- Tapasztalat: általában az egyszerűbb modell általánosít jobban
  
  - De persze a túl egyszerű modell sem jó

- Az optimális komplexitású modell feladatonként eltérő
  
  ![](assets/2024-05-29-13-46-45-image.png)

### Általánosítás és túltanulás

- No Free Lunch tétel: sosem lehetünk biztosak benne, hogy a tanult modell jól általánosít a tanulás során nem látott esetekre

- Tapasztalat: a modell méretének komplexitásának növelésével a modell rugalmassága nő, egyre pontosabb lesz a tanítópéldákon
  
  - Viszont a tesztpéldákon egy ponton túl romlani fog a teljesítménye
  
  - Ezt hívják túltanulásnak (overfitting): a modell az általános tulajdonságok után már az aktuális véges mintahalmaz egyedi furcsaságait kezdi megtanulni
    
    - lásd fentebbi ábra

### A tanulás hibájának mérése

- A tanítópéldák alapján a tanítóalgoritmus készít egy modellt, azaz egy hipotézist a $(x_1,...,x_n) \rarr c$ függvényre
  
  - Ez a tér tetszőleges $(x_1,...,x_n)$ pontjára meg tudja tippelni, hogy az melyik osztályba esik (kiértékelés)

- Fő célunk nem a tanítópéldák címkéjének hibátlan megtanulása, hanem a tanítás során nem látott példákra való általánosítás

- Hogyan tudunk becslést adni az általánosító képességre?
  
  - A példáink egy részét nem használjuk fel a tanítás során => külön teszthalmaz kell
  
  - Ezeken hogyan teljesít a modellünk? (címkézett példák!)

- Kiértékelés:
  
  - A modell lefuttatása a teszthalmazon => tippelt címkék
  
  - A tippelt (jósolt) és a valódi címkék összehasonlítása
  
  - Az eltérés számszerűsítése („mérése”)
  
  - Nagyon sok metrika van, területenként eltérő lehet, hogy melyiket használják (pontosság, precision-recall-F1, AUC, UAR, MSE, RMSE, korreláció, Cllr, WER/CER)

- Regressziós modell kiértékelésénél: Mean squared error
  
  - **Hiba (Error) kiszámítása**: Az egyes megfigyelésekre a hiba az eltérés a valódi érték ( $ y_i $ ) és a modell által becsült érték ( $ \hat{y}_i $ ) között. Az egyes hibák kiszámítása: $ e_i = y_i - \hat{y}_i $.
  
  - **Hibák négyzetre emelése**: Az egyes hibák négyzetre emelése annak érdekében, hogy a pozitív és negatív hibák ne egyenlítsék ki egymást. $ e_i^2 = (y_i - \hat{y}_i)^2 $.
  
  - **Négyzetes hibák átlagolása**: Az összes négyzetes hiba átlagának kiszámítása, amely az MSE értékét adja. Az MSE képlete:
    $
       MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
       $, ahol $ n $ az összes megfigyelés száma.
  
  - Root-mean-squared error: MSE gyök alatt

- Osztályozás esetén a legegyszerűbb: hibaarány
  
  - Eltévesztett tesztpéldák száma / összes tesztpélda száma
  
  - Vagy: eltalált tesztpéldák száma / összes tesztpélda száma (accuracy)

- Részletesebb analízis: tévesztési mátrix
  
  - Segít megérteni, hogy mely osztályokat keveri a gép
  
  - A különböző hibákat különböző súllyal számíthatjuk a hibafüggvénybe
  
  - Ehhez egy költségmátrixban kell megadni az egyes cellák súlyát
  
  - „0-1 loss”: a főátló elemeit 0-val, a többi cellát 1-gyel súlyozzuk
  
  - Megegyezik az osztályozási hibaaránnyal
    ![](assets/2024-05-29-14-45-08-image.png)

- Információ-visszakeresési (information retrieval) feladatok
  
  - Releváns elemek megtalálása (pl. Google keresés)
  
  - Pozitív és negatív osztályok (kell vs. nem kell)
  
  - Analóg feladatok is lehetnek, pl. beteg / nem beteg

- Speciális metrikák
  
  - 2x2-es tévesztési mátrix
  
  - Négy kategória: True/False Positive/Negative
  
  - Precision, Recall: TP és az összes ??? aránya
  
  - F-measure: a kettő harmonikus közepe
  
  - Specificity: TN / (TN + FP), sensitivity: TP / (TP + FN)
    ![](assets/2024-05-29-14-47-13-image.png)

- Osztályozásnál: keresztentrópia
  
  A keresztentrópia (cross-entropy) hibafüggvény egy széles körben használt veszteségfüggvény a gépi tanulásban, különösen osztályozási problémák esetén, beleértve a bináris és többosztályos osztályozást is. A keresztentrópia mérőszámot ad arra, hogy mennyire jól teljesít a predikciós modell a valós osztályok előrejelzésében.
  
  **Bináris keresztentrópia** 
  
  Bináris osztályozási problémák esetén, ahol csak két lehetséges kimenetel (0 vagy 1) van, a keresztentrópia veszteségfüggvényt így írhatjuk fel:
  
  $
  H(y, \hat{y}) = - \frac{1}{n} \sum_{i=1}^{n} [y_i \log \hat{y}_i + (1 - y_i) \log (1 - \hat{y}_i)]
  $
  
  Itt:
  
  - $ y_i $ az $ i $-edik valódi címke (0 vagy 1),
  - $ \hat{y}_i $ az $ i $-edik predikált valószínűség az 1-es osztályra,
  - $ n $ a minták száma. 