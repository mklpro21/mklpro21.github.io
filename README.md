# mklpro21.com

Javna spletna stran za **Lazy Pro Trip** in podporno aplikacijo **LPT Pic Edit**.
Statična stran, brez gradnje — kar je v repozitoriju, je tisto, kar se streže.

> ⚠️ Ta repozitorij je **javen**. Koda aplikacij ostaja v svojih zasebnih
> repozitorijih; sem ne sodi nič, česar ne bi objavil na oglasni deski.

## Kaj je kje

```
index.html            angleška naslovnica (Lazy Pro Trip) — PRIVZETA od 27. 9. 2026
sl/index.html         slovenska naslovnica
de/index.html         nemška naslovnica
pic-edit/             LPT Pic Edit — angleško
sl/pic-edit/          LPT Pic Edit — slovensko
de/pic-edit/          LPT Pic Edit — nemško
en/, en/pic-edit/     samo preusmeritvi na / in /pic-edit/ (stari angleški naslovi)
podpora/              podpora + pogosta vprašanja (EN, SL, DE na eni strani)
zasebnost/            pravilnik o zasebnosti (EN, SL, DE na eni strani)
404.html              stran za neobstoječe naslove (GitHub Pages jo streže sam)
<ključ>.txt           ključ IndexNow (32 hex znakov) — glej »Indeksiranje«
assets/css/site.css   celotno oblikovanje, ena datoteka
assets/fonts/         Jura in Geist Mono (SIL OFL) — gostujeta lokalno
assets/img/shots/     posnetki zaslona, WebP
assets/img/mklpro21-* znak »M« in napis MKLpro21 — podpis avtorja v nogi vseh strani
design/               oblikovna filozofija in izhodiščni list
docs/                 zapisi sej — kaj se je na strani spremenilo in zakaj
CNAME                 mklpro21.com
```

**Privzeti jezik je angleščina** (odločitev 27. 9. 2026): v primeru nejasnosti je
angleško besedilo glavni prevod, `hreflang="x-default"` kaže na angleško stran.
Do 27. 9. je bila na `/` slovenščina, angleščina pa na `/en/`.

**Naslova, ki ju ima Apple v App Store Connect**, sta `‌/podpora/` in
`‌/zasebnost/`. Če se poti kdaj spremenita, je treba popraviti tudi vpis v ASC —
sicer pregledovalec naleti na 404.

**Podpora in zasebnost sta trojezični na eni strani** (EN, nato SL, nato DE),
ločeni z `<hr>` in dosegljivi prek zaznamkov `#sl` in `#de` (`#en` je vrh strani).
Slovenski strani nanju kažeta z `#sl`, nemški z `#de`. Naslova sama ostaneta
`‌/podpora/` in `‌/zasebnost/`, ker sta vpisana v ASC — jezik se dodaja **v** stran,
ne kot nova pot.

**Aplikacija odpira pravilnik z zaznamkom po jeziku** (`privacyPolicyUrl()` v
`constants/appInfo.ts` repozitorija aplikacije). Buildi do vključno 4.40 (24) za
slovenščino pošljejo `/zasebnost/` brez zaznamka — ti od 27. 9. pristanejo na
angleškem vrhu.

**Izbris računa** (Google Play »Account deletion URL«, Apple 5.1.1(v)):
`/zasebnost/#delete-account` (EN), `#izbris-racuna` (SL), `#konto-loeschen` (DE).
Če se zaznamek spremeni, popravi vpis v Play Console.

⚠️ Ob spremembi pravilnika o zasebnosti je treba popraviti **vse tri** različice
in datum v vseh treh. Trenutno vse tri navajajo **27. september 2026** (RevenueCat,
prijava z e-pošto/Googlom/Applom, oblak brez sledi v osnovnem paketu, števec uporabe,
anonimno mesečno štetje, izbris računa, hramba dnevnikov največ 12 mesecev).

## Predogled

```bash
python3 -m http.server 8765
```

Nato odpri `http://localhost:8765/`. Odpiranje datotek prek `file://` **ne
deluje**, ker so poti do CSS in slik absolutne (`/assets/…`).

## Posnetki zaslona

Vsi posnetki so **prečiščeni**: imena strank, naslovi, e-pošta, davčna številka
in registrske tablice so zamenjani z izmišljenimi. Zamenjave so dosledne — ista
stranka ima na vseh zaslonih isto novo ime:

🔴 **Spodnja tabela izniči prečiščevanje in je javna.** Ta repozitorij je javen,
zato jo lahko kdor koli prebere — tudi prek `raw.githubusercontent.com` in iskanja
po GitHubu — in vsak posnetek na strani prevede nazaj v prava imena in tablice.
Smiselno jo je preseliti v zasebni repozitorij in tu pustiti samo postopek.
⚠️ Odstranitev iz te datoteke je ne odstrani iz zgodovine gita. **Odločitev čaka**
— glej `docs/SESJA-2026-08-18-MAC-NEMSKA-RAZLICICA.md`.

| pravo | na strani |
| --- | --- |
| Bmc, Tehnodom | Vertimo |
| Žabjek d.o.o., Marex | Nordel |
| Dobles | Kremita |
| Starles | Tavrin |
| Metalka zastopstva TORNA | Belvor zastopstva |
| Metaloprema | Movita |
| Gamat d.o.o. | Arkona d.o.o. |
| PIL IMPEX d.o.o. | Lumea d.o.o. |
| Tectronik Industries Slovenija d.o.o. | Vertimo d.o.o. |
| LJ62ZKG / LJ87CUG | LJ01LPT / LJ02LPT |
| osebni e-naslovi | uporabnik@primer.si |

⚠️ **Ob dodajanju novega posnetka preveri isto.** Najhitreje z Applovim Vision
OCR: preberi besedilo s slike in poišči prava imena, preden datoteko commitaš.

### Nemški posnetki (`30-de-*` … `42-de-*`)

Iz serije nemških posnetkov z dne 18. 8. 2026 jih je na strani **trinajst**.
Prečiščevanje:

| posnetek | kaj je bilo narejeno |
| --- | --- |
| `30-de-aktivna-pot` | tablica `LJ 62-ZKG` na fotografiji in oznaka `LJ62ZKG` v vrstici vozila **zamenjani** s prečiščenima izrezoma iz `01-aktivna-pot.webp` (ista fotografija, zamik 23 px) |
| `35-de-vozilo` | tablica `LJ87CUG` je bila zabrisana, a jo je Vision **še vedno prebral** (`LJ087-CUG`) — prekrita z mozaikom in zabrisana |
| `40-de-tema-carbon`, `41-de-tema-usnje`, `42-de-tema-svetla` | ista tablica: zamegljeni sta bili samo srednji dve števki, `LJ` in `-CUG` sta ostala berljiva s prostim očesom (Vision je zaradi packe odpovedal, človek ne) — prekrita z mozaikom |
| ostalih osem | brez posegov, OCR ne najde ničesar |

⚠️ **Vision OCR ni zadosten preizkus za tablice.** Packa čez sredino besedila
zavede OCR, človeku pa ostane dovolj. Pri tablicah poglej tudi sam, povečano.

Posnetki tem `40`–`42` (z napisom, ki se je lomil sredi besede) so bili 11. 10. 2026
**odstranjeni** in zamenjani z `49`–`51` — glej spodaj.

### Androidni posnetki (`43-*` … `60-*`, 11. 10. 2026)

Vir: `Downloads\Android Screen shot LPT in LPT pic` (Redmi, 8.–11. 10.), pretvorjeni v
WebP 760 px (široki: widget 1080 × 600 izrez, ležeči Pic Edit 1200 px).

| posnetek | kaj |
| --- | --- |
| `43`–`45` EN, `46`–`48` SL, `49`–`51` DE | nadzorna plošča LPT v treh ozadjih (carbon, usnje, svetlo), vsaka v svojem jeziku |
| `52`–`54` | widget za Android na domačem zaslonu (EN, DE, SL), izrez iz celega zaslona |
| `55`–`58`, `60` | LPT Pic Edit 1.3.0: žarek (turkizen, zlat, rožnat), Car Beautify, ležeči način |
| `59` | Pic Edit, Blur → Plate ležeče (`…12-51-38`) — lupa kaže le `SLO LJ`, grb in zabrisan okvir trgovca; številka ni vidna |

Vozilo je povsod `Škodilak · LJ 01 LPT` — prekrivna tablica iz Pic Edita, OCR ni potreben.
**Zavrnjena:** posnetka zavihka Blur → Plate `…12-51-14` in `…12-51-51` — lupa v kotu kaže **izvirno tablico** pod prekrivno. Za stran se uporabi
posnetek brez lupe (ali z drugim avtom).

### Posnetki z iPhona in avtomobila (`61-*` … `74-*`, 11. 10. 2026)

Vir: `Downloads/Screen shots IOS new build 3 langage` (iPhone 8. 10., LPT 4.42; zasloni
v avtu so fotografije). Pretvorjeni s `cwebp -q 80` (`brew install webp`; `sips` WebP ne zapiše).

| posnetek | vir | kaj |
| --- | --- | --- |
| `61` EN, `62` SL | `IMG_0468`, `0465` (mapa `Screen shots UI 3 lang and 2 cars`) | naslovna slika: nadzorna plošča, ozadje carbon, prekrivna tablica `LJ 01 LPT` |
| `63` EN, `64` SL, `65` DE | `IMG_0397`, `0398`, `0394` | widget na iPhonu z gumbom REFRESH / OSVEŽI / NEU LADEN (izrez) |
| `66` EN (tudi DE), `67` SL | `IMG_0389`, `0400` | živa aktivnost na zaklenjenem zaslonu |
| `68` EN, `69` SL, `70` DE | `IMG_0385`, `0401`, `0396` | živa aktivnost v CarPlay |
| `71` EN, `72` SL, `73` DE | `IMG_0404`, `0417`, `0409` | Android Auto med potjo |
| `74` EN | `IMG_0426` | seznam vozil (`LJ 01 LPT`, `LJ 02 LPT`) |
| `76`, `77` | `IMG_0471`, `0473` (mapa `LPT pic screen shot`) | Pic Edit na iPhonu, izrez platna: pred (ozadje, zabrisana tablica) / po (izrezan, vijoličen žarek kot v `78`, prekrivna tablica `LJ 02 LPT`; posnetek iz klepeta 11. 10.) — v razdelku 01 vseh treh `pic-edit/` |
| `78` | posnetek iz klepeta 11. 10. (iPhone, EN) | isti Ford v Lazy Pro Trip: nadzorna plošča z modrim žarkom, `LJ 02 LPT` — ob paru Pred / Po |

Tablica na fotografiji avta je v aplikaciji že zakrita (vidi se le `LJ`). **Zavrnjen:**
`IMG_0384` — obvestilo o postanku kaže pravo ime stranke. Nemška nadzorna plošča na iPhonu
(`IMG_0428`, `0429`, `0469`, `0470`) lomi gumb sredi besede (»GESCHÄFTSRE / ISE«), zato je DE naslovna slika
ostala `30-de-aktivna-pot` — do 11. 10. zvečer, glej spodaj.

### Nemška aktivna pot in zemljevidi (`79-*` … `82-*`, 11. 10. 2026 zvečer)

Vir: `Downloads\Screen shot Android DE in maps` (Redmi, 11. 10.), WebP 760 px.

| posnetek | vir | kaj |
| --- | --- | --- |
| `79` DE | `…20-34-01` | naslovna slika DE: aktivna pot, carbon, gumb FAHRT BEENDEN — nadomešča `30` |
| `83` DE | `…21-00-56` (s telefona prek adb) | izbirnik jezika »Sprache«, izbran Deutsch — nadomešča `19` na DE strani |
| `80` DE, `81` EN, `82` SL | `…20-34-25`, `…20-35-06`, `…20-35-31` | zemljevid službene poti Koper–Ljubljana–Celje — nadomešča `32` (DE) in `02` (EN, SL) |

Na zemljevidih so le mesta in žebljički postankov, brez naslovov in imen strank. Neuporabljen:
`…20-33-43` (ista nemška pot, svetlo ozadje). `02`, `30` in `32` so odstranjeni.

**Zavrnjeni posnetki** — vsebujejo prava imena podjetij in zaseben naslov, ki
niso bili prečiščeni; če jih kdaj dodajamo, jih je treba najprej prepisati po
tabeli zgoraj:

| posnetek | kaj je na njem |
| --- | --- |
| `IMG_0203`, `IMG_0221` | seznam strank — sedem resničnih imen podjetij |
| `IMG_0208`, `IMG_0225` | postanki in poti — štiri resnična podjetja z naslovi **in zaseben stanovanjski naslov** |
| `IMG_0201` | nastavitve — oseben e-naslov v vrstici Cloud-Backup |
| `IMG_0207` | izvirnik posnetka `30-de-aktivna-pot`, z nezabrisano tablico |

## Oblikovanje

Vodilo je v [`design/OBLIKOVNA-FILOZOFIJA.md`](design/OBLIKOVNA-FILOZOFIJA.md)
(»Odometrična tišina«). Na kratko: temno polje, ozka paleta, lasne črte, klinične
monospace oznake, ena velika gesta na odsek, praznina kot nosilec. Krivulja v
ozadju naslovnice je ista kot na listu `design/list-01-odometricna-tisina.png`.

Barve in tipografija so v vrhu `assets/css/site.css` kot spremenljivke. Modra
`#2D9CFF` je vzeta iz ikone in besednega znaka — uporablja se **samo tam, kjer
nekaj pomeni**, ne kot okras.

## Objava na GitHub Pages

Repozitorij mora biti javen, v nastavitvah pa Pages nastavljen na vejo `main`,
mapa `/` (root). `CNAME` že vsebuje domeno.

Pri Squarespaceu (tam je domena registrirana) je treba zamenjati **samo** A
zapise in `www`:

| zapis | vrednost |
| --- | --- |
| A `@` | `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` |
| CNAME `www` | `mklpro21.github.io` |

⚠️ **MX zapisov se ne dotikaj** — pošta `team@mklpro21.com` teče prek Googla in
je hkrati `SUPPORT_EMAIL` v aplikaciji.

## Domena

`CNAME` je aktiven od commita `3b346d9`. Vse različice naslova (`http://`,
`www.`, `mklpro21.github.io`) GitHub Pages preusmeri s 301 na
`https://mklpro21.com/` — kanonični naslov je **brez `www`**.

Projektne strani tega računa živijo pod isto domeno —
`mklpro21.github.io/lazyprotrip-support/` je `mklpro21.com/lazyprotrip-support/`.
Od 27. 9. 2026 sta tam samo še preusmeritvi na `/podpora/` in `/zasebnost/`
(repozitorij `mklpro21/lazyprotrip-support`), da ne visi podvojena, zastarela
politika zasebnosti.

## Indeksiranje

Do 27. 9. 2026 strani ni poznal noben iskalnik (`site:mklpro21.com` prazno), čeprav
je bila tehnično odprta. Iskalnik strani sam od sebe ne najde, dokler nanjo ne kaže
nobena povezava.

- **Bing, Yandex, Seznam, Naver** — prek IndexNow. Ključ je v datoteki
  `<ključ>.txt` v korenu (vsebina = ime brez `.txt`). Po vsaki večji spremembi:

  ```bash
  curl -X POST https://api.indexnow.org/indexnow -H "Content-Type: application/json; charset=utf-8" -d '{"host":"mklpro21.com","key":"<ključ>","keyLocation":"https://mklpro21.com/<ključ>.txt","urlList":["https://mklpro21.com/"]}'
  ```

- **Google** IndexNow ne podpira; potrebna je **Google Search Console** z
  lastnikovo prijavo: dodaj lastnost *Domena* `mklpro21.com`, potrdi jo z zapisom
  TXT pri Squarespaceu (MX zapisov se ne dotikaj), nato *Sitemaps* →
  `https://mklpro21.com/sitemap.xml` in *Pregled URL-ja* → *Zahtevaj indeksiranje*
  za `/`, `/sl/` in `/de/`.
