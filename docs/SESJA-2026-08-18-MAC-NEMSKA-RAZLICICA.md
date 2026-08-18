# Seja 18. 8. 2026 (Mac) — nemška različica strani

Repozitorij `mklpro21/mklpro21.github.io`, veja `main`.
Commita **`65e275d`** (nemški strani) in **`82aa39d`** (podpora, zasebnost, teme, novosti).
Potisnjeno isti dan; GitHub Pages je postregel novo različico **~30 s po potisku**.

**Koda aplikacije se v tej seji ni spremenila** — `LazyProTrip-v3` ni bil odprt razen za
branje, ko je bilo treba preveriti trditve. Graf zato ni osvežen (Mac ga tako ali tako
ne gradi).

---

## Kaj je zunaj

| naslov | prej | zdaj |
| --- | --- | --- |
| `/` · `/en/` | ✅ | ✅ + preklopnik DE, okvir z novostma |
| `/de/` · `/de/pic-edit/` | — | ✅ novo |
| `/pic-edit/` · `/en/pic-edit/` | ✅ | ✅ + preklopnik DE |
| `/podpora/` · `/zasebnost/` | SL + EN | SL + EN + **DE** |
| `/sitemap.xml` | 6 naslovov | 8, z `hreflang` za vse tri jezike |

Vseh **13 nemških posnetkov** se streže (200), preverjeno po objavi.

---

## Podpora in zasebnost: tretji jezik **v** strani, ne kot nova pot

`‌/podpora/` in `‌/zasebnost/` sta vpisana v App Store Connect. Nova pot (`/de/podpora/`) bi
pomenila, da je treba popraviti vpis v ASC, sicer pregledovalec naleti na 404. Zato je
nemščina dodana **v isti datoteki**, tako kot je bila prej dodana angleščina:

```
SL  →  <hr id="en">  →  EN  →  <hr id="de">  →  DE
```

Na vrhu je skok med jeziki (`English ↓ · Deutsch ↓`), nemški strani pa kažeta neposredno na
`/podpora/#de` in `/zasebnost/#de`, da nemški obiskovalec ne pristane na slovenskem besedilu.

⚠️ **Ob vsaki vsebinski spremembi pravilnika je treba popraviti vse tri različice in datum v
vseh treh.** Trenutno vse tri navajajo 13. avgust 2026 — dodajanje prevoda vsebine ni
spremenilo, zato datum ostaja.

---

## Posnetki zaslona: kaj je bilo prečiščeno

Merilo je tabela v `README.md` (prava imena → izmišljena). Od 20 nemških posnetkov z dne
18. 8. jih je na strani **13**.

| posnetek | poseg |
| --- | --- |
| `30-de-aktivna-pot` | tablica `LJ 62-ZKG` na fotografiji in oznaka `LJ62ZKG` v vrstici vozila **zamenjani** z izrezoma iz `01-aktivna-pot.webp` |
| `35-de-vozilo` | `LJ87CUG` — mozaik |
| `40`, `41`, `42` (teme) | ista tablica — mozaik |
| ostalih osem | brez posega |

### Presaditev tablice namesto zamegljevanja (`30-de-aktivna-pot`)

`IMG_0207` in objavljeni `01-aktivna-pot.webp` sta **ista fotografija istega avta v istem
okvirju**, le zamaknjena. Zamik sem izmeril s korelacijo na štirih neodvisnih izsekih
(kolo, maska, žaromet, odbijač) — vsi štirje dajo **dx = 0, dy = −23 px** v prostoru 760 px.
Zato je bilo mogoče prenesti prečiščeni izrez s tablico `LJ 01-LPT` in oznako `LJO1LPT`
namesto zamegljevanja. Šiv ni viden.

⚠️ Pri `40`–`42` (Ford) ista poteza **ne deluje**: MSE ostane visok in dva izseka se ne
strinjata o zamiku (`dx = 23` proti `dx = −30`). Fotografija je drugače izrisana — drugačen
sij, drugačen izrez. Tam je mozaik pravilna izbira, presaditev bi bila vidna.

---

## 🔴 Vision OCR sam ni zadosten preizkus za tablice

`README.md` priporoča preverjanje z Applovim Vision OCR. V tej seji je **odpovedal v obe
smeri**, zato priporočilo ne zadošča:

| | OCR | prosto oko |
| --- | --- | --- |
| `35-de-vozilo` | ✅ prebral `LJ087-CUG` | packa je videti dovolj gosta |
| `40`–`42` (teme) | ❌ ni prebral ničesar | ✅ `LJ` in `-CUG` berljiva takoj |

Vzrok je isti v obeh primerih: **packa je pokrila samo srednji dve števki.** OCR potrebuje
celotno zaporedje in ob prekinjeni sredini odpove; človek prebere okvir in ugane sredino.
Tri od trinajstih slik so šle skozi prvi pregled prav zato, ker je bil pregled samo strojni.

**Postopek odslej:** OCR **in** pogled na povečano tablico. OCR lovi tisto, kar oko spregleda
(drobne oznake, besedilo v okvirju tablice), oko lovi tisto, kar OCR spregleda (delne packe).

---

## Zavrnjeni posnetki

Neprečiščeni; če jih kdaj dodajamo, jih je treba najprej prepisati po tabeli zamenjav.

| posnetek | kaj je na njem |
| --- | --- |
| `IMG_0203`, `IMG_0221` | seznam strank — sedem resničnih imen podjetij |
| `IMG_0208`, `IMG_0225` | postanki in poti — štiri resnična podjetja z naslovi in **zaseben stanovanjski naslov** |
| `IMG_0201` | nastavitve — oseben e-naslov v vrstici Cloud-Backup |
| `IMG_0207` | izvirnik `30-de-aktivna-pot`, z nezabrisano tablico |

⚠️ **Imena tu namenoma niso izpisana** — ta repozitorij je javen. Izvirniki so v
`~/Downloads/DE screen shots`, imena pa se preberejo z Vision OCR neposredno z njih.
Glej tudi opozorilo o tabeli zamenjav spodaj.

Ker sta bila zavrnjena oba posnetka strank in oba posnetka postankov, sta razdelka o zaznavi
postankov in o ločevanju službeno/zasebno na nemški strani pokrita z drugimi nemškimi
zasloni — nastavitvami zaznave (`34`) in statistiko z razdelitvijo Geschäftlich/Privat (`36`).

---

## Popravek trditve: gumb piše »Excel«, datoteka je CSV

Nemška stran je pri izvozu trdila **»Excel und PDF«**, ker tako piše gumb v aplikaciji.
`app/export.tsx:220` pa pod istim gumbom zapiše `text/csv` prek `csvName(...)` — datoteka je
CSV, ki ga Excel odpre, ne `.xlsx`. Popravljeno na **»CSV und PDF«**, kar je že prej pisalo
v SL in EN.

⚠️ Isto neskladje ostaja **v aplikaciji** (gumb `excel` → CSV) in v besedilih za App Store.
Ni popravljeno tukaj, ker je koda.

---

## Izpostavljene novosti v vseh treh jezikih

Okvir `.note` na koncu razdelka s funkcijami, v SL, EN in DE. Obe trditvi sta bili pred
zapisom preverjeni v kodi, ne po commit sporočilu:

**Natančnejše merjenje na iPhonu** (`213c558`) — `Location.Accuracy.High` je na iOS pomenil
`kCLLocationAccuracyNearestTenMeters`. Na strani je opisan **mehanizem, ne odstotek**: prej je
bila zahtevana natančnost desetih metrov, lomljenka skozi tako grobe točke v ovinkih reže.
Android nespremenjen.

**Službeno vozilo z več vozniki** (`Vehicle.sharedVehicle`, `types/vehicle.ts`) — nesledeni
kilometri se zabeležijo kot `correction` in ne kot `private_use`. Na strani je zapisano prav
to — popravek števca namesto zasebne uporabe — **brez obljube o davčnem izidu**, čeprav
komentar v kodi omenja boniteto. Isto vprašanje je dodano tudi med pogosta vprašanja v vseh
treh jezikih, ker bo ravno to ljudi zanimalo.

---

## Namerno puščeno

**Lomljeni napis na gumbu.** Trije posnetki tem kažejo `GESCHÄFTSRE` / `ISE STARTEN` — nemški
napis se lomi sredi besede. Odločitev z dne 18. 8.: posnetke uporabimo, ker dobro pokažejo tri
ozadja; napis se popravi v aplikaciji (`constants/languages.ts:31`), ne na sliki. Za popravek
teče ločena seja. Ko bo popravljen, je te tri posnetke vredno ponoviti.

**Klavzula o prevladujoči jezikovni različici** pravilnika o zasebnosti. Pri treh jezikih je
vredna razmisleka, a je pravno besedilo — odloženo na zahtevo.

---

## Preverjeno

- **Vse strani:** zgradba (uravnoteženost oznak), vse notranje povezave in **vsi zaznamki**,
  vključno z `#de` med stranmi — 8 strani, brez napake.
- **Nemška naslovnica:** 22 slik, nobena zlomljena; trojica tem se izriše.
- **Mobilni pogled** 375 px: preklopnik s tremi jeziki ne razpade.
- **Po objavi:** vseh 9 naslovov 200, vseh 13 nemških posnetkov 200.
- **Tablice po objavi:** OCR pognan nad datotekami, **prenesenimi z domene** (ne lokalnimi) —
  najde samo `LJ 01-LPT`, `LJO1LPT`, `LJO2LPT`. Nikjer `ZKG` ali `CUG`.

---

## 🔴 Tabela zamenjav je v javnem repozitoriju

`README.md` vsebuje tabelo **pravo ime → ime na strani**. Repozitorij je javen, zato je ta
tabela dosegljiva komur koli — tudi neposredno prek `raw.githubusercontent.com` in prek
iskanja po GitHubu. Kdor jo prebere, lahko **razveljavi prečiščevanje vseh posnetkov na
strani**: iz »Vertimo« nazaj v pravo ime, iz `LJ01LPT` nazaj v pravo tablico.

Tabela je starejša od te seje, 18. 8. pa je bila **razširjena** z imeni iz zavrnjenih nemških
posnetkov — s tem je bilo javno objavljenih še nekaj imen, ki jih prej ni bilo nikjer.

Smiselno je preseliti tabelo iz javnega repozitorija (v zasebni repozitorij aplikacije ali
lokalno) in tu pustiti samo postopek brez imen. ⚠️ Odstranitev iz `README.md` odstrani imena
iz **trenutne** različice, ne pa iz zgodovine gita — za to bi bil potreben prepis zgodovine.

**Odločitev čaka.**

---

## Odprto

- Tabela zamenjav v javnem repozitoriju (zgoraj) — **odloči**.
- Podpora in zasebnost sta v treh jezikih, aplikacija jih govori **sedem**. Preostali štirje
  (ES, HR, SR, RU) nimajo ne strani ne razdelka.
- Klavzula o prevladujoči različici.
- `17-statistika`, `20-stroski`, `22-widget-android`, `23-izvoz-podjetje`, `27-nastavitve-sl`
  niso uporabljeni na nobeni strani. Stanje je starejše od te seje, nisem se ga dotikal.
