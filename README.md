# TeWa Haustechnik – Karriereseite

Recruiting-Landingpage / Ad-Funnel für die **TeWa Haustechnik GmbH** (Balingen).
Stellen: **Anlagenmechaniker SHK** und **Servicetechniker SHK** (m/w/d).

Aufbau 1:1 an der ALWA-Karriereseite orientiert – in eigenem TeWa-CI, mit den
beiden oben genannten Positionen und angebunden an die LeadTable-Kachel von TeWa.

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert
- `bilder/` – Hero-Fotos & Logo (siehe unten)
- `creatives/` – Meta-Ads: Werbetexte (fertig) + Bild-Creatives (folgen, siehe Ordner)

## ⚠️ Noch zu bestätigen / einzupflegen

Diese Punkte sind mit sinnvollen Platzhaltern belegt und sollten mit den echten
Daten von TeWa abgeglichen werden:

1. **CI-Farben & Schrift** – aktuell ein professionelles Haustechnik-Blau
   (`--brand:#0e5aa7`). Zum Anpassen an das echte TeWa-Branding nur die
   `:root`-Variablen ganz oben im `<style>`-Block in `index.html` austauschen.
2. **Logo** – Text-Fallback „TeWa“. Sobald ein Logo in `bilder/` liegt
   (`tewa-logo.png`/`.svg` bzw. `tewa-logo-weiss.png`/`.svg`), wird es
   automatisch verwendet.
3. **Benefits** – die 6 Benefit-Kacheln sind ein fachlich passender Vorschlag
   für einen SHK-Meisterbetrieb (siehe Kommentar im Abschnitt `BENEFITS`).
   Bitte mit den tatsächlichen Benefits von TeWa ersetzen.
4. **E-Mail** – `info@tewa-haustechnik.de` ist eine Annahme. Bitte die richtige
   (Bewerbungs-)Adresse eintragen. Telefon `07433 3910270` ist aus dem öffentlichen
   Firmeneintrag übernommen – bitte prüfen.
5. **Impressum/Datenschutz-Links** – zeigen auf `https://tewa-haustechnik.de/impressum`
   bzw. `/datenschutz`. Bitte die korrekten URLs verifizieren.

## Bilder (Hero-Fotos & Logo)

Die Fotos gehören in den Ordner **`bilder/`**. Der Hero lädt automatisch das
passende Bild – fehlt es, bleibt ein Farbverlauf stehen (kein kaputtes Bild).
Erwartete Dateinamen:

- `bilder/hero.jpg` – allgemeines Hero-Bild (Startseite ohne Stellen-Parameter)
- `bilder/anlagenmechaniker.jpg` – bei `?stelle=anlagenmechaniker`
- `bilder/servicetechniker.jpg` – bei `?stelle=servicetechniker`

Logo (optional, ersetzt den Text-Schriftzug automatisch):

- `bilder/tewa-logo.svg` / `.png` – farbiges Logo (Kopfzeile)
- `bilder/tewa-logo-weiss.svg` / `.png` – weißes Logo (Hero & Footer, dunkler Hintergrund)

Hero-Fotos: Querformat, mind. ~1600 px breit. Motiv rechts platzieren –
links liegt die Textfläche.

## Stellen-Deeplinks für die Ad

Die Anzeige kann direkt auf eine Stelle verlinken; die Seite wählt sie vor und
startet beim Erfahrungs-Schritt:

- `…/?stelle=anlagenmechaniker`
- `…/?stelle=servicetechniker`

## Screening / Vorfilterung

Das Bewerbungsformular ist ein 3-Schritt-Funnel zur Vorfilterung:

1. **Stelle wählen** (Anlagenmechaniker / Servicetechniker)
2. **Qualifikation** (Ausbildung / Erfahrung) – wer „weder Ausbildung noch
   Erfahrung im SHK-Bereich“ wählt, wird ausgesteuert (kein Lead an LeadTable).
3. **Kontaktdaten** + optionaler Lebenslauf-Upload

Screen-out und Erfolg gelten nur für den aktuellen Besuch – ein Seiten-Neuladen
startet frisch (kein dauerhaftes Sperren per localStorage).

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`
   (oder den gewünschten Branch).
2. Nach ein paar Minuten ist die Seite unter `https://<user>.github.io/tewa-haustechnik/`
   erreichbar (bzw. unter der hinterlegten Custom-Domain, z. B. `tewa-haustechnik.de/karriere`).

## Bewerbungen (LeadTable)

Jede abgeschlossene Bewerbung wird per Webhook an LeadTable gesendet
(Felder u. a. `vorname`, `nachname`, `name`, `email`, `telefon`, `stelle`,
`erfahrung`, `lebenslauf`, `quelle`, `seite`).
Der Webhook ist in `index.html` in der Variable `WEBHOOK_URL` hinterlegt:

```
https://api-v2.lead-table.com/api/webhook/generic/…
```

Portal-Kachel (Leads einsehen):
`https://portal.lead-table.com/customer/6a9e9ca28d4aae7e0039840b/table/6a9e9cb32b0d1835c8e2b7d7/leads`

## Lebenslauf-Upload (optional)

Der optionale Datei-Upload nutzt Supabase Storage (Bucket `bewerbungen`).
Er ist **standardmäßig deaktiviert** – die Bewerbung wird trotzdem gesendet
(Feld `lebenslauf` = „nicht hochgeladen“).

Zum Aktivieren:
1. Ein Supabase-Projekt anlegen, `supabase-bewerbungen.sql` einmalig im
   SQL-Editor ausführen.
2. In `index.html` `SUPABASE_URL` und `SUPABASE_KEY` (Publishable/anon Key) eintragen.

Danach landet im LeadTable-Feld `lebenslauf` ein direkt öffenbarer Link.
