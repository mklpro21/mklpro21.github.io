# Seja 27. 9. 2026 (Windows) — angleščina privzeta, stran usklajena z aplikacijo 4.40, odprtje za iskalnike

Repozitorija `mklpro21/mklpro21.github.io` in `mklpro21/lazyprotrip-support`, veja `main`.
Na Windows ju prej ni bilo — klonirana v `C:\mklpro21.github.io` in `C:\lazyprotrip-support`.

## Naročilo

1. Posodobi stran skladno z aplikacijo (izbris podatkov, »logCat«, …).
2. Privzeti jezik strani je **angleščina**; ob nejasnosti je angleščina glavni prevod.
3. Stran je »zaprta« — dostopna samo z neposrednim vpisom naslova. Odpri jo.

### Kaj je pomenilo »zaprta«

Tehnično je bila odprta: `mklpro21.com`, `www.`, `http://` in `mklpro21.github.io` vsi vrnejo
200 ali 301 na `https://mklpro21.com/`, `robots.txt` dovoli vse, `noindex` ni nikjer. Iskanje
`site:mklpro21.com` pa **ni vrnilo ničesar** — strani ni poznal noben iskalnik. Uporabnik je
potrdil: to je pomen. Iskalnik strani sam ne najde, dokler nanjo ne kaže nobena povezava.

### Kaj je »logCat«

Ne sistemski `logcat` Androida (tega aplikacija nikamor ne pošilja), ampak **štetje poti in
izvozov** — knjiga kvote (`services/quota/`) in anonimna mesečna vrstica (`usage_monthly`),
po kateri se ve, kdaj se konča brezplačna raba in začne Premium. Opisano v politiki zasebnosti
kot »števec uporabe« in »anonimno mesečno štetje«.

## Odločitve uporabnika (27. 9.)

| Tema | Odločitev |
| --- | --- |
| Android na strani | ostane »zaključna faza« |
| Free/Pro na naslovnici | **ne** — samo v politiki zasebnosti (RevenueCat, oblak brez sledi, merjenje) |
| Hramba poslanih dnevnikov sledenja | **največ 12 mesecev** (prej je politika trdila »po odpravi izbrišemo«, dnevniki pa so trajno v `user-logs/`) |

## Kaj se je spremenilo

### Struktura (angleščina privzeta)

| naslov | prej | zdaj |
| --- | --- | --- |
| `/` | slovenščina | **angleščina** |
| `/sl/` | — | slovenščina |
| `/en/`, `/en/pic-edit/` | angleščina | preusmeritev na `/`, `/pic-edit/` (meta refresh + JS, ohrani `#`) |
| `/pic-edit/` | slovenščina | angleščina |
| `/sl/pic-edit/` | — | slovenščina |
| `/podpora/`, `/zasebnost/` | SL → EN → DE | **EN → SL (`#sl`) → DE (`#de`)**, `#en` = vrh |
| `/404.html` | — | nova |

Datoteke so premaknjene z `git mv` (zgodovina ostane). Preklopnik jezikov je povsod v
vrstnem redu **EN / SL / DE**. `hreflang="x-default"` kaže na angleško stran. Slovenski
strani kažeta na `/podpora/#sl` in `/zasebnost/#sl`.

### Vsebina

- **Okvir novosti** (vse tri naslovnice): »New · version 4.40« — izbris računa v aplikaciji,
  surov CSV vseh poti, privzeti jezik telefona (sicer angleščina). Avgustovski novosti
  (natančnost na iPhonu, vozilo z več vozniki) sta umaknjeni; drugo ostaja v podpori.
- **»Your data stays yours«**: stavek »edino, kar zapusti telefon, so koordinate postanka in
  zemljevid« ni bil več točen (anonimno štetje, stikala s strežnika, RevenueCat) — zdaj našteje
  primere in se za popoln seznam sklicuje na politiko; »no analytics« → »no third-party
  analytics or tracking«.
- **Podpora** — nova vprašanja: *Do I need an account?* (e-pošta, Google, Apple na iPhonu),
  *Sending us the tracking log* (`#tracking-log`), *Exporting all my data* (surov CSV),
  *Which language*, Xiaomi/Redmi/POCO → vodnik MIUI; *Deleting data* razširjen na izbris
  računa (`#delete-data`).
- **Politika zasebnosti** — datum **27. september 2026** v vseh treh. Novo: prijava z
  e-pošto/geslom in Googlom (prej samo Apple), oblačna kopija vključuje stranke in števec
  uporabe, osnovna kopija brez GPS sledi (Pro s sledmi, naložena sled ostane do izbrisa
  računa), **RevenueCat** kot obdelovalec (ZDA, SCC v njihovem DPA — preverjeno na
  revenuecat.com/dpa), anonimno mesečno štetje (brez identifikatorja, brez seje), javna
  stikala s strežnika, diktiranje na Androidu (Google), dnevniki največ 12 mesecev, razdelek
  **izbris računa** (`#delete-account` / `#izbris-racuna` / `#konto-loeschen`), surov CSV pri
  pravicah, pravica do pritožbe pri Informacijskem pooblaščencu.

Trditve o izbrisu računa so preverjene v živi bazi (samo branje): `delete_own_account()`
izbriše vrstico v `auth.users`, vse štiri tabele kopij (`trip_`, `vehicle_`, `cost_`,
`settings_backups`) imajo `ON DELETE CASCADE`, datotek v Storage ni.

### Stari repozitorij `lazyprotrip-support`

Na `mklpro21.com/lazyprotrip-support/privacy.html` je visela **kopija politike s 13. 8.** —
po tej posodobitvi bi trdila drugače kot veljavna. `index.html` in `privacy.html` sta zdaj
preusmeritvi na `/podpora/` in `/zasebnost/`.

### Odprtje za iskalnike

- `sitemap.xml`: nova struktura, `lastmod`, brez `/en/`.
- Ključ **IndexNow** v korenu (`72cf4c1c….txt`); po objavi poslani vsi naslovi (Bing, Yandex,
  Seznam, Naver). Postopek v `README.md` → »Indeksiranje«.
- **Google** IndexNow ne podpira — potrebna je Search Console z lastnikovo prijavo (koraki v
  `README.md`). To ostaja uporabniku.

## Logotip MKLpro21 (dopolnitev iste seje)

Vir: `Documents\MKLpro21\MKLpro21 logo.zip` (Grok). Arhiv vsebuje **plasti**, ki jih je orodje
izrezalo iz ene slike, ne končnih datotek:

| plast | uporabno? |
| --- | --- |
| `stylized-m-logo.png` (436×348) | ✅ znak »M«, modro-turkizen preliv, čisto prosojno ozadje |
| `mklpro21.png` (461×112) | ⚠️ napis — temnomoder (`#03182D`) na **neprosojni** sivi podlagi (`#DDD`) |
| `illegible.png`, `light-gray-background.png` | ❌ odrezek znaka in podlaga z izrezom |

Obdelava (PIL): znak obrezan na vsebino in pomanjšan na 128 px višine → `assets/img/mklpro21-mark.png`
(160×128, prikaz 24 px). Napisu je podlaga izrezana iz svetlosti (alfa = (218 − L) / 206, gladi
robove) in besedilo prebarvano v `--text` `#dfe9f6`, ker bi bil temen napis na temni strani neviden
→ `assets/img/mklpro21-wordmark.png` (440×95, prikaz 14 px, prosojnost 0,72).

Umestitev: **podpis avtorja v nogi vseh osmih strani** (`.maker` v `site.css`), vrstica nad drobnim
tiskom. Glava ostaja logotip Lazy Pro Trip — stran predstavlja aplikacijo, MKLpro21 je izdelovalec.
Ime v drobnem tisku in v politiki poenoteno z logotipom: `MKLpro` → **`MKLpro21`**.

Ostali trije arhivi v isti mapi (`logo2`–`logo4`, 17. 9.) niso bili ne pregledani ne uporabljeni —
uporabnik je izbral `MKLpro21 logo.zip`.

## Aplikacija (repozitorij LPT)

`privacyPolicyUrl('sl')` vrne `…/zasebnost/#sl` (prej brez sidra) — test posodobljen.
Velja od naslednjega builda; **buildi do vključno 4.40 (24)** slovenske uporabnike pripeljejo
na angleški vrh strani, od koder je `Slovenščina ↓` en dotik.

## Neodvisna preverba politike proti kodi

Ločen pregled (verifier) je vse trditve angleške politike, podpore in obeh okvirjev naslovnice
preveril proti kodi aplikacije. Ujel je **dve vrzeli, obe popravljeni v vseh treh jezikih**:

1. 🔴 **Google Places — tudi na iPhonu.** Stara politika (že 13. 8.) je pisala »koordinate postanka
   gredo Applu *ali* Googlu«. `services/geocoding.ts` pa ob vsakem naslovu vzporedno pokliče še
   `places.googleapis.com` (`findNearbyPoi`) — **na obeh platformah**, in ne le za postanke, ampak
   tudi za začetek in konec poti (`TripContext.tsx`). Zdaj: sistemski geokoder (Apple na iPhonu,
   Google na Androidu) **in** na obeh Googlov Places za ime podjetja.
2. Mesečna vrstica nosi še `paywall_enabled` — dodano »ali so bili plačljivi paketi vklopljeni«.

Vse ostalo (poti v menijih, vsebina oblaka, prijave, tok izbrisa, RevenueCat, surov CSV, glava
dnevnika — brez modela telefona, privzeti jezik, odsotnost analitike v `package.json`) se ujema.

## Preverjeno

- Lokalni strežnik: **261 notranjih povezav** na 11 straneh, vsi zaznamki obstajajo, oznake
  uravnotežene — 0 napak.
- Preusmeritev `/en/` → `/` v brskalniku; na 375 px nobena stran ne drsi vodoravno.
- Zaznamek `#delete-account` pristane na razdelku.

## Odprto

- **Google Search Console** (uporabnik): lastnost *Domena* `mklpro21.com`, TXT pri Squarespaceu,
  oddaja `sitemap.xml`.
- **Play Console → Account deletion URL:** `https://mklpro21.com/zasebnost/#delete-account`.
- **App Store Connect:** Support URL in Privacy URL ostaneta `/podpora/` in `/zasebnost/` —
  preveri, da ne kažeta še na `mklpro21.github.io/lazyprotrip-support/…` (bi delalo prek
  preusmeritve, a je ovinek).
- ✅ **Upravljavec vpisan** (dopolnitev iste seje): razdelek *Who is responsible* / *Kdo je
  odgovoren* / *Verantwortlicher* (`#controller`, `#upravljavec`, `#verantwortlicher`) — »Matej
  Kljun, Slovenija · team@mklpro21.com; MKLpro je ime znamke, ne registrirano podjetje«.
  Registriranega podjetja ni (MklPro s.p. je zaprt), zato je upravljavec fizična oseba; domači
  naslov namenoma ni objavljen (GDPR 13(1)(a) zahteva identiteto in kontakt, e-naslov zadošča).
  ⚠️ **Pred vklopom Pro** ne bo več dovolj: DSA status trgovca v obeh trgovinah objavi naslov in
  telefon, redna prodaja naročnin pa verjetno zahteva registrirano dejavnost (preveri računovodja).
  Ko bo registrirana, v politiko vpiši njeno ime in poslovni naslov.
- **Čiščenje `user-logs/`** v repozitoriju aplikacije starejših od 12 mesecev — politika to
  zdaj obljublja. Najstarejši dnevniki so z avgusta 2026, rok torej prvič poteče avgusta 2027.
- **RevenueCat ob izbrisu računa** stranke ne izbriše samodejno — politika zato piše »na
  zahtevo«. Ko bo v kodi, popravi besedilo.
- Tabela zamenjav v `README.md` (javna) — odločitev še vedno čaka (glej 18. 8.).
