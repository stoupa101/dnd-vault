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
      price: "15 zl"
      weight: "2 lb"
    - name: "Dyka"
      qty: 1
      price: "2 zl"
      weight: "1 lb"
    - name: "Foukacka"
      qty: 1
      price: "1 zl"
      weight: "1 lb"
      note: "15 strel, 5x otravena"
  batoh:
    naradi:
      - name: "Kutilske nastroje"
        qty: 1
        price: "50 zl"
        weight: "10 lb"
        note: "x2 odbornost"
      - name: "Kovarske nastroje"
        qty: 1
        price: "20 zl"
        weight: "8 lb"
      - name: "Navigacni pomucky"
        qty: 1
        price: "25 zl"
        weight: "2 lb"
        note: "x2 odbornost"
    preziti:
      - name: "Lecivy lektvar"
        qty: 2
        price: "50 zl/ks"
        weight: "0.5 lb/ks"
      - name: "Zelezne davky"
        qty: 10
        price: "5 sm/den"
        weight: "2 lb/den"
        note: "1 den jidla na osobu"
      - name: "Pochodne"
        qty: 7
        price: "1 mm/ks"
        weight: "1 lb/ks"
        note: "Jasne svetlo 20 stop, tlumene 20 stop, hori 1 hodinu"
      - name: "Kresadlo"
        qty: 1
        price: "5 sm"
        weight: "1 lb"
        note: "Ocel, pazourek, hubka, drevo"
      - name: "Mech na vodu"
        qty: 1
        price: "2 sm"
        weight: "5 lb (plny)"
        note: "4 galony vody"
      - name: "Karimatka"
        qty: 1
        price: "1 zl"
        weight: "7 lb"
    special:
      - name: "Trn z Mantikory"
        qty: 9
        price: "-"
        weight: "-"
      - name: "Opis napisu v chramu Luna"
        qty: 1
        price: "-"
        weight: "-"
      - name: "Mechanismus skoku"
        qty: 1
        price: "-"
        weight: "-"
        note: "vybity"
      - name: "Mince klanu Deviti zlatych mecu"
        qty: 1
        price: "-"
        weight: "-"
      - name: "Medvedi zub"
        qty: 1
        price: "-"
        weight: "-"
      - name: "List (prepis mapy)"
        qty: 10
        price: "-"
        weight: "-"
    ostatni:
      - name: "Lano"
        qty: 1
        price: "1 sm"
        weight: "9 lb"
        note: "Konopne, 50 stop (10 sahu)"
      - name: "Pacidlo"
        qty: 1
        price: "2 zl"
        weight: "5 lb"
      - name: "Zrcatko"
        qty: 1
        price: "5 zl"
        weight: "0.5 lb"
        note: "Ocelove, 10x13 cm"
      - name: "Pecetni vosk"
        qty: 1
        price: "1 zl"
        weight: "0.25 lb"
      - name: "Kladivo remeslne"
        qty: 1
        price: "1 zl"
        weight: "3 lb"
      - name: "Skoba"
        qty: 10
        price: "5 mm/ks"
        weight: "0.25 lb/ks"
      - name: "Krumpac"
        qty: 1
        price: "2 zl"
        weight: "10 lb"
      - name: "Lopata"
        qty: 1
        price: "2 zl"
        weight: "5 lb"
      - name: "Kupeecke vahy"
        qty: 1
        price: "5 zl"
        weight: "3 lb"
  lodi:
    - name: "Kratky mec"
      qty: 1
      price: "10 zl"
      weight: "2 lb"
      note: "1k6 bodne, lehky, vytribeny"
    - name: "Otravena sipka"
      qty: 1
      price: "-"
      weight: "-"
    - name: "Investice"
      qty: 300
      note: "zl"
log: []
---

# Inventář

> [!success] Stav
> **`= this.Penize` zl** u sebe · **`= this.Penize_celkem` zl** celkem · **`= this.Suroviny` ks** surovin · **`= this.HP`/44 HP**

> [!tip] Přehled
> Tabulky zobrazují předměty z YAML frontmatteru. Množství, cena a váha jsou uvedeny u každé položky.
> Tlačítka pro přesuny budou přidána později.

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
    return [`${item.name}${qty}${note}`, item.price || "-", item.weight || "-"];
  });
  dv.table(["Předmět", "Cena", "Váha"], rows);
}
```

---

## Batoh

### Nářadí

```dataviewjs
const inv = dv.current().inventory?.batoh?.naradi || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`, item.price || "-", item.weight || "-"];
  });
  dv.table(["Nářadí", "Cena", "Váha"], rows);
}
```

### Přežití

```dataviewjs
const inv = dv.current().inventory?.batoh?.preziti || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`, item.price || "-", item.weight || "-"];
  });
  dv.table(["Předmět", "Cena", "Váha"], rows);
}
```

### Speciál

```dataviewjs
const inv = dv.current().inventory?.batoh?.special || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`, item.price || "-", item.weight || "-"];
  });
  dv.table(["Předmět", "Cena", "Váha"], rows);
}
```

### Ostatní

```dataviewjs
const inv = dv.current().inventory?.batoh?.ostatni || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    const qty = item.qty > 1 ? ` ×${item.qty}` : "";
    return [`${item.name}${qty}${note}`, item.price || "-", item.weight || "-"];
  });
  dv.table(["Předmět", "Cena", "Váha"], rows);
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
    return [`${item.name}${qty}${note}`, item.price || "-", item.weight || "-"];
  });
  dv.table(["Předmět", "Cena", "Váha"], rows);
}
```

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
