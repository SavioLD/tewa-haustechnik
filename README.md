# Gempper GmbH – Karriereseite

Recruiting-Landingpage / Ad-Funnel für die **Gempper GmbH Fertigungstechnik** (Albstadt).
Stellen: **Industriemechaniker** und **Zerspanungsmechaniker** (m/w/d).

Aufbau 1:1 an der ALWA-Karriereseite orientiert – im eigenen Gempper-CI, mit den
beiden oben genannten Positionen, einem Vorfilter-Funnel und angebunden an die
LeadTable-Kachel von Gempper.

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert
- `bilder/` – Hero-Fotos & Logo (siehe unten)
- `creatives/` – Meta-Ads: entstehen in **Schritt 2**, sobald das Bildmaterial vorliegt

## ⚠️ Noch zu bestätigen / einzupflegen

Diese Punkte sind mit sinnvollen Platzhaltern belegt und sollten mit den echten
Daten von Gempper abgeglichen werden:

1. **CI-Farben & Schrift** – an der Website `gempper-gmbh.de` abgenommen:
   tiefes Marine-/Petrolblau (`--brand-900:#163a4e`, `--brand:#2a5c7a`) + Weiß
   (monochrom), Schrift *Montserrat*. Feinjustage der Hex-Werte jederzeit über
   die `:root`-Variablen ganz oben im `<style>`-Block in `index.html`.
2. **Logo** – das echte weiße Gempper-Logo liegt in `bilder/`
   (`gempper-logo-weiss.avif` + `.png`-Fallback) und wird in Kopfzeile, Hero und
   Footer (alle im Marineblau) automatisch verwendet. Falls für andere Zwecke
   eine dunkle Logovariante gebraucht wird, einfach zusätzlich in `bilder/` ablegen.
3. **Benefits** – die 6 Benefit-Kacheln bilden die von Gempper vorgegebenen
   Leistungen ab: betriebliche Altersvorsorge (BAV/Altersvorsorge),
   vermögenswirksame Leistungen, Urlaubsgeld, voll bezahlte Überstunden,
   gestellte Arbeitskleidung und den sicheren Familienbetrieb.
4. **Kontaktdaten** – Adresse `Kohlplattenstraße 14 · 72459 Albstadt`, Telefon
   `07431 989749-0` und `info@gempper-gmbh.de` stammen aus öffentlichen
   Firmeneinträgen. Bitte prüfen bzw. die gewünschte Bewerbungs-Adresse eintragen.
5. **Impressum/Datenschutz-Links** – zeigen auf `https://www.gempper-gmbh.de/impressum`
   bzw. `/datenschutz` sowie die Canonical-URL auf `…/karriere/`. Bitte die
   korrekten URLs verifizieren.

## Bilder (Hero-Fotos & Logo)

Die Fotos gehören in den Ordner **`bilder/`**. Der Hero lädt automatisch das
passende Bild – fehlt es, bleibt ein Farbverlauf stehen (kein kaputtes Bild).
Erwartete Dateinamen:

- `bilder/hero.jpg` – allgemeines Hero-Bild (Startseite ohne Stellen-Parameter)
- `bilder/industriemechaniker.jpg` – bei `?stelle=industriemechaniker`
- `bilder/zerspanungsmechaniker.jpg` – bei `?stelle=zerspanungsmechaniker`

Logo (optional, ersetzt den Text-Schriftzug „GEMPPER“ automatisch):

- `bilder/gempper-logo.svg` / `.png` – farbiges Logo (Kopfzeile)
- `bilder/gempper-logo-weiss.svg` / `.png` – weißes Logo (Hero & Footer, dunkler Hintergrund)

Hero-Fotos: Querformat, mind. ~1600 px breit. Motiv rechts platzieren –
links liegt die Textfläche.

## Stellen-Deeplinks für die Ad

Die Anzeige kann direkt auf eine Stelle verlinken; die Seite wählt sie vor und
startet beim Qualifikations-Schritt:

- `…/?stelle=industriemechaniker`
- `…/?stelle=zerspanungsmechaniker`

## Screening / Vorfilterung

Das Bewerbungsformular ist ein 7-Schritt-Funnel zur Vorfilterung. Jeder Schritt
ist ein einziger Klick (Auto-Weiter), damit die Conversion hoch bleibt:

1. **Stelle wählen** (Industriemechaniker / Zerspanungsmechaniker / beides)
2. **Ausbildung & Erfahrung** – *Pflicht.* Wer „keine passende Ausbildung und
   keine Erfahrung im Metallbereich“ wählt, wird ausgesteuert.
3. **Wohnort & Umkreis** – *Pflicht.* Postleitzahl-Eingabe + Umkreis-Frage
   (max. ~30 km um Albstadt). Wer „Umzug/Pendeln kommt nicht infrage“ wählt,
   wird ausgesteuert.
4. **Führerschein** – *Pflicht.* Ohne Führerschein → Aussteuerung.
5. **Deutschkenntnisse** – *Pflicht.* Nur Grundkenntnisse (A1–A2) → Aussteuerung.
6. **MAZAK / Mazatrol** – *optional* (Kenntnisse sind ein Plus, kein Muss;
   keine Aussteuerung).
7. **Kontaktdaten** + optionaler Lebenslauf-Upload.

Ausgesteuerte Bewerbungen erzeugen **keinen** Lead in LeadTable. Screen-out und
Erfolg gelten nur für den aktuellen Besuch – ein Seiten-Neuladen startet frisch
(kein dauerhaftes Sperren per localStorage).

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`
   (oder den gewünschten Branch).
2. Nach ein paar Minuten ist die Seite unter `https://<user>.github.io/<repo>/`
   erreichbar (bzw. unter der hinterlegten Custom-Domain, z. B. `gempper-gmbh.de/karriere`).

## Bewerbungen (LeadTable)

Jede abgeschlossene (nicht ausgesteuerte) Bewerbung wird per Webhook an LeadTable
gesendet (Felder u. a. `vorname`, `nachname`, `name`, `email`, `telefon`, `plz`,
`stelle`, `qualifikation`, `umkreis`, `fuehrerschein`, `deutsch`,
`mazak_mazatrol`, `lebenslauf`, `quelle`, `seite`).
Der Webhook ist in `index.html` in der Variable `WEBHOOK_URL` hinterlegt:

```
https://api-v2.lead-table.com/api/webhook/generic/…
```

Portal-Kachel (Leads einsehen):
`https://portal.lead-table.com/customer/6a9986f6ae1832073e265d33/table/6a998711ae1832073e2665e1/leads`

## Lebenslauf-Upload (optional)

Der optionale Datei-Upload nutzt Supabase Storage (Bucket `bewerbungen`).
Er ist **standardmäßig deaktiviert** – die Bewerbung wird trotzdem gesendet
(Feld `lebenslauf` = „nicht hochgeladen“).

Zum Aktivieren:
1. Ein Supabase-Projekt anlegen, `supabase-bewerbungen.sql` einmalig im
   SQL-Editor ausführen.
2. In `index.html` `SUPABASE_URL` und `SUPABASE_KEY` (Publishable/anon Key) eintragen.

Danach landet im LeadTable-Feld `lebenslauf` ein direkt öffenbarer Link.
