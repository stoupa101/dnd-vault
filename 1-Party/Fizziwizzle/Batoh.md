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

---

## Přehled inventáře

### Opasek (rychlý přístup)

```dataviewjs
const inv = dv.current().inventory?.opasek || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item, i) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    const btnId = `opasek-${i}`;
    return [`${item.name}${qty}${note}`, `[🎒](#${btnId}-to-batoh) [✋](#${btnId}-to-hand) [🍖](#${btnId}-consume) [🚢](#${btnId}-to-lodi)`];
  });
  dv.table(["Předmět", "Akce"], rows);
}
```

### Batoh

```dataviewjs
const inv = dv.current().inventory?.batoh || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item, i) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    const btnId = `batoh-${i}`;
    return [`${item.name}${qty}${note}`, `[](#${btnId}-to-opasek) [✋](#${btnId}-to-hand) [](#${btnId}-consume) [](#${btnId}-to-lodi)`];
  });
  dv.table(["Předmět", "Akce"], rows);
}
```

### Nářadí

```dataviewjs
const inv = dv.current().inventory?.naradi || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`, "—"];
  });
  dv.table(["Nářadí", ""], rows);
}
```

### Těžké / stavební

```dataviewjs
const inv = dv.current().inventory?.tezke || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`, "—"];
  });
  dv.table(["Předmět", ""], rows);
}
```

### Speciální předměty

```dataviewjs
const inv = dv.current().inventory?.specialni || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`, "—"];
  });
  dv.table(["Předmět", ""], rows);
}
```

### Na lodi (zázemí)

```dataviewjs
const inv = dv.current().inventory?.lodi || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item, i) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    const btnId = `lodi-${i}`;
    return [`${item.name}${qty}${note}`, `[🎒](#${btnId}-to-opasek) [✋](#${btnId}-to-hand)`];
  });
  dv.table(["Předmět", "Akce"], rows);
}
```

---

## Tlačítka přesunů

> [!tip] Ikony akcí
> 🎒 = přesun do batohu | ✋ = do ruky (opasek) | 🍖 = zkonzumovat/použít | 🚢 = na loď (zázemí)
> Klikni na ikonu v tabulce výše → automaticky se přesune 1 kus + zapíše do logu

### Z opasku

```meta-bind-button
label: "Kladivo → Batoh"
hidden: true
id: "opasek-0-to-batoh"
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
label: "Kladivo → Ruka"
hidden: true
id: "opasek-0-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Valecne kladivo (z opasku)']"
```

```meta-bind-button
label: "Kladivo → Loď"
hidden: true
id: "opasek-0-to-lodi"
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
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Valecne kladivo z opasku na lod']"
```

```meta-bind-button
label: "Dýka → Batoh"
hidden: true
id: "opasek-1-to-batoh"
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
label: "Dýka → Ruka"
hidden: true
id: "opasek-1-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Dyka (z opasku)']"
```

```meta-bind-button
label: "Dýka → Loď"
hidden: true
id: "opasek-1-to-lodi"
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
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Dyka z opasku na lod']"
```

```meta-bind-button
label: "Foukačka → Batoh"
hidden: true
id: "opasek-2-to-batoh"
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
label: "Foukačka → Ruka"
hidden: true
id: "opasek-2-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Foukacka (z opasku)']"
```

```meta-bind-button
label: "Foukačka → Loď"
hidden: true
id: "opasek-2-to-lodi"
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
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Foukacka z opasku na lod']"
```

### Z batohu

```meta-bind-button
label: "Lektvar → Opasek"
hidden: true
id: "batoh-0-to-opasek"
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
label: "Lektvar → Ruka"
hidden: true
id: "batoh-0-to-hand"
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
label: "Lektvar → Konzumace"
hidden: true
id: "batoh-0-consume"
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
label: "Lektvar → Loď"
hidden: true
id: "batoh-0-to-lodi"
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
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Lecivy lektvar z batohu na lod']"
```

```meta-bind-button
label: "Pochodeň → Opasek"
hidden: true
id: "batoh-3-to-opasek"
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
label: "Pochodeň → Ruka"
hidden: true
id: "batoh-3-to-hand"
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
label: "Pochodeň → Předat"
hidden: true
id: "batoh-3-consume"
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
label: "Pacidlo → Opasek"
hidden: true
id: "batoh-6-to-opasek"
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
label: "Pacidlo → Ruka"
hidden: true
id: "batoh-6-to-hand"
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
label: "Zrcátko → Opasek"
hidden: true
id: "batoh-7-to-opasek"
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
label: "Zrcátko → Ruka"
hidden: true
id: "batoh-7-to-hand"
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

### Z lodi

```meta-bind-button
label: "Krátký meč → Opasek"
hidden: true
id: "lodi-0-to-opasek"
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
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Kratky mec z lode na opasek']"
```

```meta-bind-button
label: "Krátký meč → Ruka"
hidden: true
id: "lodi-0-to-hand"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "x.map((item, i) => i === 0 ? {...item, qty: item.qty - 1} : item).filter(item => item.qty > 0)"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Do ruky: Kratky mec (z lode)']"
```

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
