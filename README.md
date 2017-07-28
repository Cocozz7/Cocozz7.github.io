<!doctype html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="initial-scale=1,user-scalable=no,maximum-scale=1,width=device-width">
        <meta name="mobile-web-app-capable" content="yes">
        <meta name="apple-mobile-web-app-capable" content="yes">
        <link rel="stylesheet" href="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/css/leaflet.css" />
        <link rel="stylesheet" type="text/css" href="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/css/qgis2web.css">
        <link rel="stylesheet" href="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/css/MarkerCluster.css" />
        <link rel="stylesheet" href="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/css/MarkerCluster.Default.css" />
        <style>
        html, body, #map {
            width: 100%;
            height: 100%;
            padding: 0;
            margin: 0;
        }
        </style>
        <title></title>
    </head>
    <body>
        <div id="map">
        </div>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/qgis2web_expressions.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/leaflet.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/multi-style-layer.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/leaflet-heat.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/leaflet-svg-shape-markers.min.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/leaflet.rotatedMarker.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/OSMBuildings-Leaflet.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/leaflet-hash.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/leaflet-tilelayer-wmts.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/Autolinker.min.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/js/leaflet.markercluster.js"></script>
        <script src="https://drive.google.com/drive/folders/0B7MlZVCIp3mZUnZzZkVBQU02Z1E/data/Telenor4GAsky0.js"></script>
        <script>
        var highlightLayer;
        function highlightFeature(e) {
            highlightLayer = e.target;
            highlightLayer.openPopup();
        }
        L.ImageOverlay.include({
            getBounds: function () {
                return this._bounds;
            }
        });
        var map = L.map('map', {
            zoomControl:true, maxZoom:28, minZoom:1
        })
        var hash = new L.Hash(map);
        map.attributionControl.addAttribution('<a href="https://github.com/tomchadwin/qgis2web" target="_blank">qgis2web</a>');
        var bounds_group = new L.featureGroup([]);
        var basemap0 = L.tileLayer('http://{s}.www.toolserver.org/tiles/bw-mapnik/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>',
            maxZoom: 28
        });
        basemap0.addTo(map);
        function setBounds() {
            if (bounds_group.getLayers().length) {
                map.fitBounds(bounds_group.getBounds());
            }
        }
        function geoJson2heat(geojson, weight) {
          return geojson.features.map(function(feature) {
            return [
              feature.geometry.coordinates[1],
              feature.geometry.coordinates[0],
              feature.properties[weight]
            ];
          });
        }
        function pop_Telenor4GAsky0(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_Telenor4GAsky0_0(feature) {
            if (feature.properties['RSRP-mk1'] >= -200.000000 && feature.properties['RSRP-mk1'] <= -139.000000 ) {
                return {
                pane: 'pane_Telenor4GAsky0',
                radius: 3.0,
                stroke: false,
                fillOpacity: 1,
                fillColor: 'rgba(0,0,0,1.0)',
            }
            }
            if (feature.properties['RSRP-mk1'] >= -139.000000 && feature.properties['RSRP-mk1'] <= -100.000000 ) {
                return {
                pane: 'pane_Telenor4GAsky0',
                radius: 3.0,
                stroke: false,
                fillOpacity: 1,
                fillColor: 'rgba(255,0,0,1.0)',
            }
            }
            if (feature.properties['RSRP-mk1'] >= -100.000000 && feature.properties['RSRP-mk1'] <= -75.000000 ) {
                return {
                pane: 'pane_Telenor4GAsky0',
                radius: 3.0,
                stroke: false,
                fillOpacity: 1,
                fillColor: 'rgba(255,255,76,1.0)',
            }
            }
            if (feature.properties['RSRP-mk1'] >= -75.000000 && feature.properties['RSRP-mk1'] <= -50.000000 ) {
                return {
                pane: 'pane_Telenor4GAsky0',
                radius: 3.0,
                stroke: false,
                fillOpacity: 1,
                fillColor: 'rgba(76,240,155,1.0)',
            }
            }
        }
        map.createPane('pane_Telenor4GAsky0');
        map.getPane('pane_Telenor4GAsky0').style.zIndex = 400;
        map.getPane('pane_Telenor4GAsky0').style['mix-blend-mode'] = 'normal';
        var layer_Telenor4GAsky0 = new L.geoJson(json_Telenor4GAsky0, {
            attribution: '<a href=""></a>',
            pane: 'pane_Telenor4GAsky0',
            onEachFeature: pop_Telenor4GAsky0,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.circleMarker(latlng, style_Telenor4GAsky0_0(feature))
            },
        });
        bounds_group.addLayer(layer_Telenor4GAsky0);
        map.addLayer(layer_Telenor4GAsky0);
        var baseMaps = {};
        L.control.layers(baseMaps,{'Telenor 4G Askøy<br /><table><tr><td style="text-align: center;"><img src="legend/Telenor4GAsky0_Ingensignal0.png" /></td><td>Ingen signal</td></tr><tr><td style="text-align: center;"><img src="legend/Telenor4GAsky0_Svak1.png" /></td><td>Svak</td></tr><tr><td style="text-align: center;"><img src="legend/Telenor4GAsky0_Medium2.png" /></td><td>Medium</td></tr><tr><td style="text-align: center;"><img src="legend/Telenor4GAsky0_Sterk3.png" /></td><td>Sterk</td></tr></table>': layer_Telenor4GAsky0,},{collapsed:false}).addTo(map);
        setBounds();
        </script>
    </body>
</html>
