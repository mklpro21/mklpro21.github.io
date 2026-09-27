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
- **Pravilnik nima imena in naslova upravljavca** (GDPR 13(1)(a)) — samo »MKLpro« v nogi in
  e-naslov. Rabi pravno ime in naslov.
- **Čiščenje `user-logs/`** v repozitoriju aplikacije starejših od 12 mesecev — politika to
  zdaj obljublja. Najstarejši dnevniki so z avgusta 2026, rok torej prvič poteče avgusta 2027.
- **RevenueCat ob izbrisu računa** stranke ne izbriše samodejno — politika zato piše »na
  zahtevo«. Ko bo v kodi, popravi besedilo.
- Tabela zamenjav v `README.md` (javna) — odločitev še vedno čaka (glej 18. 8.).
