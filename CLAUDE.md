# CLAUDE.md — Bestellmaske beyonity × Instone Real Estate

> Diese Datei wird von Claude Code automatisch als Projektkontext geladen.
> Sie beschreibt Ziel, Architektur, Designsystem, offene Aufgaben und Konventionen.

## Ziel
Bestell-Oberfläche (Landingpage) für den Kunden **Instone Real Estate**, betrieben
von **beyonity**. Mitarbeiter sollen vordefinierte Leistungspakete einsehen,
konfigurieren und eine Bestellung absenden können.

## Aktueller Stand
Funktionierender Prototyp als **einzelne, eigenständige HTML-Datei**
(`bestellmaske.html`) — Vanilla HTML/CSS/JS, **kein Build-Schritt**, einfach im
Browser öffnen. Alle Features unten sind implementiert.

## Dateien
- `bestellmaske.html` — komplette App (HTML + CSS + JS in einer Datei)
- `HANDOVER.md` — menschlich lesbares Übergabedokument
- `CLAUDE.md` — diese Datei

## Lokal starten
Keine Toolchain nötig: `bestellmaske.html` im Browser öffnen
(oder `python3 -m http.server` und im Browser aufrufen, falls window.storage getestet wird).

## Implementierte Features
1. **Stepansicht** — 3 Schritte (Projektdaten → Pakete → Bestellung) + gelbe Status-Leiste, färbt sich live mit.
2. **Produktkarten** — Thumbnail-Icon, „Mehr lesen"-Aufklappen für lange Texte, Preis **netto/ohne MwSt** pro Einheit, „Beispiel ansehen"-Modal, Mengenauswahl, **Fly-to-Cart-Animation**.
3. **Startwizard** (Overlay, sichtbare Steps): Name + E-Mail → Projektdaten → Anzahl Gebäude → Anzahl Einheiten → Dropdown Nutzungsart (Zur Miete / Zum Verkauf / Miete und Verkauf / Gewerblich / Mixed Use).
4. **Unsere Bestellungen** — Verlauf, anklickbar → Detail-Modal. Persistenz via `window.storage` mit In-Memory-Fallback + Seed-Daten.
5. **Warenkorb** — Drawer mit Positionen, Mengen, Summen **inkl. MwSt (19 %)**.
6. **Checkout** — Button „Bestellung senden" → öffnet vorbefüllte `mailto:` (an Besteller + cc an uns), Hinweis „schriftliche Auftragsbestätigung", erfasst Bestellung im Verlauf.
7. **Chatbot** (unten rechts) — Frage eintippen → Antwort „Vielen Dank für Ihre Frage! Fabian Hammer wird sich bei Ihnen melden."
8. **FAQ** — 4 Fragen (Was passiert als Nächstes / Bearbeitungsdauer / Link zum Produkt / Ansprechpartner).

## Designsystem (Beyonity-Brand)
- Font: **Sora** (Google Fonts).
- Farben (CSS-Variablen in `:root`):
  - `--bey-blue #3c57e1`, `--bey-blue-deep #2840c2`, `--bey-yellow #f8ff76`, `--bey-navy #001a64`
  - `--bey-light #d8ddf9`, `--bey-light-50 #ecf0fc`
  - Instone-Akzente: `--ins-navy #1b3aa0`, `--ins-pink #ff5d87`, `--ins-green #8ccf52`
  - Text: `--text #001a64`, `--text-body #3b4774`, `--text-muted #7a85a8`, `--line #e6eaf7`
- UI-Muster: sticky Top-Bar mit Logos + „×"-Trenner, gelbe Status-Leiste, Pill-Buttons,
  abgerundete Cards, weiche navy-getönte Schatten.
- Logos: beyonity = Inline-SVG (Original). Instone = **nachgebautes** Inline-SVG
  (navy „Instone" + „Real Estate" + 3 Kacheln Pink/Grün/Navy), da Originaldatei fehlte.

## Konfiguration (Platzhalter — anpassen)
Im `<script>` ganz oben, Objekt `CONFIG`:
- `vatRate: 0.19`
- `ourEmail: "bestellung@beyonity.com"`  ← **echte Empfänger-Adresse einsetzen**
- `contact: "Fabian Hammer"`

Leistungspakete stehen im Array `PACKAGES` (Titel, Farbe, Icon-SVG, `price`, `short`, `long`).
**Aktuell Platzhalter:** Grundriss-Paket, Foto & Visualisierung, 360°-Rundgang, Exposé & Texte, Premium Full-Service.

## Offene Aufgaben (TODO)
1. Echte Leistungspakete + Preise in `PACKAGES` einsetzen (liegen noch nicht vor).
2. `CONFIG.ourEmail` durch echte Empfänger-Adresse ersetzen.
3. Echter Mail-Versand (an uns + Besteller) braucht ein kleines Backend / Mail-Service —
   aktuell nur `mailto:`-Vorschau über das E-Mail-Programm des Nutzers.
4. Original-Instone-Logo (Datei) einbinden, falls gewünscht (aktuell SVG-Rekonstruktion).
5. Optional: Mengenlogik an Projektdaten koppeln (z. B. Preis × Anzahl Einheiten automatisch).

## Konventionen / Constraints
- **Einzeldatei, Vanilla JS, kein Framework, kein Build.** Wenn das aufgebrochen werden soll
  (z. B. nach React/Vite), vorher mit dem Nutzer abstimmen.
- **Kein `localStorage`/`sessionStorage`** in der Artifact-Umgebung — Persistenz läuft über
  `window.storage` (async, try/catch, Fallback auf In-Memory). Bei einem echten Repo/Deploy
  kann das durch echtes Backend/IndexedDB ersetzt werden.
- Sprache der UI: **Deutsch**.
- Beträge: `Intl.NumberFormat('de-DE', { style:'currency', currency:'EUR' })`.
