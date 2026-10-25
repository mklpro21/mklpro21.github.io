# Seja 25. 10. 2026 (Windows) — politika zasebnosti LPT Pic Edit za 1.3 (osnutek, EN/SL/DE)

Veja **`pic-edit-zasebnost`** (z `main`, neodvisna od veje `pogoji-uporabe`) — **ni potisnjeno,
ni objavljeno**. Objava po odobritvi uporabnika.

Izhodišče: analiza vrzeli Pic Edit (`lpt-pic-edit/docs/SESJA-2026-10-25-WIN-VARNOST-PRAVNO.md`,
točka **B1**): noga strani `/pic-edit/` je kazala na politiko **LPT**, ki Pic Edit ne omenja, in v
repozitoriju ni zapisano, kateri URL je vpisan v App Store Connect in Play Console.

## Kaj je narejeno

| Datoteka | Sprememba |
| --- | --- |
| `pic-edit/zasebnost/index.html` | **nova stran** — EN zgoraj, sidri `#sl` in `#de`, 12 poglavij v vsakem jeziku |
| noge `pic-edit/`, `sl/pic-edit/`, `de/pic-edit/` | *Privacy / Zasebnost / Datenschutz* → `/pic-edit/zasebnost/` (+ `#sl`, `#de`) |
| `sitemap.xml` | `/pic-edit/zasebnost/` (vstavljeno pred `/podpora/`, da se ne tepe z vejo `pogoji-uporabe`, ki dodaja na konec) |

## Vsebina — samo različica 1.3 (brez oglasov in prijave)

Fotografije ne zapustijo telefona; izvoz PNG v album »LPT Pic Edit«; lokacija iz fotografij se ne
bere; dovoljenja šele ob Kamera / Galerija / Export PNG · **odstranitev ozadja**: iPhone Vision na
napravi; **Android ML Kit prek storitev Google Play pošilja Googlu tehnične podatke o uporabi**
(naprava, aplikacija, meritve delovanja in napak — po Googlovem razkritju), ne fotografij · poročila o
sesutjih (če jih uporabnik dovoli v nastavitvah telefona), e-pošta · **pravna podlaga** (6(1)(b)/(f)
GDPR — LPT politika je nima, glej LPT B2) · česa ne počnemo · hramba · pravice · otroci · spremembe
(»pred različico z oglasi ali prijavo bo stran posodobljena«).

Osnutek za build z oglasi (`lpt-pic-edit/docs/OSNUTEK-ZASEBNOST-PIC-EDIT.md`) ostane ločen; ob tistem
buildu nadomesti to besedilo na istem URL-ju.

## Neodvisen pregled (verifier) — REQUEST CHANGES → popravljeno

Preveril je vse trditve proti `C:\lpt-pic-edit` (koda, `app.json`, zlit manifest, `expo-media-library`,
`expo-image-picker`) in Googlovo razkritje ML Kit. Potrdil: brez omrežja v `src/`, brez analitike/oglasov
v `package.json`, PNG iz Skie brez EXIF, `exif` ni vklopljen, iOS Vision brez omrežja, brez `AD_ID`.

| Ugotovitev | Popravek (EN/SL/DE) |
| --- | --- |
| `ACCESS_MEDIA_LOCATION` je v 1.3 deklariran (`app.json:36,54`, `isAccessMediaLocationEnabled`) in ga `expo-media-library` ob Export PNG zahteva | stran to pove odkrito: doda ga knjižnica, aplikacija ga ne uporablja, odstranjen bo |
| ML Kit pošilja tudi **identifikatorje namestitve**; Google ga sam imenuje »analitika uporabe« | dodano; »brez lastnega analitičnega orodja« in »razen zgoraj opisanih podatkov ML Kit«; podatkov ne prejmemo, Google jih obdeluje po svojem pravilniku |
| »nam ne pošlje ničesar« proti poročilom o sesutjih | »aplikacija **sama** nam ne pošlje ničesar«; razdelek »Kaj prejmemo« |
| galerija ne zahteva dovoljenja (sistemski izbirnik); kamera in album da | opisano po gumbih |
| »fotografije nikoli ne zapustijo telefona« ne drži ob iCloud / Google Photos / Android backup | »aplikacija nikoli ne naloži« + stavek o varnostnih kopijah telefona |
| model se lahko prenese že ob namestitvi | »ob namestitvi ali ob prvi uporabi« |
| »anonimna« poročila | »ki vas ne identificirajo« |

## Odprto (ni na tej strani — v aplikaciji in trgovinah)

1. **Povezava na politiko v aplikaciji** — Apple 5.1.1(i) in Play User Data jo zahtevata; `InfoModal.tsx`
   ima samo spletno stran in e-pošto. Naslednji build.
2. **Play Data safety**: ML Kit telemetrija (identifikatorji, podatki o aplikaciji in delovanju) — izjava
   »no data collected« bi nasprotovala tej strani. iOS »Data Not Collected« ostane.
3. `ACCESS_MEDIA_LOCATION` blokirati; zlit manifest ima tudi `READ_MEDIA_VIDEO`/`READ_MEDIA_AUDIO`
   (Play *Photo and video permissions*). Lokalni `android/` je zastarel (1.2.1) — preveri AAB 1.3 (8).
4. Poštni naslov upravljavca — po registraciji dejavnosti.
5. URL v App Store Connect in Play Console nastavi na `https://mklpro21.com/pic-edit/zasebnost/` po objavi.
