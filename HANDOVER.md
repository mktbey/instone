# Handover — Bestellmaske beyonity × Instone Real Estate

## Was das ist
Bestell-Oberfläche (Landingpage) für den Kunden **Instone Real Estate**, betrieben von
**beyonity**. Mitarbeiter sehen vordefinierte Leistungspakete, konfigurieren sie und senden
eine Bestellung ab. Umgesetzt als **einzelne, eigenständige HTML-Datei** (Vanilla JS, kein Build).

## Dateien in diesem Paket
| Datei | Zweck |
|------|------|
| `bestellmaske.html` | Die komplette App (im Browser öffnen) |
| `CLAUDE.md` | Projektkontext, wird von Claude Code automatisch geladen |
| `HANDOVER.md` | Dieses Dokument |

## Design
Look & Feel = **Beyonity-Brand** (aus Referenz-`index.html`): Font „Sora"; Blau `#3c57e1`,
Tiefblau `#2840c2`, Gelb `#f8ff76`, Navy `#001a64`; sticky Top-Bar mit beiden Logos + „×",
gelbe Status-Leiste, Pill-Buttons, abgerundete Cards, weiche Schatten.
Instone-Logo ist als **Inline-SVG nachgebaut** (Originaldatei lag nicht vor) — kann ersetzt werden.

## Fertige Features
- 3-stufige Stepansicht + gelbe Status-Leiste
- Produktkarten: Thumbnail, „Mehr lesen", Preis ohne MwSt, „Beispiel ansehen", Mengen, Fly-to-Cart-Animation
- Startwizard (Overlay): Name+E-Mail → Projektdaten → Gebäude → Einheiten → Nutzungsart-Dropdown
- „Unsere Bestellungen": Verlauf + Detail-Ansicht, persistent (window.storage + Fallback)
- Warenkorb-Drawer mit Summen inkl. MwSt (19 %)
- Checkout „Bestellung senden" → vorbefüllte Mail (Besteller + cc an uns) + Bestätigungshinweis
- Chatbot → „Vielen Dank für Ihre Frage! Fabian Hammer wird sich bei Ihnen melden."
- FAQ (4 Fragen)

## Vor dem Live-Gang anpassen
1. **Echte Pakete & Preise** im Array `PACKAGES` (aktuell Platzhalter).
2. **Empfänger-Mail** in `CONFIG.ourEmail` (Platzhalter `bestellung@beyonity.com`).
3. **Echter Mail-Versand** braucht ein kleines Backend / Mail-Service — aktuell nur mailto-Vorschau.
4. **Original-Instone-Logo** einbinden (optional).
5. MwSt-Satz / Ansprechpartner in `CONFIG` prüfen.

## Mit Claude Code weiterbauen
Lege die drei Dateien in `~/dev/instone/` ab und starte Claude Code in diesem Ordner —
`CLAUDE.md` wird automatisch als Kontext geladen. Sinnvolle erste Prompts:
- „Setze die echten Pakete und Preise in `PACKAGES` ein: …"
- „Koppele die Bestellmenge automatisch an die Anzahl Einheiten aus dem Wizard."
- „Ersetze die mailto-Vorschau durch einen echten Versand über [Backend/Service]."
