# AWW Aluminium-Werke Wutöschingen – Karriereseite

Recruiting-Landingpage / Ad-Funnel für die **Aluminium-Werke Wutöschingen AG & Co. KG**
(Wutöschingen). Stellen: **Maschinen- & Anlagenführer**, **CNC-Einrichter** und
**Ausbildungsstellen** (m/w/d).

Aufbau 1:1 an der ALWA-Karriereseite orientiert – im eigenen AWW-CI, mit den
drei oben genannten Positionen, einem Vorfilter-Formular und angebunden an die
LeadTable-Kachel von AWW.

## Inhalt

- `index.html` – die komplette Seite (self-contained, keine Build-Schritte nötig)
- `supabase-bewerbungen.sql` – legt den Storage-Bucket für den optionalen Lebenslauf-Upload an
- `.nojekyll` – sorgt dafür, dass GitHub Pages die Dateien 1:1 ausliefert
- `bilder/` – AWW-Logo (vorhanden: farbig + weiß); Hero-Fotos folgen mit dem Bildmaterial-Upload
- `creatives/` – Meta-Ads: Creatives + Werbetexte (folgen in SCHRITT 2 nach Bild-Upload)

## ⚠️ Noch zu bestätigen / einzupflegen

Diese Punkte sind mit sinnvollen, recherchierten Werten belegt und sollten mit
den echten Daten von AWW abgeglichen werden:

1. **CI-Farben & Schrift** – das AWW-Blau (`--brand:#1b558b`) ist direkt aus dem
   offiziellen AWW-Logo (`bilder/aww-logo.svg`) übernommen; dazu Schriften
   *Barlow* (Headlines) und *Inter* (Fließtext). Zum Feinjustieren einfach die
   `:root`-Variablen ganz oben im `<style>`-Block in `index.html` (und ggf. die
   Google-Fonts-Zeile im `<head>`) austauschen.
2. **Logo** – das offizielle AWW-Logo liegt in `bilder/` (`aww-logo.svg` farbig,
   `aww-logo-weiss.svg` weiß für dunkle Flächen) und wird automatisch verwendet.
   Fehlt eine Datei, greift der Text-Fallback „AWW“.
3. **Benefits** – die 6 Benefit-Kacheln basieren auf öffentlich verfügbaren
   Angaben von AWW (bAV, 30 Tage Urlaub, JobRad, Kantine, Schichtzulagen,
   Weihnachts-/Urlaubsgeld u. a.). Bitte final mit AWW bestätigen.
4. **Kontakt** – Telefon `07746 810` und `jobs@aww.de` sind aus öffentlichen
   Quellen übernommen – bitte die richtige (Bewerbungs-)Adresse/Telefonnummer
   prüfen.
5. **Impressum/Datenschutz-Links** – zeigen auf `https://www.aww.de/impressum/`
   bzw. `https://www.aww.de/datenschutz/`. Bitte die korrekten URLs verifizieren
   (Datenschutz-Slug ggf. anpassen).

## Bilder (Hero-Fotos & Logo)

Die Fotos gehören in den Ordner **`bilder/`**. Der Hero lädt automatisch das
passende Bild – fehlt es, bleibt ein Farbverlauf stehen (kein kaputtes Bild).
Erwartete Dateinamen:

- `bilder/hero.jpg` – allgemeines Hero-Bild (Startseite ohne Stellen-Parameter)
- `bilder/maschinenfuehrer.jpg` – bei `?stelle=maschinenfuehrer`
- `bilder/cnc-einrichter.jpg` – bei `?stelle=cnc`
- `bilder/ausbildung.jpg` – bei `?stelle=ausbildung`

Logo (optional, ersetzt den Text-Schriftzug automatisch):

- `bilder/aww-logo.svg` / `.png` – farbiges Logo (Kopfzeile)
- `bilder/aww-logo-weiss.svg` / `.png` – weißes Logo (Hero & Footer, dunkler Hintergrund)

Hero-Fotos: Querformat, mind. ~1600 px breit. Motiv rechts platzieren –
links liegt die Textfläche.

## Stellen-Deeplinks für die Ad

Die Anzeige kann direkt auf eine Stelle verlinken; die Seite wählt sie vor und
startet beim Vorfilter-Schritt:

- `…/?stelle=maschinenfuehrer`
- `…/?stelle=cnc`
- `…/?stelle=ausbildung`

## Screening / Vorfilterung

Das Bewerbungsformular ist ein 3-Schritt-Funnel zur Vorfilterung:

1. **Stelle wählen** (Maschinen- & Anlagenführer / CNC-Einrichter / Ausbildung)
2. **4 Qualifizierungsfragen**: Bereitschaft zur 3-Schicht, Deutschkenntnisse,
   Führerschein Klasse B, Hintergrund (Erfahrung / Quereinsteiger).
   Aussteuerung (kein Lead an LeadTable, freundliche Absage) in zwei Fällen:
   - **Produktionsstelle** ohne 3-Schicht-Bereitschaft (bei **Ausbildung** gilt das nicht).
   - **„Alles maximal schlecht"**: schwächste Option bei Schicht *und* Deutsch
     *und* Führerschein zugleich – auch bei der Ausbildung.
   **Quereinsteiger** werden **nie** allein deswegen ausgesteuert – ausdrücklich
   willkommen. Streng-/Locker-Stellschraube: `MIN_STRIKES` in `index.html`
   (3 = nur wenn wirklich alles am schlechtesten, 2 = strenger).
3. **Kontaktdaten** + optionaler Lebenslauf-Upload

Alle Antworten (Schicht, Deutsch, Führerschein, Hintergrund) werden mit an
LeadTable übergeben. Screen-out und Erfolg gelten nur für den aktuellen Besuch –
ein Seiten-Neuladen startet frisch (kein dauerhaftes Sperren per localStorage).

## Live schalten (GitHub Pages)

1. Repo-Settings → **Pages** → Source: **Deploy from a branch**, Branch: `main` / `/root`
   (oder den gewünschten Branch).
2. Nach ein paar Minuten ist die Seite unter `https://<user>.github.io/<repo>/`
   erreichbar (bzw. unter der hinterlegten Custom-Domain, z. B. `aww.de/karriere`).

## Bewerbungen (LeadTable)

Jede abgeschlossene Bewerbung wird per Webhook an LeadTable gesendet
(Felder u. a. `vorname`, `nachname` (getrennt, **kein** kombiniertes `name`-Feld,
sonst zeigt LeadTable den Namen doppelt), `email`, `telefon`, `stelle`,
`schicht`, `deutsch`, `fuehrerschein`, `hintergrund`, `lebenslauf`, `quelle`, `seite`).
Der Webhook ist in `index.html` in der Variable `WEBHOOK_URL` hinterlegt:

```
https://api-v2.lead-table.com/api/webhook/generic/…
```

Portal-Kachel (Leads einsehen):
`https://portal.lead-table.com/customer/6a8f02f883e182faf76b3d43/table/6a8f03157849fe409cdbd94a/leads`

## Lebenslauf-Upload (optional)

Der optionale Datei-Upload nutzt Supabase Storage (Bucket `bewerbungen`).
Er ist **standardmäßig deaktiviert** – die Bewerbung wird trotzdem gesendet
(Feld `lebenslauf` = „nicht hochgeladen“).

Zum Aktivieren:
1. Ein Supabase-Projekt anlegen, `supabase-bewerbungen.sql` einmalig im
   SQL-Editor ausführen.
2. In `index.html` `SUPABASE_URL` und `SUPABASE_KEY` (Publishable/anon Key) eintragen.

Danach landet im LeadTable-Feld `lebenslauf` ein direkt öffenbarer Link.
