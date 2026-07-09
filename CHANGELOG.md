# Changelog

Alle nennenswerten Änderungen an diesem Projekt werden in dieser Datei dokumentiert.

Das Format basiert auf [Keep a Changelog](https://keepachangelog.com/de/1.1.0/),
und dieses Projekt folgt [Semantic Versioning](https://semver.org/lang/de/).

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
