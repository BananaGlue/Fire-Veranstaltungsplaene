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
          "title": "A title",
          "description": "A description",
          "marker-size": "medium",
          "marker-symbol": "bus",
          "marker-color": "#fff",
          "stroke": "#555555",
          "stroke-opacity": 1.0,
          "stroke-width": 2,
          "fill": "#555555",
          "fill-opacity": 0.5
      },
      "geometry": {
          "type": "Point",
          "coordinates": [0, 0]
      }
    }
  ]
}
```