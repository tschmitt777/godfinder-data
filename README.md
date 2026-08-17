# godfinder-data

Öffentliche Kartendaten für den **Parish Finder** auf [godfinder.world](https://godfinder.world) —
orthodoxe Kirchen und Gemeinden.

## churches.json

Wird automatisch aus dem Webflow-CMS erzeugt. **Nicht von Hand bearbeiten** —
Änderungen gehören ins CMS, danach wird die Datei neu gebaut.

```
https://raw.githubusercontent.com/tschmitt777/godfinder-data/main/churches.json
```

### Aufbau

```json
{
  "generated": "2026-08-08T22:03:15Z",
  "count": 374,
  "churches": [
    {
      "n":   "Saint Sergius of Radonezh Orthodox Church Bad Kissingen",
      "a":   "Salinenstr. 20, 97688 Bad Kissingen, Germany",
      "c":   "Bad Kissingen",
      "co":  "Germany",
      "lat": 50.205654,
      "lng": 10.078123,
      "v":   0,
      "s":   "saint-sergius-of-radonezh-orthodox-church-bad-kissingen"
    }
  ]
}
```

| Feld | Bedeutung |
|------|-----------|
| `n`  | Name der Gemeinde |
| `a`  | Adresse |
| `c`  | Stadt |
| `co` | Land |
| `lat` / `lng` | Koordinaten (WGS 84) |
| `v`  | 1 = geprüft, 0 = ohne Gewähr |
| `s`  | Slug (für spätere Detailseiten) |
| `j`  | Jurisdiktion, sofern bekannt (230 von 374) |
| `w`  | Website, sofern hinterlegt |
| `sched` | Gottesdienstzeiten als reiner Text, Zeilen mit `\n` getrennt (213 von 374) |
| `e` | E-Mail-Adresse der Gemeinde (128 von 374) |
| `p` | Telefonnummer der Gemeinde (102 von 374) |
| `prec` | Fehlt = Punkt sitzt genau auf dem Gebäude. `"street"` = nur die Straße ist bekannt. `"city"` = nur der Ort. |
| `img` | Foto (nur echte Fotos, keine Platzhalter) |
| `cr` | Bildnachweis: Urheber und Lizenz — bei Creative-Commons-Bildern Pflicht |

### cityAlias

Neben `churches` enthält die Datei `cityAlias` — die Namen jeder Stadt in
23 Sprachen (Englisch, Russisch, Griechisch, Chinesisch, Arabisch,
Georgisch, Armenisch, Serbisch, Bulgarisch, Ukrainisch, Türkisch,
Polnisch …). Damit findet die Suche der Karte jede Stadt in jeder Schrift,
**ohne einen fremden Dienst zu befragen**.

```json
"cityAlias": { "München": ["Munich","Мюнхен","慕尼黑","Μόναχο","ميونخ", ...] }
```

Erzeugt von `stadt-aliase.py`. Nur Schreibweisen, die vom deutschen Namen
abweichen, werden gespeichert.

### Jurisdiktionen

`Greek` · `Russian (ROC)` · `Russian (ROCOR)` · `Russian` · `Serbian` ·
`Romanian` · `Bulgarian` · `Georgian` · `Ukrainian` · `Antiochian`

`Russian` ohne Zusatz heißt: belegt russisch-orthodox, aber ob ROCOR oder ROC
geht aus den vorliegenden Angaben nicht hervor. Wo sich gar nichts belegen
ließ, bleibt das Feld leer — es wird nichts geraten.

### Genauigkeit der Koordinaten

| Genauigkeit | Anzahl | Feld `prec` |
|---|---|---|
| Gebäude oder Gebetsort | 128 | fehlt |
| nur die Straße bekannt | 22 | `"street"` |
| nur der Ort bekannt | 224 | `"city"` |

OpenStreetMap kennt längst nicht jede Hausnummer. Wo die Hausnummer fehlt,
liefert es einen Punkt auf der Straße — der kann mehrere hundert Meter daneben
liegen. Solche Punkte sind als `prec` gekennzeichnet, damit die Karte sie
gestrichelt darstellen und "ungefähre Lage" anzeigen kann, statt eine
Genauigkeit vorzutäuschen.

Die Herkunft steht pro Eintrag auch im CMS-Feld `source`.

## Herkunft und Lizenz

Die Koordinaten stammen von [OpenStreetMap](https://openstreetmap.org/copyright)
(Nominatim) sowie von GeoNames. Die Gemeindedaten selbst werden redaktionell
gepflegt.

**Fehler gefunden?** [Issue aufmachen](https://github.com/tschmitt777/godfinder-data/issues)
oder auf godfinder.world melden.
