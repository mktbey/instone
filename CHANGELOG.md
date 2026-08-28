# Changelog

Alle nennenswerten Änderungen an diesem Projekt werden in dieser Datei dokumentiert.

Das Format basiert auf [Keep a Changelog](https://keepachangelog.com/de/1.1.0/),
und dieses Projekt folgt [Semantic Versioning](https://semver.org/lang/de/).

## [0.12.1] - 2026-08-28

### Geändert
- Projekt-Setup deutlich überarbeitet: Modal breiter (`min(92vw, 880px)`), volle Höhe scrollbar mit fixiertem Kopf und Weiter-Button, sichtbare Sektions-Überschriften (Projektdaten / Rechnungsempfänger).
- Rechnungsempfänger-Block statt einzelnem Textfeld: Filiale, Vorname, Nachname, E-Mail, Straße, Hausnummer (Text, „12a" möglich), PLZ (genau 5 Ziffern), Ort — mit Layout Straße/Hausnummer und PLZ/Ort nebeneinander auf Desktop.
- Setup-Intro-Text neu und größer (~1.2rem): „…gemäß Rahmenvertrag zusammenstellen können."
- Instone Projektnummer: Pattern-/Format-Validierung entfernt, freier Text erlaubt (Feld bleibt Pflicht). Placeholder als Beispiel behalten.
- Menüreihenfolge: Projekt-Setup steht jetzt an erster Stelle vor Pakete und FAQ.
- Footer um vollständigen Kontaktblock ergänzt (Fabian Hammer + Beyonity Germany GmbH) mit `mailto:`, `tel:` und Website-Link.

### Entfernt
- Checkbox „Rechnungsadresse entspricht Projektadresse" (inkl. Übernahmelogik) und das kombinierte Rechnungsadress-Textfeld.
- Kombiniertes „Name Ansprechpartner"-Feld — ersetzt durch getrennte Vorname/Nachname-Felder in Formular, sessionStorage, Absende-Payload und Zusammenfassung.
- Hinweistext „Format: FG gefolgt von 5 Ziffern" unter der Projektnummer.
- Chat-Widget vollständig (runder Chat-Button unten rechts, Chat-Fenster, `toggleChat`/`sendChat`, zugehöriges CSS und Markup).

## [0.12.0] - 2026-08-28

### Geändert
- Einstieg komplett überarbeitet: Multistep-Wizard entfernt, ersetzt durch einseitiges **Projekt-Setup** (Projektadresse, Anzahl Wohnungen, Vermarktungsstart, Instone Projektnummer `FGxxxxx`, Rechnungsadresse mit Checkbox „entspricht Projektadresse").
- Projektsetup wird bei jedem Seitenbesuch zuerst angezeigt; Werte via **sessionStorage** vorbefüllt (Reload verliert nichts).
- Logo oben links ist jetzt Home-Button und öffnet das Setup mit vorbefüllten Werten — bestehende Paket-/Optionsauswahl bleibt erhalten.
- Top-Nav-Label „Angemeldet als" → „Projekt", zeigt die Instone Projektnummer.
- Checkout-Message und Erfolgs-Modal nutzen Projektnummer, Projekt- und Rechnungsadresse statt Name/E-Mail.
- FAQ-Inhalte komplett ersetzt (3 neue Fragen: „Was geschieht als Nächstes?", „Wie gebe ich das Angebot frei…", „Wie lange dauert die Aufbereitung…").

### Hinzugefügt
- Optionale Leistung **AddOn Realtime-Tour: Copy Tour** — 700 € netto (mit Mengenauswahl), einsortiert bei den Realtime-Tour-Optionen.
- Optionale Leistung **Übersichtsplan 2D** — 490 € netto, einsortiert nach der Interior Visualization.
- Pattern-Validierung Instone Projektnummer (`FG` + 5 Ziffern), Live-Uppercase-Normalisierung.
- Inline-Fehlerdarstellung für ungültige Setup-Felder (pinker Rand, Fokus auf erstes ungültiges Feld).

### Entfernt
- Alter Multistep-Wizard inkl. Name/E-Mail-Felder und Nutzungsart-Dropdown.
- localStorage-basierte Projekt-Persistenz (durch sessionStorage abgelöst).

## [0.11.0] - 2026-07-09

### Geändert
- Checkout sendet die Anfrage jetzt per `fetch`-POST an den n8n-Webhook `https://n8n.beyonity.com/webhook/instone-anfrage` (Payload `{ subject, message }`) statt über einen `mailto:`-Link.
- Absende-Button wird während des Versands deaktiviert und zeigt „Wird gesendet…" (Doppelklick-Schutz).
- Erfolgs-Modal enthält nur noch einen „Schließen"-Button.

### Hinzugefügt
- Fehlerbehandlung: Bei Netzwerkfehler oder Status ≠ 200 wird ein Hinweis „Anfrage konnte nicht gesendet werden, bitte später erneut versuchen" angezeigt und der Warenkorb bleibt erhalten.

### Entfernt
- `mailto:`-Versand und Button „Bestätigungs-Mail öffnen" im Erfolgs-Modal.

## [0.10.0] - 2026-07-09

### Geändert
- Paketpreise gemäß Angeboten AN-GE-26-0104/0105/0106 aktualisiert (L 50.912,50 € · XL 53.462,50 € · XXL 57.712,50 € netto).
- Wording durchgängig „Bestellung" → „Anfrage" (Headline „Anfrage-Übersicht", Button „Anfrage senden", Stepper, Status-Bar, Wizard, FAQ, Erfolgs-Modal, Mailto).

### Entfernt
- Sektion „Verlauf / Unsere Bestellungen" inkl. Nav-Link, Order-Detail-Modal, Seed-Daten und zugehörigem JS/CSS.

## [0.9.0] - 2026-07-09

### Changed
- Paketpreise gemäß Angeboten AN-GE-26-0104/0105/0106 aktualisiert (L/XL/XXL netto).
- Optionspreise verifiziert (Sonnensimulation, Mehrsprachigkeit, Realtime-Touren S/M, Interior Visualization, Videoclip-Project).
- Texte angepasst: „Warenkorb" → „Anfrage-Übersicht" (Drawer-Überschrift); „Bestellung senden" → „Anfrage senden" (Checkout-Button).
- Setup-Assistent auf 4 Schritte reduziert (Feld „Nutzungsart" entfernt).

### Added
- Vorschaubilder für alle Leistungs-Cards.
- Render-Paket-Galerie mit 20 Bildern.
- Versionierung (`APP_VERSION`) inkl. dezenter Anzeige im Footer.
- CHANGELOG.md nach „Keep a Changelog"-Format.
