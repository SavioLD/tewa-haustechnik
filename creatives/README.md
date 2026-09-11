# Meta-Ads Creatives – TeWa Haustechnik

Hier liegen die Werbemittel für die Meta-Kampagne (Facebook/Instagram) zur
Anlagenmechaniker- und Servicetechniker-Suche.

## Status

- ✅ **Werbetexte** – fertig: siehe [`werbetexte-meta-ads.md`](./werbetexte-meta-ads.md)
  (Primary Text, Headlines, Descriptions, CTAs für beide Stellen).
- ✅ **Bild-Creatives** – KI-generiert (Higgsfield / gpt_image_2), fotorealistisch
  im TeWa-Blau, mit eingebranntem Headline + CTA. Müssen manuell hier abgelegt
  werden (siehe unten).

## Ablage der generierten Bilder

> Hinweis: Diese Repo-Umgebung darf die generierten Bilder nicht automatisch
> vom Bild-CDN herunterladen (Egress-Policy). Deshalb bitte die Bilder aus dem
> Higgsfield-Widget herunterladen und mit **genau diesen Dateinamen** ablegen:

Meta-Creatives (in diesen Ordner `creatives/`):

| Datei | Stelle | Format |
|-------|--------|--------|
| `creative-anlagenmechaniker-4x5.png`  | Anlagenmechaniker | Feed (Portrait 3:4 → 4:5) |
| `creative-anlagenmechaniker-story.png`| Anlagenmechaniker | Story/Reel 9:16 |
| `creative-servicetechniker-4x5.png`   | Servicetechniker  | Feed (Portrait 3:4 → 4:5) |
| `creative-servicetechniker-story.png` | Servicetechniker  | Story/Reel 9:16 |
| `creative-allgemein-4x5.png`          | Beide (ohne Person)| Feed (Portrait 3:4 → 4:5) |
| `creative-allgemein-story.png`        | Beide (ohne Person)| Story/Reel 9:16 |

Personen in den Motiven sind bewusst nur von der Seite / von hinten bei der
Arbeit zu sehen (kein Gesicht zur Kamera). Zusätzlich gibt es personenfreie
Varianten.

Hero-Fotos (in den Ordner `../bilder/`):

| Datei | Motiv |
|-------|-------|
| `hero.png` (oder `.jpg`)             | allgemein (Person von hinten) |
| `anlagenmechaniker.png` (oder `.jpg`)| bei `?stelle=anlagenmechaniker` (Person seitlich) |
| `servicetechniker.png` (oder `.jpg`) | bei `?stelle=servicetechniker` (Person von hinten) |
| `hero-ohne-person.png` (optional)    | personenfrei: Heizraum / Wärmepumpe |
| `motiv-bad.png` (optional)           | personenfrei: modernes Bad |

> Die optionalen personenfreien Hero-Motive können auch als `hero.png`
> verwendet werden, wenn gar keine Person im Hero gezeigt werden soll.

Der Hero-Loader akzeptiert `.jpg`, `.jpeg`, `.png` und `.webp` – die PNGs
aus der Generierung können also direkt (umbenannt) verwendet werden.

Die Claims/Texte der Creatives orientieren sich an den Werbetexten in
`werbetexte-meta-ads.md`. Feld-Feintuning der eingebrannten Typografie ggf.
in Canva/Photoshop möglich (Basis-Bild bleibt nutzbar).
