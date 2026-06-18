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
    - name: "Válečné kladivo"
      slug: "valecne-kladivo"
      qty: 1
      price: "15 zl"
      weight: "2 lb"
    - name: "Dýka"
      slug: "dyka"
      qty: 1
      price: "2 zl"
      weight: "1 lb"
    - name: "Foukačka"
      slug: "foukacka"
      qty: 1
      price: "1 zl"
      weight: "1 lb"
      note: "15 střel, 5× otrávená"
  batoh:
    naradi:
      - name: "Kutilské nářadí"
        slug: "kutilske-naradi"
        qty: 1
        price: "50 zl"
        weight: "10 lb"
        note: "×2 odbornost"
      - name: "Kovářské nářadí"
        slug: "kovarske-naradi"
        qty: 1
        price: "20 zl"
        weight: "8 lb"
      - name: "Navigační pomůcky"
        slug: "navigacni-pomucky"
        qty: 1
        price: "25 zl"
        weight: "2 lb"
        note: "×2 odbornost"
      - name: "Kladivo řemeslné"
        slug: "kladivo-remeslne"
        qty: 1
        price: "1 zl"
        weight: "3 lb"
      - name: "Krumpáč"
        slug: "krumpac"
        qty: 1
        price: "2 zl"
        weight: "10 lb"
      - name: "Lopata"
        slug: "lopata"
        qty: 1
        price: "2 zl"
        weight: "5 lb"
      - name: "Kupecké váhy"
        slug: "kupecke-vahy"
        qty: 1
        price: "5 zl"
        weight: "3 lb"
    preziti:
      - name: "Léčivý lektvar"
        slug: "lecivy-lektvar"
        qty: 2
        price: "50 zl/ks"
        weight: "0.5 lb/ks"
      - name: "Železné dávky"
        slug: "zelezne-davky"
        qty: 10
        price: "5 sm/den"
        weight: "2 lb/den"
        note: "1 den jídla na osobu"
      - name: "Pochodně"
        slug: "pochodne"
        qty: 7
        price: "1 mm/ks"
        weight: "1 lb/ks"
        note: "Jasné světlo 20 stop, tlumené 20 stop, hoří 1 hodinu"
      - name: "Křesadlo"
        slug: "kresadlo"
        qty: 1
        price: "5 sm"
        weight: "1 lb"
        note: "Ocel, pazourek, hubka, dřevo"
      - name: "Měch na vodu"
        slug: "mech-na-vodu"
        qty: 1
        price: "2 sm"
        weight: "5 lb (plný)"
        note: "4 galony vody"
      - name: "Karimatka"
        slug: "karimatka"
        qty: 1
        price: "1 zl"
        weight: "7 lb"
    special:
      - name: "Trn z Mantikory"
        slug: "trn-mantikory"
        qty: 9
        price: "-"
        weight: "-"
      - name: "Opis nápisu v chrámu Luna"
        slug: "opis-napisu-luna"
        qty: 1
        price: "-"
        weight: "-"
      - name: "Mechanismus skoku"
        slug: "mechanismus-skoku"
        qty: 1
        price: "-"
        weight: "-"
        note: "vybitý"
      - name: "Mince klanu Devíti zlatých mečů"
        slug: "mince-deviti-mecu"
        qty: 1
        price: "-"
        weight: "-"
      - name: "Medvědí zub"
        slug: "medvedi-zub"
        qty: 1
        price: "-"
        weight: "-"
      - name: "List (přepis mapy)"
        slug: "list-prepis-mapy"
        qty: 10
        price: "-"
        weight: "-"
    ostatni:
      - name: "Lano"
        slug: "lano"
        qty: 1
        price: "1 sm"
        weight: "9 lb"
        note: "Konopné, 50 stop (10 sáhů)"
      - name: "Páčidlo"
        slug: "pacidlo"
        qty: 1
        price: "2 zl"
        weight: "5 lb"
      - name: "Zrcátko"
        slug: "zrcatko"
        qty: 1
        price: "5 zl"
        weight: "0.5 lb"
        note: "Ocelové, 10×13 cm"
      - name: "Pečetní vosk"
        slug: "pecetni-vosk"
        qty: 1
        price: "1 zl"
        weight: "0.25 lb"
      - name: "Skoba"
        slug: "skoba"
        qty: 10
        price: "5 mm/ks"
        weight: "0.25 lb/ks"
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
      price: "-"
      weight: "-"
    - name: "Peníze"
      slug: "penize-zazemi"
      qty: 1
      price: "300 zl"
      weight: "-"
      note: "Investice na lodi"
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
    return [`${item.name}${note}`, item.qty, item.price || "-", item.weight || "-"];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
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
    return [`${item.name}${note}`, item.qty, item.price || "-", item.weight || "-"];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
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
    return [`${item.name}${note}`, item.qty, item.price || "-", item.weight || "-"];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
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
    return [`${item.name}${note}`, item.qty, item.price || "-", item.weight || "-"];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
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
    return [`${item.name}${note}`, item.qty, item.price || "-", item.weight || "-"];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
}
```

---

## Zázemí

```dataviewjs
const inv = dv.current().inventory?.zazemi || [];
if (inv.length === 0) {
  dv.paragraph("*Prázdno*");
} else {
  const rows = inv.map((item) => {
    const note = item.note ? ` (${item.note})` : "";
    return [`${item.name}${note}`, item.qty, item.price || "-", item.weight || "-"];
  });
  dv.table(["Název", "Počet", "Cena", "Váha"], rows);
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
