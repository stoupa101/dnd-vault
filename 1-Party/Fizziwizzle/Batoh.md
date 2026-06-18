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
    - "Valecne kladivo"
    - "Dyka"
    - "Foukacka (15 strel, 5x otravena)"
  batoh:
    - "Lecivy lektvar (2x)"
    - "Kadidlo (10 dni)"
    - "Zasoby jidla (10 dni)"
    - "Pochodne (7x)"
    - "Kresadlo"
    - "Lano (5 sahu)"
    - "Pacidlo"
    - "Zrcatko"
    - "Pecetni vosk"
    - "Mech na vodu"
  naradi:
    - "Kutilske (x2 odbornost)"
    - "Kovarske"
    - "Navigacni (x2 odbornost)"
  tezke:
    - "Kladivo (remeslne)"
    - "Skoba (10x)"
    - "Krumpac"
    - "Lopata"
    - "Kupeecke vahy"
    - "Karimatka"
  specialni:
    - "9x trn z Mantikory"
    - "Opis napisu v chramu Luna"
    - "Mechanismus skoku (vybity)"
    - "Mince klanu Deviti zlatych mecu"
    - "Medvedi zub"
    - "10x list (prepis mapy)"
  lodi:
    - "Kratky mec (1k6 bodne)"
    - "Otravena sipka"
    - "300 zl (investice)"
log: []
---

# Inventář

> [!success] Stav
> **`= this.Penize` zl** u sebe · **`= this.Penize_celkem` zl** celkem · **`= this.Suroviny` ks** surovin · **`= this.HP`/44 HP**

---

## Rychlý přehled

### Opasek (rychlý přístup)

```dataview
TABLE without id item as "Předmět"
FROM "1-Party/Fizziwizzle/Batoh.md"
FLATTEN inventory.opasek as item
WHERE file.name = "Batoh"
SORT item
```

### Batoh

```dataview
TABLE without id item as "Předmět"
FROM "1-Party/Fizziwizzle/Batoh.md"
FLATTEN inventory.batoh as item
WHERE file.name = "Batoh"
SORT item
```

### Nářadí

```dataview
TABLE without id item as "Nářadí"
FROM "1-Party/Fizziwizzle/Batoh.md"
FLATTEN inventory.naradi as item
WHERE file.name = "Batoh"
SORT item
```

### Těžké / stavební

```dataview
TABLE without id item as "Předmět"
FROM "1-Party/Fizziwizzle/Batoh.md"
FLATTEN inventory.tezke as item
WHERE file.name = "Batoh"
SORT item
```

### Speciální předměty

```dataview
TABLE without id item as "Předmět"
FROM "1-Party/Fizziwizzle/Batoh.md"
FLATTEN inventory.specialni as item
WHERE file.name = "Batoh"
SORT item
```

### Na lodi (zázemí)

```dataview
TABLE without id item as "Předmět"
FROM "1-Party/Fizziwizzle/Batoh.md"
FLATTEN inventory.lodi as item
WHERE file.name = "Batoh"
SORT item
```

---

## Přesuny mezi lokacemi

> [!tip] Jak používat
> Klikni na tlačítko → předmět se přesune + automaticky se zapíše do logu s časem

### Opasek → Batoh

```meta-bind-button
label: "Kladivo → Batoh"
hidden: true
id: "move-kladivo-opasek-batoh"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.filter(i => !i.includes('Kladivo'))"
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "[...x, 'Valecne kladivo']"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Valecne kladivo z opasku do batohu']"
```

```meta-bind-button
label: "Dýka → Batoh"
hidden: true
id: "move-dyka-opasek-batoh"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.filter(i => !i.includes('Dyka'))"
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "[...x, 'Dyka']"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Dyka z opasku do batohu']"
```

```meta-bind-button
label: "Foukačka → Batoh"
hidden: true
id: "move-foukacka-opasek-batoh"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.filter(i => !i.includes('Foukacka'))"
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "[...x, 'Foukacka (15 strel, 5x otravena)']"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Foukacka z opasku do batohu']"
```

`BUTTON[move-kladivo-opasek-batoh]` `BUTTON[move-dyka-opasek-batoh]` `BUTTON[move-foukacka-opasek-batoh]`

### Batoh → Opasek

```meta-bind-button
label: "Lektvar → Opasek"
hidden: true
id: "move-lektvar-batoh-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.filter(i => !i.includes('Lektvar'))"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, 'Lecivy lektvar (2x)']"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Lecivy lektvar z batohu na opasek']"
```

```meta-bind-button
label: "Pacidlo → Opasek"
hidden: true
id: "move-pacidlo-batoh-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.filter(i => !i.includes('Pacidlo'))"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, 'Pacidlo']"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Pacidlo z batohu na opasek']"
```

```meta-bind-button
label: "Zrcatko → Opasek"
hidden: true
id: "move-zrcatko-batoh-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.batoh
    evaluate: true
    value: "x.filter(i => !i.includes('Zrcatko'))"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, 'Zrcatko']"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Zrcatko z batohu na opasek']"
```

`BUTTON[move-lektvar-batoh-opasek]` `BUTTON[move-pacidlo-batoh-opasek]` `BUTTON[move-zrcatko-batoh-opasek]`

### Opasek → Lodi (zázemí)

```meta-bind-button
label: "Vše → Loď"
hidden: true
id: "move-all-opasek-lodi"
style: warning
actions:
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "[...x, ...getMetadata('inventory.opasek')]"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Vse z opasku na lod (zazemi)']"
```

`BUTTON[move-all-opasek-lodi]`

### Lodi → Opasek

```meta-bind-button
label: "Kratky mec → Opasek"
hidden: true
id: "move-mec-lodi-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.lodi
    evaluate: true
    value: "x.filter(i => !i.includes('mec'))"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "[...x, 'Kratky mec (1k6 bodne)']"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Kratky mec z lode na opasek']"
```

`BUTTON[move-mec-lodi-opasek]`

---

## Historie přesunů

> [!note] Log
> Automaticky zaznamenává každý přesun s přesným časem. Slouží jako důkaz pro PJ.

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
