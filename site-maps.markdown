---
title: GIS Shapefile Viewer
layout: default
---

<div id="map" style="width: 100%; height: 600px;"></div>

<script src="https://cdn.jsdelivr.net/npm/ol@v7.3.0/dist/ol.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/ol@v7.3.0/ol.css">

<script>
  // Create the map
  const map = new ol.Map({
    target: 'map',
    layers: [
      new ol.layer.Tile({
        source: new ol.source.OSM()
      })
    ],
    view: new ol.View({
      center: ol.proj.fromLonLat([0, 0]),
      zoom: 2
    })
  });

  // Add shapefile layer
  const shapefileLayer = new ol.layer.Vector({
    source: new ol.source.Vector({
      url: 'https://openlayers.org/data/vector/ecoregions.json',
      format: new ol.format.GeoJSON()
    }),
    style: new ol.style.Style({
      stroke: new ol.style.Stroke({
        color: 'blue',
        width: 2
      }),
      fill: new ol.style.Fill({
        color: 'rgba(0, 0, 255, 0.1)'
      })
    })
  });

  map.addLayer(shapefileLayer);
</script>
