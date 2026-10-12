<div align="center">

# ONEPERCENT

**Das risikobasierte Markt-Terminal in einer einzigen `index.html`**

**Sprache:** [English](README.md) | **Deutsch** | [中文](README.zh.md) | [Dansk](README.da.md)

[Live-Demo](https://kbgirishhb.github.io/Onepercentage/) | [Benutzerhandbuch](docs/USER_GUIDE.md) | [Bereitstellung](docs/DEPLOYMENT.md) | [Architektur](docs/ARCHITECTURE.md)

</div>

---

## Warum es ONEPERCENT gibt

Jede Trading-App zeigt Kurse. Kaum eine zwingt dazu, **Positionsgröße, Stopp und Ausstieg** zu planen, bevor die Aufregung beginnt. ONEPERCENT ist vom Risiko her gedacht: Die **1-%-Regel** ist das Rückgrat.

> **Was kaufe ich genau, wie viel, wo liege ich falsch, und wann steige ich mit Gewinn aus?**

## Funktionen

- **Live-Marktdaten:** Aktien, ETFs, Indizes, indische Werte (`.NS`) und Krypto, ohne API-Schlüssel, mit mehrstufiger Fallback-Kette
- **Eigener Kerzenchart:** 7 Zeiträume, Zoom, Verschieben, Fadenkreuz, Volumen
- **Indikatoren:** EMA20/50, VWAP, Bollinger-Bänder, Volumen, RSI und ATR mit verständlichen Erklärungen
- **1-%-Risikomotor:** Tagesrisiko-Anzeige mit hartem Limit, Positionsrechner, Allokationsgrenze, Break-even inkl. Gebühren
- **Erfassen und Analysieren:** Ein Klick wechselt zum 1-Minuten-Chart, berechnet einen Plan und bewertet das R:R
- **Screenshot-Analyse:** Broker-Screenshot einfügen, drei Linien ziehen, Urteil: TAKE, MARGINAL oder REJECT (unter 2R wird abgelehnt)
- **Ausstiegsplaner:** Sniper, Scale-out, Time-stop, ATR-Trail
- **Handelsjournal:** R-basiert, nur lokal auf Ihrem Gerät gespeichert
- **MEIN PLAN:** IST- und ET-Uhren, Handelsfenster, persönlicher Plan per 4-Fragen-Assistent
- **USD / INR:** Umschaltung des gesamten Terminals zum aktuellen Wechselkurs
- **Ehrliche Daten-Badges:** `LIVE`, `GH - DELAYED`, `CACHED`, `SIMULATED`

## Die 1-%-Rechnung

```text
Konto 8.000 -> Tagesrisiko 80 (1 %)
Stopp-Abstand 0,20 -> Menge = 80 / 0,20 = 400 Stück
Bei Stopp verlieren Sie genau 1 %
```

## Bereitstellung (kostenlos)

1. Öffentliches Repository erstellen und `index.html` hochladen
2. Settings > Pages > Deploy from a branch > `main` / (root)
3. Fertig: https://kbgirishhb.github.io/Onepercentage/

Für echte Marktdaten siehe [DEPLOYMENT.md](docs/DEPLOYMENT.md) (GitHub Action, Cloudflare Worker, Finnhub; Dokumentation auf Englisch).

## Haftungsausschluss

ONEPERCENT ist ein **Bildungswerkzeug** und keine Anlageberatung. Daten können verzögert oder simuliert sein. Prüfen Sie Kurse immer bei Ihrem Broker. Handel birgt erhebliche Verlustrisiken.

## Lizenz

[MIT](LICENSE.txt)
