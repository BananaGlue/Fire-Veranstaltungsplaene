# Georeferenzierte Veranstaltungspläne

Daten- und Stylemodell für die Darstellung von feuerwehrrelevanten Veranstaltungsinformationen auf Karten.

![](Bilder/Veranstaltungspläne.png)

Das Datenmodell besteht aus vorgegebenen GeoJSON-Properties und einer Style-Vorlage, die applikationsspezifisch umzusetzen ist.

## Datenmodell

Je eine GeoJSON Datei als FeatureCollection mit WGS84 als Koordinatenprojektion:

- Punktebene: `Veranstaltungen_p.geojson`
- Linienebene: `Veranstaltungen_l.geojson`
- Polygonebene: `Veranstaltungen_f.geojson`

Die Dateien sind entsprechend zu benennen.

### GeoJSON Feature Properties:

| Name | Beschreibung | Verpflichtend? |
| --- | ----------- | ----------- |
| Typ | Definiert den Typ des Features, notwendig für die Darstellungskonfiguration (Style). | MUSS |
| Titel | Optionaler Titel, der in der Karte unter eines Punkt, entlang einer Linie oder innerhalb eines Polygones dargestellt wird. | KANN |
| Info | Optionale Hinweise, die in einer Detailansicht zum Kartenelement dargestellt werden. | KANN |
| Gefahren | Optionale Gefahrenhinweise, die in einer Detailansicht zum Kartenelement dargestellt werden. | KANN |

#### Beispiel
> [!TIP]
> **Beispiel FeatureCollection mit einem Punktfeature**
> ```json
> {
>   "type": "FeatureCollection",
>   "features": [
>     {
>       "type": "Feature",
>       "properties": {
>         "Typ": "Punkt Rot X",
>         "Titel": "Metalbühne"
>       },
>       "geometry": {
>         "type": "Point"
>         "coordinates": [
>           7.27044,
>           51.45743
>         ]
>       }
>     }
>   ]
> }
> ```

### Punkttypen

Im folgenden werden die Ausprägungen der einzelnen Punkttypen und deren gedachter Anwendungszweck definiert:

| Typ | Angedachte Verwendung | Vorschau | Beispiel Feature Properties |
| --- | ----------- | ----------- | ----------- |
| Hinweis | Darstellung von Texthinweisen. | ![](Bilder/Punkt_Blau_2.png) | `{ "Typ": "Punkt Blau 2", "Titel": "Test2" }` |
| Punkt (Rot\|Gelb\|Grün\|Blau\|Lila) ([1-50]\|[A-Z]) | Darstellung von durchnummerierten / durchbuchstabierten Punkten. Der Kontext ergibt sich aus weiteren Kartenelementen der Umgebung oder aus dem optionalen Titel. | ![](Bilder/Punkt_Blau_2.png) | <pre> { <br> &emsp; "Typ": "Punkt Blau 2",<br> &emsp; "Titel": "Test2" <br> } </pre> |
| Bereitstellungsraum | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | ![](Bilder/Punkt_Blau_2.png) | |
| Bereitstellungszone | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | ![](Bilder/Punkt_Blau_2.png) | |
| Einsatzleitung | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | ![](Bilder/Punkt_Blau_2.png) | |
| Befehlsstelle | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | ![](Bilder/Punkt_Blau_2.png) | |
| Drohnengruppe | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | ![](Bilder/Punkt_Blau_2.png) | |
| Behandlungsplatz | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | ![](Bilder/Punkt_Blau_2.png) | |

Bei der Geometrie sind jeweils sowohl die Einzelobjekte als auch die jeweiligen Multiobjekte möglich (z. B. `Point`, als auch `MultiPoint`).

#### Beispiele

`Typ` MUSS vorhanden sein, `Titel`, `Info` und `Gefahren` sind optional (können weggelassen werden) oder können `null` zugewiesen bekommen.

> [!TIP]
> **Beispiel: nur Typ**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Aufbauten"
>   },
>   "geometry": {...}
> }
> ```

> [!TIP]
> **Beispiel: Titel, Info und Gefahren mit Textzuweisung**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Aufbauten",
>     "Titel": "Stand 27",
>     "Info": "Bratmax",
>     "Gefahren": "Gas"
>   },
>   "geometry": {...}
> }
> ```

> [!TIP]
> **Beispiel: Titel, Info und Gefahren mit null Zuweisung**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Aufbauten",
>     "Titel": null,
>     "Info": null,
>     "Gefahren": null
>   },
>   "geometry": {...}
> }
> ```

#### Fehlervermeidung

Es ist darauf zu achten, dass die Typen exakt wie angegeben definiert sind. Zusätzliche Leerzeichen oder abweichende Kleinschreibung führt zu fehlerhafter Darstellung.

> [!CAUTION]
> ❌ **Negativbeispiel: Leerzeichen am Ende**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Punkt Gelb X "
>   },
>   "geometry": {...}
> }
> ```

> [!CAUTION]
> ❌ **Negativbeispiel: mehr als ein Leerzeichen zwischen den Textbausteinen**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Punkt Gelb  X"
>   },
>   "geometry": {...}
> }
> ```

> [!CAUTION]
> ❌ **Negativbeispiel: abweichende Kleinschreibung zu Vorgabe**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Punkt gelb x"
>   },
>   "geometry": {...}
> }
> ```

### Linientypen

Im folgenden werden die Ausprägungen der einzelnen Linientypen und deren gedachter Anwendungszweck definiert:

| Typ | Angedachte Verwendung | Beispiel | Vorschau |
| --- | ----------- | ----------- | ----------- |
| Richtungspfeil | Darstellung von Bewegungsrichtungen. | Stellt die Verlaufsrichtung eines Veranstaltungszuges dar. | ![](Bilder/Punkt_Blau_2.png) |
| Zaunanlage | Darstellung von Zäunen. | Stellt einen Zaun dar. Sollte in Kombination mit Zugang oder Zufahrt verwendet werden um Zugangsmöglichkeiten darzustellen. | ![](Bilder/Punkt_Blau_2.png) |



Bei der Geometrie sind jeweils sowohl die Einzelobjekte als auch die jeweiligen Multiobjekte möglich (z. B. `LineString` als auch `MultiLineString`).

### Polygontypen

Im folgenden werden die Ausprägungen der einzelnen Polygontypen und deren gedachter Anwendungszweck definiert:

| Typ | Angedachte Verwendung | Beispiel | Vorschau |
| --- | ----------- | ----------- | ----------- |
| Fläche (Rot\|Gelb\|Grün\|Blau\|Lila) | Darstellung von Veranstaltungsflächen. | Aufteilung der Veranstaltungsfläche in unterschiedliche Bereiche / Zuständigkeiten. | ![](Bilder/Punkt_Blau_2.png) |
| Aufbauten | Darstellung von Veranstaltungsaufbauten. | Hütten / Stände oder ähnliches. | ![](Bilder/Punkt_Blau_2.png) |
| Aufstellfläche | Vordefinierte Aufstellflächen für die Feuerwehr. | Aufstellfläche nach DIN 14095.Bereitstellungszonen oder Behandlungsplätze. | ![](Bilder/Punkt_Blau_2.png) |
| (Feste\|Mobile\|Teilmobile) Sperre | Sperren im Rahmen des Veranstaltungsschutzes. | Zeigt anfahrenden Kräften Durchlassmöglichkeiten bzw. für die Anfahrt ungeeignete Straßen. | ![](Bilder/Punkt_Blau_2.png) |
| Indutainer | Sperre im Rahmen des Veranstaltungsschutzes. | Zeigt anfahrenden Kräften Durchlassmöglichkeiten bzw. für die Anfahrt ungeeignete Straßen. | ![](Bilder/Punkt_Blau_2.png) |
| Zugang | Zugang zu einem Gebäude. | Zugang nach DIN 14095. | ![](Bilder/Punkt_Blau_2.png) |
| Zufahrt | Zufahrt zu der Veranstaltung. | Zufahrt nach DIN 14095. | ![](Bilder/Punkt_Blau_2.png) |


Bei der Geometrie sind jeweils sowohl die Einzelobjekte als auch die jeweiligen Multiobjekte möglich (z. B. `Polygon` als auch `MultiPolygon`).

### JSON schema

Für die drei Ebenen existiert jeweils auch ein json.schema:

- [Punktebene Schema](.schemas/Veranstaltungen_p.schema.json)
- [Linienebene Schema](.schemas/Veranstaltungen_p.schema.json)
- [Polygonebene Schema](.schemas/Veranstaltungen_p.schema.json)

## Stylemodell

Die Darstellung der Daten ist applikationsspezifisch umzusetzen. 

#### Punkttypen

Im folgenden werden die zu verwendenden Füllfarben und Symbole der einzelnen Punkttypen definiert, die Symbole verweisen exemplarisch auf `Apple SF Symbols` (applikationsspezifisch):

| Typ | Füllfarbe (hex) | Symbol |
| --- | ----------- | ----------- | 
| Hinweis | #333333EE | `circle.fill` |
| Punkt Rot ([1-50]\|[A-Z]) | #FF0000AA | `[1-50]|[A-Z].circle.fill` |
| Punkt Gelb ([1-50]\|[A-Z]) | #FFFF00AA | `[1-50]|[A-Z].circle.fill` |
| Punkt Grün ([1-50]\|[A-Z]) | #00FF00AA | `[1-50]|[A-Z].circle.fill` |
| Punkt Blau ([1-50]\|[A-Z]) | #00aaffAA | `[1-50]|[A-Z].circle.fill` |
| Punkt Lila ([1-50]\|[A-Z]) | #eb34b1AA | `[1-50]|[A-Z].circle.fill` |

#### Linientypen

Im folgenden werden die zu verwendenden Linienfarben und Dashpattern der einzelnen Linientypen definiert:

| Typ | Linienfarbe (hex) | Dashpattern |
| --- | ----------- | ----------- | 
| Richtungspfeil | #8F34EBEE   | `- -` |
| Zaunanlage | #000000EE | `- . .` |

#### Polygontypen

Im folgenden werden die zu verwendenden Linienfarben, Dashpattern und Füllfarben der einzelnen Polygontypen definiert:

| Typ | Linienfarbe (hex) | Dashpattern | Füllfarbe (hex) |
| --- | ----------- | ----------- | ----------- | 
| Fläche Rot | #000000AA | `-` | #FF000066 | 
| Fläche Gelb | #000000AA | `-` | #FFFF0066 | 
| Fläche Grün | #000000AA | `-` | #00FF0066 |
| Fläche Blau | #000000AA | `-` | #00aaff66 |
| Fläche Lila | #000000AA | `-` | #eb34b166 |
| Aufbauten | #000000AA | `-` | #FBB13066 |
| Aufstellfläche | #FF0000 | `- -` | #8080807F |
| Feste Sperre | #000000 | `-` | #FF0000AA |
| Mobile Sperre | #000000 | `- -` | #00FF00AA |
| Teilmobile Sperre | #000000 | `-` | #FFFF00AA |
| Indutainer | #000000 | `-` | #0000FFAA |
| Zugang | - | - | #000000 |
| Zufahrt | #000000 | `-` | #00FF00AA |

#### Hilfspunkttypen

Im folgenden werden die zu verwendenden Füllfarben und Symbole der definierten Spezialfälle in Form von Hilfspunkttypen definiert, die Symbole verweisen exemplarisch auf `Apple SF Symbols` (applikationsspezifisch) oder auf die DIN 14095:

| Typ | Spezialfall | Symbol |
| --- | ----------- | ----------- | 
| Aufbauten (Polygon) | `Gefahren == 'Gas'` | DIN 14095 `P617` |


### Punkttypen

| Beispiel 1 | Beispiel 2 | Beispiel 3 |
|------------|-----------|-----------|
| ![](Bilder/Punkt_Blau_2.png) | ![](Bilder/Punkt_Gelb_3.png) | ![](Bilder/Punkt_Rot_X.png) |


> [!TIP]
> **Beispiel 1**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Punkt Blau 2",
>     "Titel": "Test2"
>   },
>   "geometry": {...}
> }
> ```

> [!TIP]
> **Beispiel 2**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Punkt Gelb 3",
>     "Titel": "Test3"
>   },
>   "geometry": {...}
> }
> ```

> [!TIP]
> **Beispiel 3**
> ```json
> {
>   "type": "Feature",
>   "properties": {
>     "Typ": "Punkt Rot X",
>     "Titel": "Metalbühne"
>   },
>   "geometry": {...}
> }
> ```
