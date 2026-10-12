<div align="center">

# ONEPERCENT

**Det risikobaserede markedsterminal i én enkelt `index.html`**

**Sprog:** [English](README.md) | [Deutsch](README.de.md) | [中文](README.zh.md) | **Dansk**

[Live demo](https://kbgirishhb.github.io/Onepercentage/) | [Brugervejledning](docs/USER_GUIDE.md) | [Udrulning](docs/DEPLOYMENT.md) | [Arkitektur](docs/ARCHITECTURE.md)

</div>

---

## Hvorfor ONEPERCENT findes

De fleste handelsapps viser kurser. Næsten ingen tvinger dig til at fastsætte **positionsstørrelse, stop og exit**, før spændingen tager over. ONEPERCENT tager udgangspunkt i risiko: **1 %-reglen** er rygraden.

> **Hvad køber jeg præcist, hvor meget, hvor tager jeg fejl, og hvornår går jeg ud med gevinsten?**

## Funktioner

- **Live markedsdata:** Aktier, ETF'er, indekser, indiske aktier (`.NS`) og krypto uden API-nøgler, med flere fallback-niveauer
- **Egenudviklet lysestagediagram:** 7 tidsrammer, zoom, panorering, krydshår, volumen
- **Indikatorer:** EMA20/50, VWAP, Bollinger-bånd, volumen samt RSI og ATR med letforståelige forklaringer
- **1 %-risikomotor:** Daglig risikomåler med hård grænse, positionsberegner, allokeringsloft, break-even inkl. gebyrer
- **Indfang og analysér:** Ét klik skifter til 1-minutters diagrammet, beregner en plan og vurderer R:R
- **Skærmbilledanalyse:** Indsæt et skærmbillede fra din mægler, træk tre linjer og få dommen TAKE, MARGINAL eller REJECT (under 2R afvises)
- **Exit-planlægger:** Sniper, Scale-out, Time-stop, ATR-trail
- **Handelsjournal:** R-baseret, gemmes kun på din enhed
- **MIN PLAN:** IST- og ET-ure, handelsvinduer, personlig plan via 4 spørgsmål
- **USD / INR:** Skift hele terminalen med live valutakurs
- **Ærlige data-badges:** `LIVE`, `GH - DELAYED`, `CACHED`, `SIMULATED`

## 1 %-regnestykket

```text
Konto 8.000 -> daglig risiko 80 (1 %)
Stop-afstand 0,20 -> antal = 80 / 0,20 = 400 stk.
Ved stop taber du præcis 1 %
```

## Udrulning (gratis)

1. Opret et offentligt repository og upload `index.html`
2. Settings > Pages > Deploy from a branch > `main` / (root)
3. Færdig: https://kbgirishhb.github.io/Onepercentage/

For rigtige markedsdata se [DEPLOYMENT.md](docs/DEPLOYMENT.md) (GitHub Action, Cloudflare Worker, Finnhub; dokumentationen er på engelsk).

## Ansvarsfraskrivelse

ONEPERCENT er et **uddannelsesværktøj** og ikke investeringsrådgivning. Data kan være forsinkede eller simulerede. Kontrollér altid kurser hos din mægler. Handel indebærer betydelig risiko for tab.

## Licens

[MIT](LICENSE.txt)
