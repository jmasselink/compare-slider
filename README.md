## Compare-Slider
### Using annual cloudless Sentinel-2 Web Map Services (WMS) in a side-by-side interactive comparison window.

This boilerplate `compare-slider` webpage is built with [MapLibre GL JS](https://maplibregljs.org), which is the fork of Mapbox GL JS. Included are the following packages:

- [`maplibre-gl-js`](https://github.com/maplibre/maplibre-gl-js)
- [`maplibre-gl-js-compare`](https://github.com/maplibre/maplibre-gl-compare)  
with these CDN references:
```
<script src="https://unpkg.com/maplibre-gl@4.7.1/dist/maplibre-gl.js"></script>
<link href="https://unpkg.com/maplibre-gl@4.7.1/dist/maplibre-gl.css" rel="stylesheet"/>
```

I found on the plugin's *Issues* page that the appropriate working CDN references for the plugin were:

```
<script src="https://cdn.jsdelivr.net/npm/@maplibre/maplibre-gl-compare@0.5.0/dist/maplibre-gl-compare.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@maplibre/maplibre-gl-compare@0.5.0/dist/maplibre-gl-compare.css" />
```

This integrates Sentinel-2 cloudless by EOX IT Services GmbH which has a Creative Commons Atribution-NonCommercial-ShareAlike 4.0 International License..

These WMS layers are integrated using the following references:

```
beforeMap.addSource("s2cloudless-tiles-left", {
            "type": "raster",
            "tiles": [
                `https://tiles.maps.eox.at/wms?service=WMS&request=GetMap&version=1.3.0&layers=s2cloudless-${mosaicLeft}_3857&styles=&format=image/png&crs=EPSG:3857&width=256&height=256&bbox={bbox-epsg-3857}`
            ],
            "tileSize": 256,
            "attribution": '<a href="https://s2maps.eu">Sentinel-2 cloudless</a> by <a href="https://eox.at">© EOX IT Services GmbH</a>'
        });
```

jQuery is used exclusively for DOM manipulation of the dropdown menus: populating the select elements such as `mosaicLeft` and `mosaicRight` with options defined by the `PERIODS` constant, retrieving those selected values, and binding change event handlers to update the map layers when users switch between Sentinel-2 imagery years.