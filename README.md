# Georeferenzierte Veranstaltungspläne

![Veranstaltungspläne](Bilder/IMG_0356.PNG)

[Details](Veranstaltungspläne.md)


> [!TIP]
> ✅ **Good example**
> ```python
> def add(a, b):
>     return a + b
> ```

> [!WARNING]
> ❌ **Bad example**
> ```python
> def add(a, b):
>     return a+b  # missing spaces
> ```

> [!NOTE]
> ❌ **note example**
> ```python
> def add(a, b):
>     return a+b  # missing spaces
> ```

> [!IMPORTANT]
> ❌ **important example**
> ```python
> def add(a, b):
>     return a+b  # missing spaces
> ```

> [!CAUTION]
> ❌ **caution example**
> ```python
> def add(a, b):
>     return a+b  # missing spaces
> ```

```geojson
{
  "type": "FeatureCollection",
  "features": [
    { 
      "type": "Feature",
      "properties": {
        "title": "My favorite spot",
        "description": "Best coffee in town",
        "marker-color": "#ff0000",
        "marker-size": "large",
        "stroke": "#0000ff",
        "stroke-width": 3,
        "fill": "#00ff00",
        "fill-opacity": 0.4
      },
      "geometry": {
          "type": "Point",
          "coordinates": [
            7.271547105819079,
            51.459387421814569
          ]
      }
    }
  ]
}
```