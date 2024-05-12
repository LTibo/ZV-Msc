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

### 1. Automaták minimalizálása

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