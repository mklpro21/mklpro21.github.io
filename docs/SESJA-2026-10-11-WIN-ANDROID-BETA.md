# Seja 11. 10. 2026 (Windows) — Android v beti, novi androidni posnetki, Siri glasovni ukazi

Veja **`android-beta-posnetki`** (ne `main` — stran se še ni spremenila). Ko so dodani še
posnetki z iPhona, veja gre v `main` in šele takrat na mklpro21.com.

## Naročilo

1. Zamenjaj posnetke: UI LPT v treh ozadjih in jezikih, nov Android widget, večina slik za
   stran LPT Pic Edit (vir: `Downloads\Android Screen shot LPT in LPT pic`).
2. Android je zdaj v beti — popravi besedila; ob prijavi uporabnik izbere Android ali iOS,
   da pošljemo pravo vabilo.
3. »Siri, brez rok« → »Siri glasovni ukazi«, npr. »LPT uboga glasovne ukaze«. »Brez telefona
   v roki« je že v naslovu razdelka z widgeti, zato se pri Siri ne ponavlja.
4. Posnetkov, na katerih se vidi tablica, ne uporabi. Manjkajoče posnetke uporabnik doda z
   iPhona na Macu.

## Kaj je narejeno (vseh šest strani: `/`, `/sl/`, `/de/` in trije `pic-edit/`)

### Lazy Pro Trip

| kje | prej | zdaj |
| --- | --- | --- |
| oznaka v glavi | iPhone · zaprt preizkus | **iPhone in Android** · zaprt preizkus |
| okvir novosti | »Siri, brez rok« | nova točka **»Zdaj tudi na Androidu«** (Google Play, lasten widget) + **»Glasovni ukazi Siri (iPhone)«** |
| 03 — med vožnjo | widget iPhone, CarPlay | + **widget za Android** (`52`/`53`/`54`, v jeziku strani); napis iPhone widgeta pove »iPhone« |
| razdelek Siri | »Hey Siri — brez telefona v roki« | oznaka **iPhone**, naslov **»Hey Siri — LPT uboga glasovne ukaze«** (EN *Lazy Pro Trip obeys voice commands*, DE *LPT gehorcht Sprachbefehlen*); »v žepu« umaknjen |
| 05 — po vaše | izbirnik jezika + izbirnik ozadja (`29`) | izbirnik jezika + **trojček ozadij v jeziku strani** (EN `43`–`45`, SL `46`–`48`, DE `49`–`51` namesto `40`–`42`) |
| prijava (beta) | en gumb, samo iOS; Android »zaključna faza« | **dva gumba**: *Prijava za iPhone* / *Prijava za Android*; Androidni e-mail sprašuje po **Google računu (Gmail)**, modelu in različici Androida. Ploščici: iPhone · TestFlight, Android · Google Play |
| drobni tisk | Apple … | + »Android in Google Play sta blagovni znamki družbe Google LLC« |

### LPT Pic Edit

| kje | prej | zdaj |
| --- | --- | --- |
| naslovni par | Pred / Po (stari temni UI, `09`/`10`) | **Izrezan in osvetljen** (`55`) / **Druga barva, en dotik** (`58`) |
| Izrez in žarek | »Applov Vision« | **Vision na iPhonu, Googlov ML Kit na Androidu** (preverjeno v `lpt-pic-edit/modules/subject-extractor`); slika `57` (zlat žarek) |
| **nov** razdelek Car Beautify | — | Polish, Clarity, Contrast, Saturate, Shine; AutoFix, Reset (`FilterPanel.tsx`); slika `56` |
| Kader | `12` (pokončno) | **ležeči posnetek** `60` + točka »telefon obrnite na ležeče za večje platno« |
| kartica Tablica in obraz | samo čopič | **tablica**: vlečenje ali 4 vogali, lupa, zabris ali prekrivna tablica (bela/rumena/črna) z lastnim napisom v perspektivi; čopič za obraz; **slika `59`** (ležeče, lupa in navodila) |
| prijava | 1.2.1, en gumb | **1.3.0**, dva gumba (kot zgoraj) |

### Posnetki

- Novi: `43`–`60` (opis v `README.md` → »Androidni posnetki«).
- Odstranjeni (nič več ne kaže nanje): `09`–`12` (stari Pic Edit), `22-widget-android` (stari
  androidni widget), `29-ozadja`, `40`–`42-de-tema-*`.
- Zavrnjena: dva pokončna posnetka Blur → Plate — lupa kaže izvirno tablico. Ležeči
  (`…12-51-38`) je uporabljen kot `59`: v lupi sta le `SLO LJ` in okvir, številke ni.
- `sitemap.xml`: `lastmod` 2026-10-11 za šest spremenjenih strani.

### Preverjeno

Lokalni strežnik: vse slike na šestih straneh se naložijo (0 napak), na 375 px nobena stran
ne drsi vodoravno, oba gumba za prijavo sta na telefonu cela.

## Kaj je še treba — na Macu

### Posnetki z iPhona

1. **Nadzorna plošča v novem videzu** (Škodilak) za naslovne slike: EN `01-aktivna-pot`,
   SL `21-nadzorna-sl`, DE `30-de-aktivna-pot` še kažejo stari videz s Fordom.
2. **Widget na iPhonu** (`08-widget`) — kaže še gumb END; od 4.41 je med potjo glavni gumb
   OSVEŽI. Nov posnetek naj to pokaže (besedilo na strani to že opisuje).
3. **LPT Pic Edit na iPhonu** v novem svetlem videzu (1.3.0), če je iOS build že tam —
   na strani piše »različica 1.3.0« za obe platformi. Če iOS še ni na 1.3.0, popravi besedilo.
4. **Posnetek »pred«** (fotografija z ozadjem) — z njim se lahko vrne par Pred / Po.
5. Neobvezno: novi posnetki seznama poti, zemljevida, vozil, postankov, strank, izvoza
   (vsi so iz avgusta, stari videz), Live Activity in CarPlay. Ob vsakem preveri imena
   strank in tablice (`README.md` → »Posnetki zaslona«).

### Besedila — preveri

- **Kako poteka prijava na Androidu**: stran obljublja »Google račun dodamo med
  preizkuševalce in pošljemo povezavo za namestitev iz Google Playa«. Če gre prek
  Google skupine ali javne povezave, popravi ploščico v vseh šestih straneh.
- **Glasovni ukazi na Androidu** — stran jih ne omenja (Siri je označen »iPhone«). Če LPT
  na Androidu podpira Google Assistant, dodaj.
- **Android Auto** — stran omenja samo CarPlay. Dodaj, če je podprt.
- Drobni tisk »Widget in živa aktivnost na iPhonu zahtevata iOS 26.2« — za Android widget
  minimalna različica ni navedena.
- `podpora/` — morda vprašanje »Kako se prijavim na Androidu?«.

### Objava

1. `git checkout main && git merge android-beta-posnetki && git push`.
2. IndexNow ping (ukaz v `README.md` → »Indeksiranje«) za `/`, `/sl/`, `/de/`,
   `/pic-edit/`, `/sl/pic-edit/`, `/de/pic-edit/`.

### Od prej, nespremenjeno

- `17-statistika`, `20-stroski`, `23-izvoz-podjetje`, `27-nastavitve-sl` niso bili v rabi
  že pred to sejo — lahko se odstranijo.
- Odprte točke iz `SESJA-2026-09-27-…` (Search Console, javna tabela zamenjav v README).

---

## Nadaljevanje na Macu (11. 10. 2026) — posnetki z iPhona, Android Auto

Vir: `Downloads/Screen shots IOS new build 3 langage` (opis v `README.md` → »Posnetki z iPhona in avtomobila«).

- **Naslovna slika** EN `61`, SL `62` — nadzorna plošča s Škodilakom. DE ostaja `30`:
  nemški iPhone posnetki lomijo gumb »GESCHÄFTSRE / ISE STARTEN« (napaka v aplikaciji).
- **Widget na iPhonu** v jeziku strani (`63`–`65`), gumb REFRESH / OSVEŽI / NEU LADEN.
- **Živa aktivnost** `66` (EN, DE) in `67` (SL); **CarPlay** v jeziku strani (`68`–`70`).
- **Android Auto je podprt** — nova slika v razdelku 03 (`71`–`73`), omemba v novostih, v
  okvirju »Deluje z avtom« in v drobnem tisku (blagovna znamka).
- EN seznam vozil `03` → `74`.
- Odstranjeni neuporabljeni: `01`, `03`, `06`, `07`, `08`, `17`, `20`, `21`, `23`, `27`.

Še odprto: DE naslovna slika (napaka v aplikaciji), posnetek »pred« za Pic Edit.

Odgovori uporabnika (11. 10.): Pic Edit 1.3.0 deluje na iOS; Android prijava = vpis med
preizkuševalce in vabilo (osnutek pripravi agent, uporabnik potrdi); Google Assistant še ni,
v načrtu; Android Auto začne in konča pot (z rahlim zamikom, preizkušeno). V `podpora/`
dodana vprašanja »Kako se prijavim na preizkus?«, »CarPlay in Android Auto« in opomba, da
glasovnih ukazov na Androidu še ni — v vseh treh jezikih.
