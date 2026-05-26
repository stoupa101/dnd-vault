---
NoteIcon: player
aliases:
  - Klik
  - Jiskra
tags:
  - player
  - dashboard
Player: Fizziwizzle "Klik" Gadgetgrind
Class:
  - Tinkerer (Parní rytíř)
Race:
  - Skalní gnóm
level: 5
hp: 40
max_hp: 44
ac: 19
modifier: 3
pasperc: 17
Penize: 182
Suroviny: 50
HerniDatum: 2.6.1358
damage: 5
Status: Active
---

# Klik - Dashboard

> [!info] Skalní gnóm · Tinkerer (Parní rytíř) · Lvl 5 · NN · Nebelun (Gond)
> Jazyky: Obecná, Gnómština · Odezírání ze rtů

---

## HP

```meta-bind-button
label: "-5"
hidden: true
id: "hp-minus-5"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: hp
    evaluate: true
    value: "Math.max(0, x - 5)"
```

```meta-bind-button
label: "-2"
hidden: true
id: "hp-minus-2"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: hp
    evaluate: true
    value: "Math.max(0, x - 2)"
```

```meta-bind-button
label: "-1"
hidden: true
id: "hp-minus-1"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: hp
    evaluate: true
    value: "Math.max(0, x - 1)"
```

```meta-bind-button
label: "+1"
hidden: true
id: "hp-plus-1"
style: primary
actions:
  - type: updateMetadata
    bindTarget: hp
    evaluate: true
    value: "Math.min(getMetadata('max_hp'), x + 1)"
```

```meta-bind-button
label: "+2"
hidden: true
id: "hp-plus-2"
style: primary
actions:
  - type: updateMetadata
    bindTarget: hp
    evaluate: true
    value: "Math.min(getMetadata('max_hp'), x + 2)"
```

```meta-bind-button
label: "+5"
hidden: true
id: "hp-plus-5"
style: primary
actions:
  - type: updateMetadata
    bindTarget: hp
    evaluate: true
    value: "Math.min(getMetadata('max_hp'), x + 5)"
```

```meta-bind-button
label: "Full"
hidden: true
id: "hp-full"
style: primary
actions:
  - type: updateMetadata
    bindTarget: hp
    evaluate: true
    value: "getMetadata('max_hp')"
```

**HP: `VIEW[{hp}][text]` / `VIEW[{max_hp}][text]`**
`BUTTON[hp-minus-5]` `BUTTON[hp-minus-2]` `BUTTON[hp-minus-1]` | `BUTTON[hp-plus-1]` `BUTTON[hp-plus-2]` `BUTTON[hp-plus-5]` `BUTTON[hp-full]`

---

## Peníze

```meta-bind-button
label: "-10"
hidden: true
id: "zl-minus-10"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: Penize
    evaluate: true
    value: "Math.round((x - 10) * 10) / 10"
```

```meta-bind-button
label: "-5"
hidden: true
id: "zl-minus-5"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: Penize
    evaluate: true
    value: "Math.round((x - 5) * 10) / 10"
```

```meta-bind-button
label: "-1"
hidden: true
id: "zl-minus-1"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: Penize
    evaluate: true
    value: "Math.round((x - 1) * 10) / 10"
```

```meta-bind-button
label: "+1"
hidden: true
id: "zl-plus-1"
style: primary
actions:
  - type: updateMetadata
    bindTarget: Penize
    evaluate: true
    value: "Math.round((x + 1) * 10) / 10"
```

```meta-bind-button
label: "+5"
hidden: true
id: "zl-plus-5"
style: primary
actions:
  - type: updateMetadata
    bindTarget: Penize
    evaluate: true
    value: "Math.round((x + 5) * 10) / 10"
```

```meta-bind-button
label: "+10"
hidden: true
id: "zl-plus-10"
style: primary
actions:
  - type: updateMetadata
    bindTarget: Penize
    evaluate: true
    value: "Math.round((x + 10) * 10) / 10"
```

**`VIEW[{Penize}][text]` zl** `BUTTON[zl-minus-10]` `BUTTON[zl-minus-5]` `BUTTON[zl-minus-1]` | `BUTTON[zl-plus-1]` `BUTTON[zl-plus-5]` `BUTTON[zl-plus-10]` | Nastavit: `INPUT[number:Penize]`

---

## Suroviny

```meta-bind-button
label: "-5"
hidden: true
id: "sur-minus-5"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: Suroviny
    evaluate: true
    value: "Math.max(0, x - 5)"
```

```meta-bind-button
label: "-1"
hidden: true
id: "sur-minus-1"
style: destructive
actions:
  - type: updateMetadata
    bindTarget: Suroviny
    evaluate: true
    value: "Math.max(0, x - 1)"
```

```meta-bind-button
label: "+1"
hidden: true
id: "sur-plus-1"
style: primary
actions:
  - type: updateMetadata
    bindTarget: Suroviny
    evaluate: true
    value: "x + 1"
```

```meta-bind-button
label: "+5"
hidden: true
id: "sur-plus-5"
style: primary
actions:
  - type: updateMetadata
    bindTarget: Suroviny
    evaluate: true
    value: "x + 5"
```

**`VIEW[{Suroviny}][text]` ks** `BUTTON[sur-minus-5]` `BUTTON[sur-minus-1]` | `BUTTON[sur-plus-1]` `BUTTON[sur-plus-5]`

---

## Herní datum

**`VIEW[{HerniDatum}][text]`** `INPUT[text:HerniDatum]`

---

## Boj

| AC | Iniciativa | Rychlost | Pas. vnímání | Pas. pátrání |
|---|---|---|---|---|
| **19** (17+2) | +0 | 5 sáhů | 17 | 21 |

### Útoky

| Zbraň | Hod | Dmg základ | Motor | Celkem |
|---|---|---|---|---|
| **Kladivo** 1r | +5 | 1k8+2 drtivé | reakce 1k4+3⚡ | **1k8+2 + 1k4+3⚡** |
| **Kladivo** 1.5r | +5 | 1k10+2 drtivé | reakce 1k4+3⚡ | **1k10+2 + 1k4+3⚡** |
| **Dýka** | +5 | 1k4+2 bodné | — | **1k4+2** |
| **Foukačka** | +5 | 1 bodné | 5/20 | **1** |

> [!warning] Reakce: Motor ve zbroji
> Tvor tě zasáhne (5 stop) → **1k4+3 ⚡** (automatická)

> [!tip] Vybití motoru
> Útok s motorem + spell slot → **+2k6⚡** (slot 1), +1k6 za vyšší slot, max 5k6

### Kouzla

| Lvl 1 | Lvl 2 | SO: 14 | Útok: +6 |
|---|---|---|---|
| **4** | **2** | | |

| Kouzlo | Slot | Gadget | Poznámka |
|---|---|---|---|
| Poplach (rituál) | 1 | Drátek + zvonek | 2x, -2 tábor |
| Katapult | 1 | Pružinový mech. | 3k8 drtivé |
| Pomalý pád | 1 | Padák v taštičce | 2x, akrobacie |
| Skok | 1 | Pružiny na boty | 2x, x3 skok |
| Sádlo | 1 | Mazlavý flakónek | Kluzký 2 sáhy |
| Gen. kouře | 1 | Prototyp | Nestabilní |

---

## Dovednosti

| TOP dovednosti | Bonus | Ostatní | Bonus |
|---|---|---|---|
| **Historie** | **+8** | Atletika | +5 |
| **Pátrání** | **+8** | Akrobacie | +3 |
| Mystika | +6 | Čachry | +3 |
| Náboženství | +6 | Nenápadnost | +3 |
| Příroda | +6 | Klamání | +1 |
| Vnímání | +7 | Přesvědčování | +1 |
| Vhled / Lékařství / Přežití | +5 | Umění / Zastrašování | +1 |

**Záchranné hody:** CON +3 | **INT +6** | **WIS +5** | **CHA +5** | STR +2 | DEX +0

---

## Stavy

> [!bug] Aktuální
> - [ ] Otrávený
> - [ ] Únava 1
> - [ ] Motor skoku: **vybitý**

---

## Rychlé reference

- **Konstrukce** 5 zl/hod · **Rychlé vytvoření** ≤1 zl jako akci (3x/den)
- **Oprava** 10 HP/hod · **Hledání materiálů** · **Odezírání ze rtů** · **Navigace lodi**

---

## Odkazy

| Co | Kam |
|---|---|
| Inventář detailně | [[Batoh]] |
| Kouzla a gadgety | [[Kouzla]] |
| Pravidla třídy | [[Pravidla]] |
| Klak | [[Klak]] |
| Zázemí, bohové | [[Lore]] |
| Deník a úkoly | [[Denik]] |
| Šablona sezení | [[Sablona sezeni]] |
