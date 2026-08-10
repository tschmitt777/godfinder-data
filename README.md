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

### Jurisdiktionen

`Greek` · `Russian (ROC)` · `Russian (ROCOR)` · `Russian` · `Serbian` ·
`Romanian` · `Bulgarian` · `Georgian` · `Ukrainian` · `Antiochian`

`Russian` ohne Zusatz heißt: belegt russisch-orthodox, aber ob ROCOR oder ROC
geht aus den vorliegenden Angaben nicht hervor. Wo sich gar nichts belegen
ließ, bleibt das Feld leer — es wird nichts geraten.

### Genauigkeit der Koordinaten

- **151 Einträge** sind auf die genaue Straßenadresse verortet (OpenStreetMap)
- **184 Einträge** liegen auf Stadtebene, weil nur ein Ort bekannt ist
- **39 Einträge** liegen auf Stadtebene aus einer früheren GeoNames-Abfrage

Die Herkunft steht pro Eintrag im CMS-Feld `source`.

## Herkunft und Lizenz

Die Koordinaten stammen von [OpenStreetMap](https://openstreetmap.org/copyright)
(Nominatim) sowie von GeoNames. Die Gemeindedaten selbst werden redaktionell
gepflegt.

**Fehler gefunden?** [Issue aufmachen](https://github.com/tschmitt777/godfinder-data/issues)
oder auf godfinder.world melden.
