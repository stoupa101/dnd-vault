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
hp: 44
max_hp: 44
ac_stit: 19
ac_bez_stitu: 17
Stit: true
Iniciativa: 0
Rychlost: 5
pasperc: 15
paspat: 16
Penize: 182
Suroviny: 50
HerniDatum: 4.6.1358
Status: Active
---

# Klik - Dashboard

> [!info] Skalní gnóm · Tinkerer (Parní rytíř) · Lvl 5 · NN · Nebelun (Gond)
> Jazyky: Obecná, Gnómština · Odezírání ze rtů

---

## Vlastnosti

| Vlastnost | Hodnota | Modifikátor | Poznámka |
|---|---|---|---|
| **SÍLA** | 15 | **+2** | Základ 15 |
| **OBRATNOST** | 10 | **+0** | Základ 10 |
| **ODOLNOST** | 16 | **+3** | Základ 15 +1 (skalní gnóm) |
| **INTELIGENCE** | 16 | **+3** | Základ 15 +1 (skalní gnóm) |
| **MOUDROST** | 14 | **+2** | Základ 14 |
| **CHARISMA** | 7 | **-2** | Základ 7 |

> [!note] Jak se počítají modifikátory
> `(Vlastnost - 10) / 2` zaokrouhleno dolů. Např. INT 16 → (16-10)/2 = **+3**

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

> [!note] Max HP = 44
> Lvl 1: 8 + CON(+3) = 11 · Lvl 2-5: 4×(5+3) = 32 · Celkem: **43** (mám 44)

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

### Štít

**Používám štít:** `INPUT[toggle:Stit]`

> [!note] Štít mění
> - **AC:** 19 (se štítem) / 17 (bez štítu)
> - **Kladivo:** 1k8+2 (jednoruční) / 1k10+2 (obouruční)
> - **Nevýhoda** na Nenápadnost platí vždy (lamelová zbroj)

### Obrana

| AC | Iniciativa | Rychlost | Pas. vnímání | Pas. pátrání |
|---|---|---|---|---|
| **`VIEW[{ac_stit}][text]`** se štítem / **`VIEW[{ac_bez_stitu}][text]`** bez | +0 | 5 sáhů | 15 | 16 |

> [!note] Jak se počítá AC
> - **Se štítem:** Lamelová zbroj 17 + Štít +2 = **19**
> - **Bez štítu:** Lamelová zbroj 17 = **17**
> - Iniciativa: DEX mod **+0**
> - Rychlost: Skalní gnóm 6 sáhů - Střední zbroj -1 = **5 sáhů**

> [!note] Pasivní vnímání (pasperc)
> `10 + WIS mod (+2) + Zdatnost (+3) = **15**`
> *Odezírání ze rtů: výhoda na Pátrání když vidíš rty*

> [!note] Pasivní pátrání (paspat)
> `10 + INT mod (+3) + Zdatnost (+3) = **16**`

### Útoky

#### Se štítem (jednoruční)

| Zbraň | Útok | Dmg | Motor (reakce) | Celkem |
|---|---|---|---|---|
| **Kladivo** | +5 | 1k8+2 drtivé | 1k4+3 ⚡ | **1k8+2 + 1k4+3⚡** |
| **Dýka** | +5 | 1k4+2 bodné | — | **1k4+2** |
| **Foukačka** | +5 | 1 bodné | — | **1** |

#### Bez štítu (obouruční)

| Zbraň | Útok | Dmg | Motor (reakce) | Celkem |
|---|---|---|---|---|
| **Kladivo** | +5 | 1k10+2 drtivé | 1k4+3  | **1k10+2 + 1k4+3⚡** |
| **Dýka** | +5 | 1k4+2 bodné | — | **1k4+2** |
| **Foukačka** | +5 | 1 bodné | — | **1** |

> [!note] Jak se počítá útok
> `Zdatnost (+3) + STR mod (+2) = **+5**`

> [!note] Jak se počítá damage
> `Základ zbraně + STR mod (+2)`

> [!note] Motor reakce
> `1k4 + INT mod (+3) = **1k4+3**` (automatická, když tě tvor zasáhne do 5 stop)

> [!warning] Reakce: Motor ve zbroji
> Tvor tě zasáhne (5 stop) → **1k4+3 ⚡** (automatická, nepotřebuje akci)

> [!tip] Vybití motoru
> Útok s motorem + spell slot → **+2k6⚡** (slot 1), +1k6 za vyšší slot, max 5k6

### Kouzla

| Lvl 1 | Lvl 2 | SO: 14 | Útok: +6 |
|---|---|---|---|
| **4** | **2** | | |

> [!note] Jak se počítá SO záchrany
> `8 + Zdatnost (+3) + INT mod (+3) = **14**`

> [!note] Jak se počítá útok kouzlem
> `Zdatnost (+3) + INT mod (+3) = **+6**`

> [!note] Připravená kouzla
> `INT mod (+3) + lvl/2 (2) = **5** kouzel`

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

| Dovednost | Bonus | Výpočet |
|---|---|---|
| **Historie** | **+6** | INT +3 + Zdatnost +3 |
| **Pátrání** | **+6** | INT +3 + Zdatnost +3 |
| Mystika | +3 | INT +3 |
| Náboženství | +3 | INT +3 |
| Příroda | +3 | INT +3 |
| Vnímání | +5 | WIS +2 + Zdatnost +3 |
| Vhled | +2 | WIS +2 |
| Lékařství | +2 | WIS +2 |
| Přežití | +2 | WIS +2 |
| Atletika | +5 | STR +2 + Zdatnost +3 |
| Akrobacie | +3 | DEX +0 + Zdatnost +3 |
| Čachry | +3 | DEX +0 + Zdatnost +3 |
| Nenápadnost | +3 | DEX +0 + Zdatnost +3 |
| Klamání | -2 | CHA -2 |
| Přesvědčování | -2 | CHA -2 |
| Umění | -2 | CHA -2 |
| Zastrašování | -2 | CHA -2 |

> [!note] Odbornost (Expertise)
> Na lvl 2: 2 dovednosti s pomůckou → bonus ×2. Mám: **Kutilské +6** (INT +3 + 2×Zdatnost), **Navigační +6**

**Záchranné hody:** STR +2 | DEX +0 | **CON +6** | **INT +6** | WIS +2 | CHA -2

> [!note] Záchranné hody
> `Zdatnost (+3) + Modifikátor vlastnosti`
> - Tinkerer: CON + INT (proficientní)
> - **Gnómská prohnanost:** +3 k INT/WIS/CHA záchranám proti magii

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
