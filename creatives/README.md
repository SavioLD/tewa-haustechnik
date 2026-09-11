# Meta-Ads Creatives – TeWa Haustechnik

Hier liegen die Werbemittel für die Meta-Kampagne (Facebook/Instagram) zur
Anlagenmechaniker- und Servicetechniker-Suche.

## Status – fertig & im Repo

- ✅ **Werbetexte** – siehe [`werbetexte-meta-ads.md`](./werbetexte-meta-ads.md)
  (Primary Text, Headlines, Descriptions, CTAs für beide Stellen).
- ✅ **Bild-Creatives** – aus dem hochgeladenen Bildmaterial (`../bilder/`)
  gebaut: echtes Foto + sauberes TeWa-Text-Overlay (Headline, „Wir stellen ein",
  Subline, CTA „Jetzt bewerben"). Text ist scharf gerendert (kein KI-Text).
- ✅ **Hero-Fotos** – in die Seite eingebunden (web-optimiert als JPG).

## Meta-Creatives (dieser Ordner)

| Datei | Stelle | Format | Basis-Foto |
|-------|--------|--------|-----------|
| `creative-anlagenmechaniker-4x5.png`  | Anlagenmechaniker | Feed 4:5 (1080×1350)  | Monteur an der Heizung |
| `creative-anlagenmechaniker-story.png`| Anlagenmechaniker | Story/Reel 9:16 (1080×1920) | Monteur an der Heizung |
| `creative-servicetechniker-4x5.png`   | Servicetechniker  | Feed 4:5 (1080×1350)  | Heizraum / Wärmepumpe |
| `creative-servicetechniker-story.png` | Servicetechniker  | Story/Reel 9:16 (1080×1920) | Heizraum / Wärmepumpe |

Personen sind nur seitlich / von hinten bei der Arbeit zu sehen (kein Gesicht
zur Kamera). Das Servicetechniker-Motiv ist aktuell personenfrei (Wärmepumpe) –
für ein eigenes Servicetechniker-Foto einfach ein Bild als
`../bilder/servicetechniker-person.png` hochladen, dann wird daraus ein Creative
gebaut.

## Hero-Fotos (`../bilder/`)

| Datei | Motiv | Verwendung |
|-------|-------|-----------|
| `hero.jpg`             | Monteur an der Heizung (seitlich) | Startseite / allgemein |
| `anlagenmechaniker.jpg`| Monteur an der Heizung (seitlich) | `?stelle=anlagenmechaniker` |
| `servicetechniker.jpg` | Heizraum / Wärmepumpe | `?stelle=servicetechniker` |

Der Hero-Loader akzeptiert `.jpg`, `.jpeg`, `.png` und `.webp`. Zum Austauschen
einfach die Datei unter gleichem Namen in `../bilder/` ersetzen.

Anpassen: Overlay-Texte, Farben, Zuschnitt und Formate (z. B. zusätzlich 1:1)
lassen sich auf Wunsch ändern und neu rendern – einfach kurz Bescheid geben.
