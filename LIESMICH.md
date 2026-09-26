# ESPHome-LVGL Blueprints

Wiederverwendbare Bausteine für dein Display. Das Design machst du im Builder, die Funktion kommt aus diesen Dateien. Solange die Widget-IDs gleich bleiben, überlebt alles einen Neuexport.

## Einrichten

1. Den Ordner `blueprints` neben deine Geräte-YAML legen (bei GitHub-Build: mit ins Repo).
2. Den `packages:`-Block aus `beispiel_einbinden.yaml` in deine Geräte-YAML kopieren.
3. Entity-IDs (aus HA) und Widget-IDs (aus dem Builder) anpassen.

## Was es gibt

| Datei | Wofür | Nach dem Export von Hand am Widget? |
|---|---|---|
| `farben.yaml` | dein Farbkonzept an einer Stelle | nein |
| `status_icon.yaml` | Fenster, Tür, „Licht an im Raum“: Icon färbt sich | nein |
| `licht_schalter.yaml` | Licht-Icon zeigt Zustand und schaltet beim Antippen | ja: `on_click` → `script.execute: <uid>_toggle` |
| `licht_regler.yaml` | Helligkeits-Slider (0–255) in beide Richtungen | ja: `on_release` → `script.execute` mit Wert |
| `raumklima.yaml` | Temperatur und Luftfeuchtigkeit als Text | nein |
| `heizung.yaml` | Soll/Ist, Bogen, Flamme, Plus/Minus | ja: `on_click` an Plus und Minus |

Die genauen Zeilen für „von Hand“ stehen jeweils oben in der Datei.

## Wichtig

- Jede Einbindung braucht ein eigenes `uid`, sonst gibt es doppelte IDs.
- Für Befehle vom Display an HA muss in HA beim Gerät „Dem Gerät erlauben, Home-Assistant-Aktionen auszuführen“ an sein.
- Farben ändern: nur in `farben.yaml`, alle Icons passen sich an.
- Ungetestet zusammengestellt: Falls der Compiler bei einer Zeile meckert, die Meldung genau lesen, meist ist es ein Detail.
