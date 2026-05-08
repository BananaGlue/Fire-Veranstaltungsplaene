# Georeferenzierte Veranstaltungspläne

![](Bilder/IMG_0356.PNG)

[Details](Veranstaltungspläne.md)

### Punktebene

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
>   "geometry": {}
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
>   "geometry": {}
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
>   "geometry": {}
> }
> ```




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