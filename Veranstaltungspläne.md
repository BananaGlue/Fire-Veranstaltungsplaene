# Georeferenzierte Veranstaltungspläne

Daten- und Stylemodell für die Darstellung von feuerwehrrelevanten Veranstaltungsinformationen auf Karten.

## Datenmodell

Je eine GeoJSON Datei als FeatureCollection mit WGS84 als Koordinatenprojektion:

- Punktebene
- Linienebene
- Polygonebene

Bei der Geometrie sind jeweils sowohl die Einzelobjekte als auch die jeweiligen Multiobjekte möglich (z. B. Polygon als auch MultiPolygon).

Für das Datenmodell existiert ein json.schema.

#### GeoJSON Properties:

| Name | Beschreibung | Verpflichtend? |
| --- | ----------- | ----------- |
| Typ | Definiert den Typ des Features, notwendig für die Darstellungskonfiguration (Style). | MUSS |
| Titel | Optionaler Titel, der in der Karte unter eines Punkt, entlang einer Linie oder innerhalb eines Polygones dargestellt wird. | KANN |
| Info | Optionale Hinweise, die in einer Detailansicht zum Kartenelement dargestellt werden. | KANN |
| Gefahren | Optionale Gefahrenhinweise, die in einer Detailansicht zum Kartenelement dargestellt werden. | KANN |

#### Punkttypen

Im folgenden werden die Ausprägungen der einzelnen Punkttypen und deren gedachter Anwendungszweck definiert:

| Typ | Angedachte Verwendung | Beispiel |
| --- | ----------- | ----------- | 
| Hinweis | Darstellung von Texthinweisen. | Ab hier keine Wendemöglichkeit mehr. |
| Punkt (Rot\|Gelb\|Grün\|Blau\|Lila) ([1-50]|[A-Z]) | Darstellung von durchnummerierten / durchbuchstabierten Punkten. Der Kontext ergibt sich aus weiteren Kartenelementen der Umgebung oder aus dem optionalen Titel. | Punkt Rot 13 |
| Bereitstellungsraum | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | BR-Z1 |
| Bereitstellungszone | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | BR-3 |
| Einsatzleitung | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | EL FW |
| Befehlsstelle | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | BfSt Pol |
| Drohnengruppe | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | Drohnengruppe |
| Behandlungsplatz | Darstellung von taktischen Zeichen für vorgeplante Orte mit taktischer Bedeutung. | BHP-1 |

#### Linientypen

Im folgenden werden die Ausprägungen der einzelnen Linientypen und deren gedachter Anwendungszweck definiert:

| Typ | Angedachte Verwendung | Beispiel |
| --- | ----------- | ----------- | 
| Richtungspfeil | Darstellung von Bewegungsrichtungen. | Stellt die Verlaufsrichtung eines Veranstaltungszuges dar. |
| Zaunanlage | Darstellung von Zäunen. | Stellt einen Zaun dar. Sollte in Kombination mit Zugang oder Zufahrt verwendet werden um Zugangsmöglichkeiten darzustellen. |

#### Polygontypen

Im folgenden werden die Ausprägungen der einzelnen Polygontypen und deren gedachter Anwendungszweck definiert:

| Typ | Angedachte Verwendung | Beispiel |
| --- | ----------- | ----------- | 
| Fläche (Rot\|Gelb\|Grün\|Blau\|Lila) | Darstellung von Veranstaltungsflächen. | Aufteilung der Veranstaltungsfläche in unterschiedliche Bereiche / Zuständigkeiten. |
| Aufbauten | Darstellung von Veranstaltungsaufbauten. | Hütten / Stände oder ähnliches. |
| Aufstellfläche | Vordefinierte Aufstellflächen für die Feuerwehr. | Aufstellfläche nach DIN 14095.Bereitstellungszonen oder Behandlungsplätze. |
| (Feste\|Mobile\|Teilmobile) Sperre | Sperren im Rahmen des Veranstaltungsschutzes. | Zeigt anfahrenden Kräften Durchlassmöglichkeiten bzw. für die Anfahrt ungeeignete Straßen. |
| Indutainer | Sperre im Rahmen des Veranstaltungsschutzes. | Zeigt anfahrenden Kräften Durchlassmöglichkeiten bzw. für die Anfahrt ungeeignete Straßen. |
| Zugang | Zugang zu einem Gebäude. | Zugang nach DIN 14095. |
| Zufahrt | Zufahrt zu der Veranstaltung. | Zufahrt nach DIN 14095. |

## Stylemodell

Die Darstellung der Daten ist applikationsspezifisch umzusetzen. 

#### Punkttypen

Im folgenden werden die zu verwendenden Füllfarben und Symbole der einzelnen Punkttypen definiert, die Symbole verweisen exemplarisch auf `Apple SF Symbols`:

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

Im folgenden werden die zu verwendenden Füllfarben und Symbole der definierten Spezialfälle in Form von Hilfspunkttypen definiert, die Symbole verweisen exemplarisch auf `Apple SF Symbols` oder auf die DIN 14095:

| Typ | Spezialfall | Symbol |
| --- | ----------- | ----------- | 
| Aufbauten (Polygon) | `Gefahren == 'Gas'` | DIN 14095 `P617` |
