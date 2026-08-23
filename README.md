# 🏔️ Zahlenberg — Größer · kleiner · gleich bis 100

Ein interaktives Bergwelt-Mathespiel für die Grundschule: Ein Bergsteiger klettert
einen Berg hinauf, indem Zahlen im Zahlenraum bis 100 sortiert oder verglichen
werden. Das Spiel ist bewusst so gestaltet, dass es auch Kinder bedienen können,
die noch nicht sicher lesen können — es kommt fast ohne Text aus und arbeitet mit
eindeutigen visuellen Symbolen.

**Zielgruppe:** Grundschule, vor allem Klasse 2
**Status:** Version 1.0 — veröffentlichungsbereit

## 🎮 Spielprinzip

Zwei Aufgabentypen wechseln sich zufällig ab (je ca. 50 %):

- **Zahlen sortieren:** Vier Zahlenkarten müssen per Drag & Drop auf vier
  Bergstationen gezogen werden — von klein nach groß oder umgekehrt. Welche
  Richtung gilt, zeigt ein Symbol (kleiner Berg → großer Berg oder umgekehrt),
  kein Lesen nötig.
- **Vergleichen:** Zwei gleich große Berggipfel mit je einer Zahl — das Kind wählt
  das passende Zeichen: `<`, `=` oder `>`. Rund 20 % der Aufgaben sind
  Gleich-Aufgaben, damit auch das Gleichheitszeichen geübt wird.

Nach jeder richtig gelösten Aufgabe steigt der Bergsteiger eine Station höher.
**Nach 10 richtig gelösten Aufgaben** erreicht er den Gipfel — Konfetti und ein
Gipfel-Symbol feiern den Erfolg.

Bei falschen Antworten gibt es keine Fehlermeldung und keinen Punktabzug — die
betroffenen Karten bzw. das Zeichen wackeln kurz, und das Kind kann es sofort
erneut versuchen.

## 🛠️ Technik

Eine einzige, in sich geschlossene `index.html`-Datei — kein Build-Prozess, keine
Abhängigkeiten, kein Server nötig.

- Reines HTML, CSS und JavaScript (kein Framework)
- Alle Grafiken (Berge, Bergsteiger, Wolken) sind reines CSS/SVG — keine
  Bilddateien
- Ton wird zur Laufzeit synthetisch erzeugt (Web Audio API) — keine Audiodateien
- **Drag & Drop funktioniert einheitlich für Maus UND Touch** über die
  standardisierte Pointer-Events-API (kein klassisches HTML5-Drag, das auf
  Touchgeräten unzuverlässig ist). Kartenpositionierung beim Rundenstart erfolgt
  synchron über echte Render-Zyklen (`requestAnimationFrame`), nicht über
  geschätzte Wartezeiten — das macht auch sehr schnell aufeinanderfolgende
  Interaktionen zuverlässig.
- Zahlengenerierung: 0–100, bewusst inklusive „unrunder" zweistelliger Zahlen
  (z. B. 34, 43, 67, 76), damit echtes Stellenwertverständnis gefragt ist, nicht
  nur Zehnerzahlen-Erkennung
- Läuft vollständig offline, keine externen Ressourcen
- Responsiv für Desktop, Laptop, Tablet, Smartphone und Smartboard, in Hoch- und
  Querformat

## 📁 Projektstruktur

```
zahlenberg-projekt/
├── index.html      ← das komplette Spiel (HTML + CSS + JavaScript)
├── README.md        ← diese Datei
└── .gitignore
```

## ▶️ Lokal ausprobieren

Einfach `index.html` im Browser öffnen — kein Server, keine Installation nötig.

## 🌐 Veröffentlichung

### GitHub

1. Neues Repository auf [github.com](https://github.com) anlegen.
2. `index.html`, `README.md` und `.gitignore` hochladen.

### Netlify / Vercel

Das Projekt ist eine reine statische HTML/CSS/JS-Seite ohne Build-Schritt — beide
Plattformen erkennen das automatisch, es ist keine Konfiguration nötig.

**Netlify (per Drag & Drop, ganz ohne GitHub):**
1. Auf [app.netlify.com](https://app.netlify.com) einloggen.
2. Den Ordner mit der `index.html` direkt in den Browser ziehen („Deploy manually").
3. Netlify vergibt sofort einen Link.

**Vercel (über GitHub):**
1. Mit GitHub bei [vercel.com](https://vercel.com) einloggen.
2. „Add New…" → „Project" → Repository importieren → „Deploy".

## ✅ Qualitätssicherung

Vor der Freigabe automatisiert geprüft:
- Sortieren von klein→groß und groß→klein
- Vergleich mit `<`, `>` und `=`, inklusive gezielter Stellenwert-Fallen
  (34/43, 67/76, 89/98, 9/90, 100/10)
- Zufällige Aufgabenverteilung, keine doppelten Zahlen bei Sortieraufgaben
- Drag & Drop mit echter Maus-Simulation UND echten nativen Touch-Events
  (Chrome DevTools Protocol), jeweils über mehrere Dutzend Runden fehlerfrei
- Alle Bildschirmgrößen inkl. Hoch-/Querformat: Smartboard, Laptop, iPad,
  iPhone, Android-Tablet, Android-Handy, iPhone SE
- Fortschritt exakt 0→10, Spielende exakt nach 10 Aufgaben
- Neustart, Rückkehr zur Startseite, Sound an/aus
- Mehrere vollständige Runden hintereinander ohne Fehler, keine
  Speicher-/DOM-Lecks

## 📄 Lizenz

© Förderfreude Games. Alle Rechte vorbehalten.
