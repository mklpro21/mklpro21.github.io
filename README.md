# mklpro21.com

Javna spletna stran za **Lazy Pro Trip** in podporno aplikacijo **LPT Pic Edit**.
Statična stran, brez gradnje — kar je v repozitoriju, je tisto, kar se streže.

> ⚠️ Ta repozitorij je **javen**. Koda aplikacij ostaja v svojih zasebnih
> repozitorijih; sem ne sodi nič, česar ne bi objavil na oglasni deski.

## Kaj je kje

```
index.html            slovenska naslovnica (Lazy Pro Trip)
en/index.html         angleška naslovnica
de/index.html         nemška naslovnica
pic-edit/             LPT Pic Edit — slovensko
en/pic-edit/          LPT Pic Edit — angleško
de/pic-edit/          LPT Pic Edit — nemško
podpora/              podpora + pogosta vprašanja (SL + EN na eni strani)
zasebnost/            pravilnik o zasebnosti (SL + EN na eni strani)
assets/css/site.css   celotno oblikovanje, ena datoteka
assets/fonts/         Jura in Geist Mono (SIL OFL) — gostujeta lokalno
assets/img/shots/     posnetki zaslona, WebP
design/               oblikovna filozofija in izhodiščni list
CNAME                 mklpro21.com
```

**Naslova, ki ju ima Apple v App Store Connect**, sta `‌/podpora/` in
`‌/zasebnost/`. Če se poti kdaj spremenita, je treba popraviti tudi vpis v ASC —
sicer pregledovalec naleti na 404.

⚠️ **Podpora in zasebnost sta samo SL + EN.** Nemški strani nanju kažeta z
napisoma »Support« in »Datenschutz«, obiskovalec pa pristane na dvojezični
strani. Če se doda nemščina, se `podpora/` in `zasebnost/` uredita **skupaj** —
naslova ostaneta ista, ker sta vpisana v ASC.

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

### Nemški posnetki (`30-de-*` … `39-de-*`)

Iz serije nemških posnetkov z dne 18. 8. 2026 jih je na strani **deset**.
Prečiščevanje:

| posnetek | kaj je bilo narejeno |
| --- | --- |
| `30-de-aktivna-pot` | tablica `LJ 62-ZKG` na fotografiji in oznaka `LJ62ZKG` v vrstici vozila **zamenjani** s prečiščenima izrezoma iz `01-aktivna-pot.webp` (ista fotografija, zamik 23 px) |
| `35-de-vozilo` | tablica `LJ87CUG` je bila zabrisana, a jo je Vision **še vedno prebral** (`LJ087-CUG`) — prekrita z mozaikom in zabrisana |
| ostalih osem | brez posegov, OCR ne najde ničesar |

**Zavrnjeni posnetki** — vsebujejo prava imena podjetij in zaseben naslov, ki
niso bili prečiščeni; če jih kdaj dodajamo, jih je treba najprej prepisati po
tabeli zgoraj:

| posnetek | kaj je na njem |
| --- | --- |
| `IMG_0203`, `IMG_0221` | seznam strank — Žabjek d.o.o., Dobles, Starman, Tehimpex, Metaloprema, Tehnodom 2, Starles |
| `IMG_0208`, `IMG_0225` | postanki in poti — McDonald's Celje, MERKUR Celje, MOL Rudnik, Trafika 3DVA **in zaseben stanovanjski naslov** |
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

## ⚠️ CNAME ni aktiven

Vsebina domene je pripravljena v `CNAME.txt`, a **ni** aktivirana — dokler DNS
kaže na Squarespace, bi aktiven `CNAME` pomenil, da `mklpro21.github.io`
preusmerja na domeno, ki še ne dela, in stran ne bi bila dosegljiva nikjer.

Po preklopu DNS zapisov (glej zgoraj) domeno vklopiš z:

```bash
git mv CNAME.txt CNAME && git commit -m "Vklop domene mklpro21.com" && git push
```

Takrat se **vse** projektne strani tega računa preselijo pod domeno —
`mklpro21.github.io/lazyprotrip-support/` postane `mklpro21.com/lazyprotrip-support/`.
Stari naslov se preusmeri, a Support in Privacy URL v App Store Connect je
vseeno pametno posodobiti na `/podpora/` in `/zasebnost/`.
