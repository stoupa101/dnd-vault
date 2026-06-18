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
    - name: Válečné kladivo
      slug: valecne-kladivo
      qty: 1
      price: 15 zl
      weight: 2 lb
    - name: Dýka
      slug: dyka
      qty: 1
      price: 2 zl
      weight: 1 lb
    - name: Foukačka
      slug: foukacka
      qty: 1
      price: 1 zl
      weight: 1 lb
      note: Střelná zbraň, dostřel 5/20 stop
    - name: "Šipka do foukačky"
      slug: "sipka-foukacka"
      qty: 10
      price: "5 me"
      weight: "0.25 lb"
      note: "1 bodné poškození"
    - name: "Šipka otrávená"
      slug: "sipka-otravena"
      qty: 5
      price: "."
      weight: "0.25 lb"
      note: "1k4+2 jedové poškození"
  batoh:
    naradi:
      - name: Kutilské nářadí
        slug: kutilske-naradi
        qty: 1
        price: 50 zl
        weight: 10 lb
        note: ×2 odbornost
      - name: Kovářské nářadí
        slug: kovarske-naradi
        qty: 1
        price: 20 zl
        weight: 8 lb
      - name: Navigační pomůcky
        slug: navigacni-pomucky
        qty: 1
        price: 25 zl
        weight: 2 lb
        note: ×2 odbornost
      - name: Kladivo řemeslné
        slug: kladivo-remeslne
        qty: 1
        price: 1 zl
        weight: 3 lb
      - name: Krumpáč
        slug: krumpac
        qty: 1
        price: 2 zl
        weight: 10 lb
      - name: Lopata
        slug: lopata
        qty: 1
        price: 2 zl
        weight: 5 lb
      - name: Kupecké váhy
        slug: kupecke-vahy
        qty: 1
        price: 5 zl
        weight: 3 lb
      - name: Páčidlo
        slug: pacidlo
        qty: 1
        price: 2 zl
        weight: 5 lb
    preziti:
      - name: Léčivý lektvar
        slug: lecivy-lektvar
        qty: 2
        price: 50 zl
        weight: 0.5 lb
        note: 2d4+2 HP
      - name: Železné dávky
        slug: zelezne-davky
        qty: 10
        price: 5 st/den
        weight: 2 lb/den
        note: 1 den jídla na osobu
      - name: Pochodeň
        slug: pochoden
        qty: 7
        price: 1 me
        weight: 1 lb
        note: Jasné světlo 20 stop, tlumené 20 stop, hoří 1 hodinu
      - name: Křesadlo
        slug: kresadlo
        qty: 1
        price: 5 st
        weight: 1 lb
        note: Ocel, pazourek, hubka, dřevo
      - name: Měch na vodu
        slug: mech-na-vodu
        qty: 1
        price: 2 st
        weight: 5 lb (plný)
        note: 4 galony vody
      - name: Karimatka
        slug: karimatka
        qty: 1
        price: 1 zl
        weight: 7 lb
    ostatni:
      - name: Lano
        slug: lano
        qty: 5
        price: 1 st
        weight: 9 lb
        note: Konopné, 5 sáhů (25 stop)
      - name: Zrcátko
        slug: zrcatko
        qty: 1
        price: 5 zl
        weight: 0.5 lb
        note: Ocelové, 10×13 cm
      - name: Pečetní vosk
        slug: pecetni-vosk
        qty: 1
        price: 1 zl
        weight: 0.25 lb
      - name: Skoba
        slug: skoba
        qty: 10
        price: 5 me
        weight: 0.25 lb
    special:
      - name: Trn z Mantikory
        slug: trn-mantikory
        qty: 9
        price: .
        weight: .
      - name: Opis nápisu v chrámu Luna
        slug: opis-napisu-luna
        qty: 1
        price: .
        weight: .
      - name: Mechanismus skoku
        slug: mechanismus-skoku
        qty: 1
        price: .
        weight: .
        note: vybitý
      - name: Mince klanu Devíti zlatých mečů
        slug: mince-deviti-mecu
        qty: 1
        price: .
        weight: .
      - name: Medvědí zub
        slug: medvedi-zub
        qty: 1
        price: .
        weight: .
      - name: List (přepis mapy)
        slug: list-prepis-mapy
        qty: 10
        price: .
        weight: .
  zazemi:
    - name: "Krátký meč"
      slug: "kratky-mec"
      qty: 1
      price: "10 zl"
      weight: "2 lb"
      note: "1k6 bodné, lehký, vytříbený"
    - name: "Otrávená šipka"
      slug: "otravena-sipka"
      qty: 1
      price: "."
      weight: "."
    - name: "Peníze"
      slug: "penize-zazemi"
      qty: 1
      price: "300 zl"
      weight: "."
      note: "Investice na lodi"
log: []
---

# Inventář

> [!success] Stav
> **`= this.Penize` zl** u sebe · **`= this.Penize_celkem` zl** celkem · **`= this.Suroviny` ks** surovin · **`= this.HP`/44 HP**

> [!tip] Přesuny
> Klikni na tlačítko → přesune se 1 kus. Pokud cíl položku už má, zvýší se množství. Pokud množství klesne na 0, položka zmizí.

---

## Rychlý přístup (Opasek)

```dataviewjs
const inv = dv.current().inventory?.opasek || [];
if (inv.length === 0) { dv.paragraph("*Prázdno*"); } else {
  const rows = inv.filter(i => i.qty > 0).map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    return [`${item.name}${note}`, item.qty, item.price || ".", item.weight || "."];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
}
```

### Přesun do Zázemí 🚢

```meta-bind-button
label: "🚢 Válečné kladivo"
hidden: true
id: "opasek-valecne-kladivo-to-zazemi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map(i => i.slug === 'valecne-kladivo' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.some(i => i.slug === 'valecne-kladivo') ? x.map(i => i.slug === 'valecne-kladivo' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Válečné kladivo',slug:'valecne-kladivo',qty:1,price:'15 zl',weight:'2 lb'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Valecne kladivo z opasku do zazemi']"
```

```meta-bind-button
label: "🚢 Dýka"
hidden: true
id: "opasek-dyka-to-zazemi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map(i => i.slug === 'dyka' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.some(i => i.slug === 'dyka') ? x.map(i => i.slug === 'dyka' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Dýka',slug:'dyka',qty:1,price:'2 zl',weight:'1 lb'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Dyka z opasku do zazemi']"
```

```meta-bind-button
label: "🚢 Foukačka"
hidden: true
id: "opasek-foukacka-to-zazemi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map(i => i.slug === 'foukacka' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.some(i => i.slug === 'foukacka') ? x.map(i => i.slug === 'foukacka' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Foukačka',slug:'foukacka',qty:1,price:'1 zl',weight:'1 lb',note:'Střelná zbraň, dostřel 5/20 stop'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Foukacka z opasku do zazemi']"
```

```meta-bind-button
label: " Šipka do foukačky"
hidden: true
id: "opasek-sipka-foukacka-to-zazemi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map(i => i.slug === 'sipka-foukacka' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.some(i => i.slug === 'sipka-foukacka') ? x.map(i => i.slug === 'sipka-foukacka' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Šipka do foukačky',slug:'sipka-foukacka',qty:1,price:'5 me',weight:'0.25 lb',note:'1 bodné poškození'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Sipka do foukacky z opasku do zazemi']"
```

```meta-bind-button
label: "🚢 Šipka otrávená"
hidden: true
id: "opasek-sipka-otravena-to-zazemi"
style: default
actions:
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.map(i => i.slug === 'otravena-sipka' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.some(i => i.slug === 'otravena-sipka') ? x.map(i => i.slug === 'sipka-otravena' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Šipka otrávená',slug:'sipka-otravena',qty:1,price:'.',weight:'0.25 lb',note:'1k4+2 jedové poškození'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Sipka otravena z opasku do zazemi']"
```

`BUTTON[opasek-valecne-kladivo-to-zazemi]` `BUTTON[opasek-dyka-to-zazemi]` `BUTTON[opasek-foukacka-to-zazemi]` `BUTTON[opasek-sipka-foukacka-to-zazemi]` `BUTTON[opasek-sipka-otravena-to-zazemi]`

---

## Batoh

### Nářadí

```dataviewjs
const inv = dv.current().inventory?.batoh?.naradi || [];
if (inv.length === 0) { dv.paragraph("*Prázdno*"); } else {
  const rows = inv.filter(i => i.qty > 0).map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    return [`${item.name}${note}`, item.qty, item.price || ".", item.weight || "."];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
}
```

### Přežití

```dataviewjs
const inv = dv.current().inventory?.batoh?.preziti || [];
if (inv.length === 0) { dv.paragraph("*Prázdno*"); } else {
  const rows = inv.filter(i => i.qty > 0).map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    return [`${item.name}${note}`, item.qty, item.price || ".", item.weight || "."];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
}
```

### Ostatní

```dataviewjs
const inv = dv.current().inventory?.batoh?.ostatni || [];
if (inv.length === 0) { dv.paragraph("*Prázdno*"); } else {
  const rows = inv.filter(i => i.qty > 0).map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    return [`${item.name}${note}`, item.qty, item.price || ".", item.weight || "."];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
}
```

### Speciál

```dataviewjs
const inv = dv.current().inventory?.batoh?.special || [];
if (inv.length === 0) { dv.paragraph("*Prázdno*"); } else {
  const rows = inv.filter(i => i.qty > 0).map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    return [`${item.name}${note}`, item.qty, item.price || ".", item.weight || "."];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
}
```

---

## Zázemí

```dataviewjs
const inv = dv.current().inventory?.zazemi || [];
if (inv.length === 0) { dv.paragraph("*Prázdno*"); } else {
  const rows = inv.filter(i => i.qty > 0).map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    return [`${item.name}${note}`, item.qty, item.price || ".", item.weight || "."];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
}
```

### Přesun na Opasek 

```meta-bind-button
label: " Krátký meč"
hidden: true
id: "zazemi-kratky-mec-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.map(i => i.slug === 'kratky-mec' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.some(i => i.slug === 'kratky-mec') ? x.map(i => i.slug === 'kratky-mec' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Krátký meč',slug:'kratky-mec',qty:1,price:'10 zl',weight:'2 lb',note:'1k6 bodné, lehký, vytříbený'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Kratky mec ze zazemi na opasek']"
```

```meta-bind-button
label: "🎒 Otrávená šipka"
hidden: true
id: "zazemi-otravena-sipka-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.map(i => i.slug === 'otravena-sipka' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.some(i => i.slug === 'otravena-sipka') ? x.map(i => i.slug === 'otravena-sipka' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Otrávená šipka',slug:'otravena-sipka',qty:1,price:'.',weight:'.'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Otravena sipka ze zazemi na opasek']"
```

```meta-bind-button
label: " Peníze"
hidden: true
id: "zazemi-penize-to-opasek"
style: primary
actions:
  - type: updateMetadata
    bindTarget: inventory.zazemi
    evaluate: true
    value: "x.map(i => i.slug === 'penize-zazemi' ? {...i, qty: i.qty - 1} : i).filter(i => i.qty > 0)"
  - type: updateMetadata
    bindTarget: inventory.opasek
    evaluate: true
    value: "x.some(i => i.slug === 'penize-zazemi') ? x.map(i => i.slug === 'penize-zazemi' ? {...i, qty: i.qty + 1} : i) : [...x, {name:'Peníze',slug:'penize-zazemi',qty:1,price:'300 zl',weight:'.',note:'Investice na lodi'}]"
  - type: updateMetadata
    bindTarget: log
    evaluate: true
    value: "[...x, new Date().toLocaleString('cs-CZ') + ' - Presunuto: Penize ze zazemi na opasek']"
```

`BUTTON[zazemi-kratky-mec-to-opasek]` `BUTTON[zazemi-otravena-sipka-to-opasek]` `BUTTON[zazemi-penize-to-opasek]`

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

```dataview
TABLE without id entry as "Záznam"
FROM "1-Party/Main/Batoh.md"
FLATTEN log as entry
WHERE file.name = "Batoh"
SORT entry DESC
LIMIT 20
```

---

## Plánované / rozpracované

- [ ] Gadget pro Zalamyra: krátký meč s ledovým zraněním + vystřelování ledových šipek
- [ ] Stříblak (alchymistické mořidlo) - 4 dny výroby, 25 zl materiál
- [ ] Automatická kopáčka (pro Klaka)
- [ ] Opisovačka textů (pro Klaka)
- [ ] Elektrické kladivo (pro Klaka)

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

Hustý perleťový povlak na lodí dřevo. 2× životnost ve slaném prostředí, zabraňuje hnilobě.
- 1 dávka = 10 m², výroba 4 dny, materiál 25 zl
- Ingredience: olej do lucerny, mušle, krev slizovice, včelí vosk, naplavené dřevo, kyselina
