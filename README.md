# b&p Metalltechnik – Karriereseite

Recruiting-Landingpage / Ad-Funnel für die **b&p Metalltechnik GmbH** (Lennestadt).
Offene Stelle: **Zerspanungsmechaniker (m/w/d)**.

Aufbau 1:1 an der ALWA-Karriereseite orientiert – in eigenem b&p-CI, mit der
oben genannten Position und angebunden an die LeadTable-Kachel von b&p.

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert
- `bilder/` – Hero-Fotos & Logo (siehe unten) – **hier bitte das Bildmaterial ablegen**
- `creatives/` – Meta-Ads: Creatives + Werbetexte (folgen in Schritt 2, siehe Ordner)

## ⚠️ Noch zu bestätigen / einzupflegen

Diese Punkte sind mit sinnvollen Platzhaltern belegt und sollten mit den echten
Daten von b&p abgeglichen werden:

1. **CI-Farben & Schrift** – die Seite konnte aus der Build-Umgebung **nicht**
   auf `bp-metall.de` zugreifen (Netzwerk gesperrt), daher aktuell ein
   technisches Industrie-CI: Stahl-Blau (`--brand:#1f6fa5`) mit Graphit-Dunkel
   und einem Metallic-Akzent, Schrift „Barlow / Barlow Semi Condensed“.
   Zum Anpassen an das echte b&p-Branding nur die `:root`-Variablen ganz oben
   im `<style>`-Block in `index.html` austauschen (Farben + `--f-display`/`--f-body`).
2. **Logo** – Text-Fallback „b&p“. Sobald ein Logo in `bilder/` liegt
   (`bp-logo.png`/`.svg` bzw. `bp-logo-weiss.png`/`.svg`), wird es
   automatisch verwendet.
3. **Benefits** – die 6 Benefit-Kacheln sind ein fachlich passender Vorschlag
   für einen Zerspanungs-/Werkzeugbau-Betrieb (siehe Kommentar im Abschnitt
   `BENEFITS`). Bitte mit den tatsächlichen Benefits von b&p ersetzen.
4. **Vorfilter-Fragen** – der Funnel nutzt einen Vorschlag (Qualifikation +
   Schwerpunkt in der Zerspanung, siehe unten). Bitte prüfen/anpassen; ggf.
   z. B. Schichtbereitschaft oder CNC-Steuerung ergänzen.
5. **Kontaktdaten & Rechts-Links** – Telefon `02721 603140` und
   `info@bp-metall.de` sind aus dem öffentlichen Firmeneintrag übernommen.
   Impressum/Datenschutz zeigen auf `https://www.bp-metall.de/impressum/`
   bzw. `/datenschutz/`. Bitte die korrekten Adressen/URLs verifizieren.

## Bilder (Hero-Fotos & Logo)

Die Fotos gehören in den Ordner **`bilder/`**. Der Hero lädt automatisch das
passende Bild – fehlt es, bleibt ein Farbverlauf stehen (kein kaputtes Bild).
Erwartete Dateinamen:

- `bilder/hero.jpg` – Hero-Bild (allgemein; alternativ `zerspanungsmechaniker.jpg`)

Logo (optional, ersetzt den Text-Schriftzug automatisch):

- `bilder/bp-logo.svg` / `.png` – farbiges Logo (Kopfzeile)
- `bilder/bp-logo-weiss.svg` / `.png` – weißes Logo (Hero & Footer, dunkler Hintergrund)

Hero-Fotos: Querformat, mind. ~1600 px breit. Motiv rechts platzieren –
links liegt die Textfläche.

## Screening / Vorfilterung

Das Bewerbungsformular ist ein 3-Schritt-Funnel zur Vorfilterung – ausgelegt
auf **Bewerberqualität statt reiner Masse**:

1. **Qualifikation** – Ausbildung Zerspanungsmechaniker / vergleichbarer
   Metallberuf / Berufserfahrung. Wer „weder Ausbildung noch Erfahrung in der
   Metallbearbeitung“ wählt, wird ausgesteuert (kein Lead an LeadTable).
2. **Schwerpunkt** – CNC-Fräsen / -Drehen / beides / Einsteiger (nur zur
   Einordnung, keine Aussteuerung).
3. **Kontaktdaten** + optionaler Lebenslauf-Upload.

Screen-out und Erfolg gelten nur für den aktuellen Besuch – ein Seiten-Neuladen
startet frisch (kein dauerhaftes Sperren per localStorage).

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`
   (oder den gewünschten Branch).
2. Nach ein paar Minuten ist die Seite unter `https://<user>.github.io/<repo>/`
   erreichbar (bzw. unter der hinterlegten Custom-Domain, z. B. `bp-metall.de/karriere`).

## Bewerbungen (LeadTable)

Jede abgeschlossene Bewerbung wird per Webhook an LeadTable gesendet
(Felder u. a. `vorname`, `nachname`, `name`, `email`, `telefon`, `stelle`,
`qualifikation`, `schwerpunkt`, `lebenslauf`, `quelle`, `seite`).
Der Webhook ist in `index.html` in der Variable `WEBHOOK_URL` hinterlegt:

```
https://api-v2.lead-table.com/api/webhook/generic/…
```

Portal-Kachel (Leads einsehen):
`https://portal.lead-table.com/customer/6a9fbc8bd7eae5fa903160b4/table/6a9fbca556885b968028a7a2/leads`

## Lebenslauf-Upload (optional)

Der optionale Datei-Upload nutzt Supabase Storage (Bucket `bewerbungen`).
Er ist **standardmäßig deaktiviert** – die Bewerbung wird trotzdem gesendet
(Feld `lebenslauf` = „nicht hochgeladen“).

Zum Aktivieren:
1. Ein Supabase-Projekt anlegen, `supabase-bewerbungen.sql` einmalig im
   SQL-Editor ausführen.
2. In `index.html` `SUPABASE_URL` und `SUPABASE_KEY` (Publishable/anon Key) eintragen.

Danach landet im LeadTable-Feld `lebenslauf` ein direkt öffenbarer Link.
