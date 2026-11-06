# Nebenkosten & Energie Tracker

Eine lokal gespeicherte, smartphonefreundliche Web-App für Zählerstände, Verbrauchsauswertung und Kostenprognosen.

## Dateien

- `index.html` – vollständige Anwendung
- `manifest.webmanifest` – PWA-Installationsinformationen
- `sw.js` – Offline-Cache für die App-Dateien
- `icon.svg` – App-Symbol

## Veröffentlichung über GitHub Pages

1. Erstelle auf GitHub ein neues Repository.
2. Lade alle vier Dateien aus diesem Ordner direkt in das Hauptverzeichnis des Repositorys hoch.
3. Öffne **Settings → Pages**.
4. Wähle bei **Build and deployment** die Option **Deploy from a branch**.
5. Wähle den Branch `main` und den Ordner `/ (root)`, danach **Save**.
6. Warte, bis GitHub Pages die Seite veröffentlicht hat. Die URL wird in den Pages-Einstellungen angezeigt.

## Installation auf dem iPhone

1. Öffne die veröffentlichte HTTPS-Adresse in Safari.
2. Tippe auf **Teilen**.
3. Wähle **Zum Home-Bildschirm**.
4. Starte die App über das neue Symbol.

## Tarife eintragen

Unter ⚙ → Einstellungen & Tarife können getrennt hinterlegt werden:

- Strom: Arbeitspreis in €/kWh, Grundpreis in €/Monat und optionaler monatlicher Abschlag
- Fernwärme: Arbeitspreis in €/kWh, Grundpreis in €/Monat und Heizkosten-Abschlag
- Betriebskosten-Abschlag
- Strom-Jahresziel und Beginn des Abrechnungszeitraums

Ein leerer Tarif wird als 0 behandelt und nicht durch einen erfundenen Standardpreis ersetzt. Kostenprognosen sind Schätzungen anhand der eingetragenen Verbrauchswerte und Preise. Die Betriebskosten-Vorauszahlung wird separat ausgewiesen; ohne tatsächliche Betriebskosten lässt sich daraus keine seriöse Nachzahlung berechnen.

## Daten und Datenschutz

Die Ablesungen und Einstellungen werden im lokalen Speicher des Browsers auf dem verwendeten Gerät abgelegt. Es gibt keinen Server und keine automatische Synchronisierung zwischen Geräten. Erstelle regelmäßig ein JSON-Backup über **JSON sichern**. Ein Browserwechsel, das Löschen der Website-Daten oder ein anderes Gerät übernimmt die Daten nicht automatisch.

## Hinweise zur Berechnung

- Verbrauchsraten werden aus den Differenzen zwischen zwei Ablesungen und der tatsächlichen Anzahl der Tage berechnet.
- Die Jahresprognose addiert den bereits gemessenen Verbrauch seit dem ersten Eintrag zum prognostizierten Verbrauch bis zum 31. Dezember.
- Die Monatsgrafik verteilt Verbrauch zwischen zwei Ablesungen nach Kalendertagen auf die betroffenen Monate.
- Strom-Jahresziel wird im Einzugsjahr anhand der tatsächlichen Kalendertage anteilig berechnet.
- Rückläufige Zählerstände werden beim Speichern abgewiesen, damit Zählerwechsel oder Korrekturen nicht unbemerkt als Nullverbrauch erscheinen. Bei einem Zählerwechsel sollte ein eigener Zählerwechsel-/Korrekturmechanismus ergänzt werden.

## Offline-Funktion

Die App-Dateien werden nach dem ersten erfolgreichen Online-Aufruf durch den Service Worker zwischengespeichert. Die erste Bereitstellung und das erstmalige Laden müssen online erfolgen. Es werden keine externen JavaScript- oder CSS-CDNs benötigt.
