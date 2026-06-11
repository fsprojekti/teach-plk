# Izpit — Rešitve

---

## Naloga 1 — Normalne oblike logične funkcije *(25 točk)*

Izhodiščna enačba:

$$F(A, B, C, D) = \overline{A} \cdot (B \oplus C) + A \cdot (C \equiv D)$$

Razlaga operatorjev:
- $B \oplus C$ — XOR: $B\overline{C} + \overline{B}C$
- $C \equiv D$ — XNOR: $CD + \overline{C}\,\overline{D}$

---

### 1.1 Pravilnostna tabela *(10 točk)*

| # | A | B | C | D | B⊕C | C≡D | /A·(B⊕C) | A·(C≡D) | **F** |
|:-:|:-:|:-:|:-:|:-:|:---:|:---:|:--------:|:-------:|:-----:|
|  0 | 0 | 0 | 0 | 0 |  0  |  1  |    0     |    0    | **0** |
|  1 | 0 | 0 | 0 | 1 |  0  |  0  |    0     |    0    | **0** |
|  2 | 0 | 0 | 1 | 0 |  1  |  0  |    1     |    0    | **1** |
|  3 | 0 | 0 | 1 | 1 |  1  |  1  |    1     |    0    | **1** |
|  4 | 0 | 1 | 0 | 0 |  1  |  1  |    1     |    0    | **1** |
|  5 | 0 | 1 | 0 | 1 |  1  |  0  |    1     |    0    | **1** |
|  6 | 0 | 1 | 1 | 0 |  0  |  0  |    0     |    0    | **0** |
|  7 | 0 | 1 | 1 | 1 |  0  |  1  |    0     |    0    | **0** |
|  8 | 1 | 0 | 0 | 0 |  0  |  1  |    0     |    1    | **1** |
|  9 | 1 | 0 | 0 | 1 |  0  |  0  |    0     |    0    | **0** |
| 10 | 1 | 0 | 1 | 0 |  1  |  0  |    0     |    0    | **0** |
| 11 | 1 | 0 | 1 | 1 |  1  |  1  |    0     |    1    | **1** |
| 12 | 1 | 1 | 0 | 0 |  1  |  1  |    0     |    1    | **1** |
| 13 | 1 | 1 | 0 | 1 |  1  |  0  |    0     |    0    | **0** |
| 14 | 1 | 1 | 1 | 0 |  0  |  0  |    0     |    0    | **0** |
| 15 | 1 | 1 | 1 | 1 |  0  |  1  |    0     |    1    | **1** |

### 1.2 PDNO in PKNO *(5 točk)*

$$F_{PDNO} = \sum m(2, 3, 4, 5, 8, 11, 12, 15)$$

$$F_{PKNO} = \prod M(0, 1, 6, 7, 9, 10, 13, 14)$$

### 1.3 MDNO in MKNO *(10 točk)*

**Veitchov diagram za F:**

```
          CD
AB    | 00 | 01 | 11 | 10 |
------+----+----+----+----|
 00   |  0 |  0 |  1 |  1 |
 01   |  1 |  1 |  0 |  0 |
 11   |  1 |  0 |  1 |  0 |
 10   |  1 |  0 |  1 |  0 |
```

Gruče za MDNO:
- **Gruča 1** — stolpec CD=11 in CD=10 pri AB=00 (m2, m3): $\overline{A}\,\overline{B}\,C$
- **Gruča 2** — stolpec CD=00 in CD=01 pri AB=01 (m4, m5): $\overline{A}\,B\,\overline{C}$
- **Gruča 3** — stolpca CD=00 in CD=11 pri AB=11 in AB=10 (m8, m11, m12, m15): $A\,(C \equiv D)$

$$\boxed{F_{MDNO} = \overline{A}\,\overline{B}\,C + \overline{A}\,B\,\overline{C} + A\,(C \equiv D)}$$

Opomba: prva dva člena sta skupaj $\overline{A}(B \oplus C)$ — enačba je že minimalna.

**Veitchov diagram za /F (ničle):**

```
          CD
AB    | 00 | 01 | 11 | 10 |
------+----+----+----+----|
 00   |  1 |  1 |  0 |  0 |
 01   |  0 |  0 |  1 |  1 |
 11   |  0 |  1 |  0 |  1 |
 10   |  0 |  1 |  0 |  1 |
```

Gruče za $\overline{F}$ (MDNO komplementa):
- $\overline{A}\,\overline{B}\,\overline{C}$ — pokrije m0, m1
- $\overline{A}\,B\,C$ — pokrije m6, m7
- $A\,(C \oplus D)$ — pokrije m9, m10, m13, m14

Z De Morganovim izrekom:

$$\boxed{F_{MKNO} = (A + B + C)\cdot(A + \overline{B} + \overline{C})\cdot(\overline{A} + (C \equiv D))}$$

---

## Naloga 2 — Realizacija sekvenčnega vezja iz enačb *(25 točk)*

Podani enačbi:

$$M1[k{+}1] = (A + M1[k]) \cdot \overline{B} \cdot \overline{M2[k]}$$
$$M2[k{+}1] = (B + M2[k]) \cdot M1[k]$$

### 2.1 Pravilnostna tabela *(10 točk)*

| # | A | B | M1[k] | M2[k] | M1[k+1] | M2[k+1] |
|:-:|:-:|:-:|:-----:|:-----:|:-------:|:-------:|
|  0 | 0 | 0 |   0   |   0   |    0    |    0    |
|  1 | 0 | 0 |   0   |   1   |    0    |    0    |
|  2 | 0 | 0 |   1   |   0   |    1    |    1    |
|  3 | 0 | 0 |   1   |   1   |    0    |    1    |
|  4 | 0 | 1 |   0   |   0   |    0    |    0    |
|  5 | 0 | 1 |   0   |   1   |    0    |    0    |
|  6 | 0 | 1 |   1   |   0   |    0    |    1    |
|  7 | 0 | 1 |   1   |   1   |    0    |    1    |
|  8 | 1 | 0 |   0   |   0   |    1    |    0    |
|  9 | 1 | 0 |   0   |   1   |    0    |    0    |
| 10 | 1 | 0 |   1   |   0   |    1    |    1    |
| 11 | 1 | 0 |   1   |   1   |    0    |    1    |
| 12 | 1 | 1 |   0   |   0   |    0    |    0    |
| 13 | 1 | 1 |   0   |   1   |    0    |    0    |
| 14 | 1 | 1 |   1   |   0   |    0    |    1    |
| 15 | 1 | 1 |   1   |   1   |    0    |    1    |

**Primer izračuna (#10):** A=1, B=0, M1=1, M2=0:  
$M1' = (1+1)\cdot\overline{0}\cdot\overline{0} = 1\cdot1\cdot1 = 1$;  
$M2' = (0+1)\cdot1 = 1$

**Opomba:** Ko B=1, je vedno $M1'=0$ (vrstice 4–7, 12–15). Ko M1=0, je vedno $M2'=0$.

**Ocenjevanje:** 0,5 točke za vsako pravilno vrstico (16 × 0,5 = 8 točk) + 2 točki opomba.

### 2.2 Lestvični diagram na osnovi enačb *(15 točk)*

Neposredna realizacija iz podanih enačb:

```
 Rung 1: M1[k+1] = (A + M1)·/B·/M2
                                              (M1)
||----+----[ A  ]----+----[/B ]----[/M2]---( )----||
      |              |
      +----[ M1 ]----+


 Rung 2: M2[k+1] = (B + M2)·M1
                                              (M2)
||----+----[ B  ]----+----[ M1]------------( )----||
      |              |
      +----[ M2 ]----+
```

**Razlaga vezja:**
- **M1**: samozadrževalni krog (A ali M1) z dvojno blokado — aktiven le, ko B=0 IN M2=0
- **M2**: aktivira se prek B (ali samo-drži), a le ko je M1=1 — M2 ne more biti aktiven brez M1
- **Medsebojna odvisnost**: M2 je odvisna od M1, M1 pa je blokirana z M2 — ko obe postaneta 1, M1 v naslednjem ciklu pade

**Ocenjevanje:** 5 točk Rung 1 (samozadrž. + /B + /M2), 7 točk Rung 2 (samozadrž. + M1), 3 točke razlaga.

---

## Naloga 3 — Realizacija krmilnega programa v FBD *(25 točk)*

### Zahteve

| Zahteva                                   | Implementacija                        |
|-------------------------------------------|---------------------------------------|
| Q1 se aktivira ob I1                      | RS bistabil, S = I1                   |
| Q1 ostane aktiven do 4× aktivacije I2     | CTU števec (PV=4), CU = I2            |
| Po deaktivaciji Q1 čakaj 8 sekund         | TON časovnik (PT=t#8s), IN = /Q1      |
| Med čakanjem I1 ignoriran                 | TON.Q pogoj za ponastavitev CTU in omogočanje RS.S |

---

### FBD krmilni program

```
 I1 ────────────────────────────────────────────── AND ──── S
                                                 ┌──┤      ┌──────┐
 TON.Q ──────────────────────────────────────────┘        │  RS  ├──── Q1
                                                           │      │
                                              ┌──────────► │  R   │
                                              │            └──────┘
 I2 ──────────────────── CTU ─── CTU.Q ──────┤
                       ┌───────┐             │
   /Q1 ──────────────► │  R    │             │
                       │  PV=4 │             │
                       └───────┘             │
                                             │
 /Q1 ──────────────── TON ─── TON.Q ────────┘
                    ┌────────┐    (→ RS.R in CTU.R pogoj)
                    │ PT=t#8s│
                    └────────┘
```

**Bloki in povezave:**

| Blok    | Vhodi                                  | Izhodi        |
|---------|----------------------------------------|---------------|
| **AND** | IN1 = I1, IN2 = TON.Q                  | → RS.S        |
| **RS**  | S = AND_out, R = CTU.Q                 | Q1            |
| **CTU** | CU = I2 (naraščajoča fronta), R = /Q1, PV = 4 | CTU.Q  |
| **TON** | IN = /Q1, PT = t#8s                    | TON.Q         |

---

### Logika delovanja

```
Korak 1:  Ko TON.Q = 1 (sistem pripravljen):
          I1 ↑  →  AND = 1  →  RS.S = 1  →  Q1 = 1

Korak 2:  Q1 = 1  →  /Q1 = 0  →  TON.IN = 0  →  TON.Q = 0
          (I1 je zdaj blokiran, ker AND zahteva TON.Q = 1)

Korak 3:  Vsak I2 ↑  →  CTU.CU++  (šteje do 4)

Korak 4:  Po 4× I2  →  CTU.Q = 1  →  RS.R = 1  →  Q1 = 0

Korak 5:  Q1 = 0  →  /Q1 = 1  →  CTU.R = 1  →  CTU = 0 (ponastavitev)
          /Q1 = 1  →  TON.IN = 1  →  timer začne teči (8s)

Korak 6:  Po 8s  →  TON.Q = 1  →  sistem spet sprejema I1
```

**Opomba:** TON.Q kot pogoj AND zagotavlja, da se Q1 ne more znova aktivirati med 8-sekundnim čakanjem.

---

## Naloga 4 — SFC za vodenje mešalnega rezervoarja *(25 točk)*

### Definicija signalov

| Signal | Tip   | Pomen (0 / 1)                                    |
|--------|-------|--------------------------------------------------|
| V1     | Izhod | Polnilni ventil (zaprt / odprt)                  |
| V2     | Izhod | Izpustni ventil (zaprt / odprt)                  |
| M      | Izhod | Mešalo (izklopljeno / vklopljeno)                |
| LH     | Vhod  | Senzor visokega nivoja (pod / nad visokim nivojem) |
| LL     | Vhod  | Senzor nizkega nivoja (nad / pod nizkim nivojem)  |

### Zaporedje delovanja

1. Polni z **V1** → dokler **LH = 1** (visoki nivo dosežen)
2. Meša z **M** → **20 sekund**
3. Prazni z **V2** → dokler **LL = 1** (nizki nivo dosežen)
4. Čakaj **5 sekund** → ponovi od koraka 1

---

### SFC diagram

```
       ╔══════════════╗
  ══► ║    Init      ║  V1=0, V2=0, M=0
       ╚══════╤═══════╝
              │ TRUE
       ╔══════╧═══════╗
  S1: ║  Polnjenje    ║  V1=1
       ╚══════╤═══════╝
              │ LH = 1
       ╔══════╧═══════╗
  S2: ║   Mešanje     ║  M=1, TON1.IN=1
       ╚══════╤═══════╝
              │ TON1.Q = 1  (po 20s)
       ╔══════╧═══════╗
  S3: ║  Praznjenje   ║  V2=1
       ╚══════╤═══════╝
              │ LL = 1
       ╔══════╧═══════╗
  S4: ║   Čakanje     ║  TON2.IN=1
       ╚══════╤═══════╝
              │ TON2.Q = 1  (po 5s)
              │
      ════════╝  (povratek na S1 — neskončna zanka)
```

---

### Tabela korakov, akcij in prehodov

| Korak           | Aktivne akcije              | Pogoj prehoda naprej      |
|-----------------|-----------------------------|---------------------------|
| **Init**        | V1=0, V2=0, M=0             | TRUE                      |
| **S1** Polnjenje  | V1=1                      | LH = 1                    |
| **S2** Mešanje    | M=1, TON1.IN=1            | TON1.Q = 1 (po t#20s)    |
| **S3** Praznjenje | V2=1                      | LL = 1                    |
| **S4** Čakanje    | TON2.IN=1                 | TON2.Q = 1 (po t#5s) → nazaj na S1 |

**Ocenjevanje:** 3 točke za vsak korak z akcijami in prehodom (4 × 3 = 12 točk) + 5 točk za pravilno neskončno zanko + 5 točk za tabelo + 3 točke za definicijo signalov.
