---
tags:
  - inventar
  - tinkerer
Penize: 182
Penize_celkem: 482
Suroviny: 50
HerniDatum: 4.6.1358
HP: 44
inventory:
  opasek:
    - name: "Valecne kladivo"
      qty: 1
    - name: "Dyka"
      qty: 1
    - name: "Foukacka"
      qty: 1
      note: "15 strel, 5x otravena"
  batoh:
    - name: "Lecivy lektvar"
      qty: 2
    - name: "Kadidlo"
      qty: 1
      note: "10 dni"
    - name: "Zasoby jidla"
      qty: 1
      note: "10 dni"
    - name: "Pochodne"
      qty: 7
    - name: "Kresadlo"
      qty: 1
    - name: "Lano"
      qty: 1
      note: "5 sahu"
    - name: "Pacidlo"
      qty: 1
    - name: "Zrcatko"
      qty: 1
    - name: "Pecetni vosk"
      qty: 1
    - name: "Mech na vodu"
      qty: 1
  naradi:
    - name: "Kutilske nastroje"
      qty: 1
      note: "x2 odbornost"
    - name: "Kovarske nastroje"
      qty: 1
    - name: "Navigacni pomucky"
      qty: 1
      note: "x2 odbornost"
  tezke:
    - name: "Kladivo remeslne"
      qty: 1
    - name: "Skoba"
      qty: 10
    - name: "Krumpac"
      qty: 1
    - name: "Lopata"
      qty: 1
    - name: "Kupeecke vahy"
      qty: 1
    - name: "Karimatka"
      qty: 1
  specialni:
    - name: "Trn z Mantikory"
      qty: 9
    - name: "Opis napisu v chramu Luna"
      qty: 1
    - name: "Mechanismus skoku"
      qty: 1
      note: "vybity"
    - name: "Mince klanu Deviti zlatych mecu"
      qty: 1
    - name: "Medvedi zub"
      qty: 1
    - name: "List (prepis mapy)"
      qty: 10
  lodi:
    - name: "Kratky mec"
      qty: 1
      note: "1k6 bodne, lehky, vytribeny"
    - name: "Otravena sipka"
      qty: 1
    - name: "Investice"
      qty: 300
      note: "zl"
log: []
---

# Inventář

> [!success] Stav
> **`= this.Penize` zl** u sebe · **`= this.Penize_celkem` zl** celkem · **`= this.Suroviny` ks** surovin · **`= this.HP`/44 HP**

> [!tip] Jak přesouvat
> 1. Najdi předmět v tabulce výše
> 2. Klikni na odpovídající tlačítko v sekci "Přesuny" níže
> 3. Předmět se přesune (1 kus) + zapíše se do logu s časem
> 4. Tabulka se aktualizuje automaticky (Dataview čte YAML)

---

## Rychlý přístup (Opasek)

```dataviewjs
const inv = dv.current().inventory?.opasek || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`];
  });
  dv.table(["Předmět"], rows);
}
```

### Přesuny z opasku

```meta-bind-button
label: "🎒 Kladivo → Batoh"
hidden: true
id: "opasek-kladivo-to-batoh"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "[...x, {name: 'Valecne kladivo', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Valecne kladivo z opasku do batohu']"
```

```meta-bind-button
label: "✋ Kladivo → Do ruky"
hidden: true
id: "opasek-kladivo-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Valecne kladivo (z opasku)']"
```

```meta-bind-button
label: "🚢 Kladivo → Zázemí"
hidden: true
id: "opasek-kladivo-to-lodi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "[...x, {name: 'Valecne kladivo', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Valecne kladivo z opasku do zazemi']"
```

```meta-bind-button
label: "🎒 Dýka → Batoh"
hidden: true
id: "opasek-dyka-to-batoh"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map((item, i) => i === 1 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "[...x, {name: 'Dyka', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Dyka z opasku do batohu']"
```

```meta-bind-button
label: "✋ Dýka → Do ruky"
hidden: true
id: "opasek-dyka-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Dyka (z opasku)']"
```

```meta-bind-button
label: "🚢 Dýka → Zázemí"
hidden: true
id: "opasek-dyka-to-lodi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map((item, i) => i === 1 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "[...x, {name: 'Dyka', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Dyka z opasku do zazemi']"
```

```meta-bind-button
label: "🎒 Foukačka → Batoh"
hidden: true
id: "opasek-foukacka-to-batoh"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map((item, i) => i === 2 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "[...x, {name: 'Foukacka', qty: 1, note: '15 strel, 5x otravena'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Foukacka z opasku do batohu']"
```

```meta-bind-button
label: "✋ Foukačka → Do ruky"
hidden: true
id: "opasek-foukacka-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Foukacka (z opasku)']"
```

```meta-bind-button
label: "🚢 Foukačka → Zázemí"
hidden: true
id: "opasek-foukacka-to-lodi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map((item, i) => i === 2 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "[...x, {name: 'Foukacka', qty: 1, note: '15 strel, 5x otravena'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Foukacka z opasku do zazemi']"
```

`BUTTON[opasek-kladivo-to-batoh]` `BUTTON[opasek-kladivo-to-hand]` `BUTTON[opasek-kladivo-to-lodi]`

`BUTTON[opasek-dyka-to-batoh]` `BUTTON[opasek-dyka-to-hand]` `BUTTON[opasek-dyka-to-lodi]`

`BUTTON[opasek-foukacka-to-batoh]` `BUTTON[opasek-foukacka-to-hand]` `BUTTON[opasek-foukacka-to-lodi]`

---

## Batoh

```dataviewjs
const inv = dv.current().inventory?.batoh || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`];
  });
  dv.table(["Předmět"], rows);
}
```

### Přesuny z batohu

```meta-bind-button
label: " Lektvar → Opasek"
hidden: true
id: "batoh-lektvar-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, {name: 'Lecivy lektvar', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Lecivy lektvar z batohu na opasek']"
```

```meta-bind-button
label: "✋ Lektvar → Do ruky"
hidden: true
id: "batoh-lektvar-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Lecivy lektvar (z batohu)']"
```

```meta-bind-button
label: "🍖 Lektvar → Zkonzumovat"
hidden: true
id: "batoh-lektvar-consume"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Zkonzumovano: Lecivy lektvar']"
```

```meta-bind-button
label: "🚢 Lektvar → Zázemí"
hidden: true
id: "batoh-lektvar-to-lodi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "[...x, {name: 'Lecivy lektvar', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Lecivy lektvar z batohu do zazemi']"
```

```meta-bind-button
label: "🎒 Pochodeň → Opasek"
hidden: true
id: "batoh-pochoden-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 3 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, {name: 'Pochodne', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Pochodne z batohu na opasek']"
```

```meta-bind-button
label: " Pochodeň → Do ruky"
hidden: true
id: "batoh-pochoden-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 3 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Pochodne (z batohu)']"
```

```meta-bind-button
label: "🍖 Pochodeň → Předat kolegovi"
hidden: true
id: "batoh-pochoden-give"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 3 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Predano kolegovi: Pochodne']"
```

```meta-bind-button
label: "🎒 Pacidlo → Opasek"
hidden: true
id: "batoh-pacidlo-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 6 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, {name: 'Pacidlo', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Pacidlo z batohu na opasek']"
```

```meta-bind-button
label: " Pacidlo → Do ruky"
hidden: true
id: "batoh-pacidlo-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 6 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Pacidlo (z batohu)']"
```

```meta-bind-button
label: "🎒 Zrcátko → Opasek"
hidden: true
id: "batoh-zrcatko-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 7 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, {name: 'Zrcatko', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Zrcatko z batohu na opasek']"
```

```meta-bind-button
label: "✋ Zrcátko → Do ruky"
hidden: true
id: "batoh-zrcatko-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.map((item, i) => i === 7 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Zrcatko (z batohu)']"
```

`BUTTON[batoh-lektvar-to-opasek]` `BUTTON[batoh-lektvar-to-hand]` `BUTTON[batoh-lektvar-consume]` `BUTTON[batoh-lektvar-to-lodi]`

`BUTTON[batoh-pochoden-to-opasek]` `BUTTON[batoh-pochoden-to-hand]` `BUTTON[batoh-pochoden-give]`

`BUTTON[batoh-pacidlo-to-opasek]` `BUTTON[batoh-pacidlo-to-hand]`

`BUTTON[batoh-zrcatko-to-opasek]` `BUTTON[batoh-zrcatko-to-hand]`

---

## Batoh: Nářadí

```dataviewjs
const inv = dv.current().inventory?.naradi || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`];
  });
  dv.table(["Nářadí"], rows);
}
```

---

## Batoh: Těžké / stavební

```dataviewjs
const inv = dv.current().inventory?.tezke || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`];
  });
  dv.table(["Předmět"], rows);
}
```

---

## Batoh: Speciální předměty

```dataviewjs
const inv = dv.current().inventory?.specialni || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`];
  });
  dv.table(["Předmět"], rows);
}
```

---

## Zázemí (Loď)

```dataviewjs
const inv = dv.current().inventory?.lodi || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`];
  });
  dv.table(["Předmět"], rows);
}
```

### Přesuny ze zázemí

```meta-bind-button
label: "🎒 Krátký meč → Opasek"
hidden: true
id: "lodi-mec-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, {name: 'Kratky mec', qty: 1, note: '1k6 bodne, lehky, vytribeny'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Kratky mec ze zazemi na opasek']"
```

```meta-bind-button
label: "✋ Krátký meč → Do ruky"
hidden: true
id: "lodi-mec-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Kratky mec (ze zazemi)']"
```

```meta-bind-button
label: "🎒 Otrávená šipka → Opasek"
hidden: true
id: "lodi-sipka-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "x.map((item, i) => i === 1 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, {name: 'Otravena sipka', qty: 1}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Otravena sipka ze zazemi na opasek']"
```

```meta-bind-button
label: "✋ Otrávená šipka → Do ruky"
hidden: true
id: "lodi-sipka-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "x.map((item, i) => i === 1 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Otravena sipka (ze zazemi)']"
```

`BUTTON[lodi-mec-to-opasek]` `BUTTON[lodi-mec-to-hand]`

`BUTTON[lodi-sipka-to-opasek]` `BUTTON[lodi-sipka-to-hand]`

---

## Vyčištění logu

```meta-bind-button
label: "🗑️ Vymazat log"
hidden: true
id: "clear-log"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: log
    evaluate: false
    value: []
```

`BUTTON[clear-log]`

---

## Historie přesunů

> [!note] Log
> Automaticky zaznamenává každý přesun s přesným časem. Slouží jako důkaz pro PJ.
> Klikni "🗑️ Vymazat log" pro vyčištění (např. na začátku nového sezení).

```dataview
TABLE without id entry as "Záznam"
FROM "1-Party/Fizziwizzle/Batoh.md"
FLATTEN log as entry
WHERE file.name = "Batoh"
SORT entry DESC
LIMIT 20
```

---

## Plánované / rozpracované

- [ ] Gadget pro Zalamyra: kratky mec s ledovym zranenim + vystrelovani ledovych sipek
- [ ] Stribilak (alchymisticke moridlo) - 4 dny vyroby, 25 zl material
- [ ] Automaticka kopacka (pro Klaka)
- [ ] Opisovacka textu (pro Klaka)
- [ ] Elektricke kladivo (pro Klaka)

---

## Referenční předměty

### Krátký ledový meč tinkerera

Pro Zalamyra. Jílec se stříbrnými drátky a modrými krystaly, páčka a zásobník ledových šipek.

- Melee: **1k6 bodné + 1k4 chladné**
- Ranged: 20/60 stop, **1k4 chladné** (INT mod na útok)
- Mrazivý dotek: +1k4 chladné při zásahu
- Vrhací mechanismus: 3-5 střel/krátký odpočinek, vyžaduje údržbu
- Upgrade potenciál: +dmg, slow, kapacita

### Stříblak (alchymistické mořidlo)

Hustý perleťový povlak na lodí dřevo. 2x životnost ve slaném prostředí, zabraňuje hnilobě.
- 1 dávka = 10 m², výroba 4 dny, materiál 25 zl
- Ingredience: olej do lucerny, mušle, krev slizovice, včelí vosk, naplavené dřevo, kyselina
