# Izpit — Programirljivi logični krmilniki

---

## Naloga 1 — Normalne oblike logične funkcije (25 točk)

Dana je logična funkcija štirih spremenljivk:

$$F(A, B, C, D) = \overline{A} \cdot (B \oplus C) + A \cdot (C \equiv D)$$

1. Zapišite pravilnostno tabelo za $F(A,B,C,D)$ *(10 točk)*

2. Zapišite $F_{PDNO}$ in $F_{PKNO}$ *(5 točk)*

3. Zapišite $F_{MDNO}$ in $F_{MKNO}$ *(10 točk)*

---

## Naloga 2 — Realizacija sekvenčnega vezja iz enačb (25 točk)

Podani sta enačbi sekvenčnega vezja z dvema vhodoma ($A$, $B$) in dvema izhodoma ($M1$, $M2$):

$$M1[k{+}1] = (A + M1[k]) \cdot \overline{B} \cdot \overline{M2[k]}$$
$$M2[k{+}1] = (B + M2[k]) \cdot M1[k]$$

1. Sestavite pravilnostno tabelo *(10 točk)*

2. Realizirajte vezje z lestvičnim diagramom na podlagi podanih enačb *(15 točk)*

---

## Naloga 3 — Realizacija krmilnega programa v FBD (25 točk)

Izhod **Q1** se aktivira ob aktivaciji vhoda **I1**. Izhod Q1 nato ostane aktiven, dokler se vhod **I2** ne aktivira **4-krat**. Po deaktivaciji Q1 sistem počaka **8 sekund** pred možnostjo ponovne aktivacije (v tem času se nova aktivacija I1 ignorira).

Zapišite krmilni program v jeziku **FBD** (Function Block Diagram).

---

## Naloga 4 — SFC za vodenje mešalnega rezervoarja (25 točk)

Narišite SFC za vodenje sistema, ki mora delovati na naslednji način:

Mešalni rezervoar se polni prek ventila **V1** do visokega nivoja, ki ga zazna senzor **LH**. Po dosegu visokega nivoja se ventil V1 zapre in vklopi se mešalo **M** za **20 sekund**. Po končanem mešanju se odpre izpustni ventil **V2** in rezervoar se prazni do nizkega nivoja, ki ga zazna senzor **LL**. Ko je rezervoar prazen, se V2 zapre in sistem po **5 sekundah** ponovi cikel od začetka.

> Ventila V1, V2 (0/1 … zaprt/odprt),  
> mešalo M (0/1 … izklopljeno/vklopljeno),  
> senzor LH (0/1 … pod visokim nivojem / nad visokim nivojem),  
> senzor LL (0/1 … nad nizkim nivojem / pod nizkim nivojem)

<img src="naloga4.png" alt="Shema rezervoarja z ventili V1, V2, V3 in merilnikoma X0, X1" width="40%">
