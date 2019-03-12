## Basic settings

Basic settings for the application include map options such as projection and extent.

### Page settings

With the pageSettings object you can define a footer and control the visibility of the map grid.

#### Example page settings definition

```json
"pageSettings": {
"footer": {
  "img": "img/png/logo.png",
  "url" : "https://github.com/origo-map/origo",
  "urlText": "Origo"
},
"mapGrid": {
  "visible": true
}
}
```

### footer

Name | Type | Description
---|---|---
`img` | string | URL or file path to an image.
`text` | string | Text to be displayed.
`url` | string | Sets the URL for a link.
`urlText` | string | The text to display for the link set in the url option.

### mapGrid

Name | Type | Description
---|---|---
`visible` | boolean | Sets the visibility of the map grid. Default is false.

### Map projection
The map projection is defined with the mandatory property projectionCode. If the projection is EPSG:3857 (Web mercator) or EPSG:4326 (WGS84) then the proj4Defs is optional, otherwise it is mandatory. An optional projection extent can also be set. Projections are handled with the proj4js library. The Proj4js definitions can be found on [epsg.io](http://epsg.io/).

#### Example projection definition

```json
{
"projectionCode": "EPSG:3010",
"proj4Defs": [
      {
          "code": "EPSG:3010",
          "alias": "urn:ogc:def:crs:EPSG::3010",
          "projection": "+proj=tmerc +lat_0=0 +lon_0=16.5 +k=1 +x_0=150000 +y_0=0 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs"
      }
],
"projectionExtent": [
  -1678505.1838360203,
  4665380,
  2431912.7361639794,
  8775797.92
]
}
```

### proj4Defs

Name | Type | Description
---|---|---
`proj4Defs` | array | The proj4 definitions for projections used in the map. Several projections can be definied but the projection set as projectionCode will be the map projection. Each projection is defined as an object. Visit [epsg.io](http://epsg.io/) to find proj4 definitions. EPSG:3857 (Web mercator) and EPSG:4326 (WGS84) doesn't need to be defined.

Name | Type | Description
---|---|---
`code` | string | The EPSG-name.
`alias` | string | An optional EPSG alias.
`projection` | string | The Proj4js definition for the projection.

### projectionCode

Name | Type | Description
---|---|---
`projectionCode` | string | The EPSG-name for the projection that will be used when the map is created. Visit [epsg.io](http://epsg.io/) to find the EPSG-code.

### projectionExtent

Name | Type | Description
---|---|---
`projectionExtent` | array | Extent that will be set for the projection.

### extent

Name | Type | Description
---|---|---
`extent` | array | Constraining extent for map layers.

### center

Name | Type | Description
---|---|---
`center` | array | The intial center coordinates for the map.

### zoom

Name | Type | Description
---|---|---
`zoom` | number | Initial zoom level for the map.

### resolutions

Name | Type | Description
---|---|---
`resolutions` | array | The resolutions used to define available zoom levels for the map. The resolutions should be valid for the base maps.

### enableRotation

Name | Type | Description
---|---|---
`enableRotation` | boolean | To be able to rotate the map or not. Default is true.

### groups

Name | Type | Description
---|---|---
`groups` | array | Define groups to organise layers. The group names are used in the legend control. Each group is defined as an object. A group can contain subgroups, defined as groups within a group.

Name | Type | Description
---|---|---
`name` | string | Name of the group that identifies the group. Each name must be unique.
`title` | string | A title for the group. The title is visible for the user in the legend control.
`abstract` | short description of the group. Adds a show info button to the layer in legend. Optional.
`expanded` | boolean | Whether the group should be expanded not. Used by the legend control. Default is false.
`groups` | array | Array of group objects defining subgroups. Optional.

### featureinfoOptions

Property | Type | Description
---|---|---
`clusterFeatureinfoLevel` | number | Zoom level where cluster layers will be identifiable. Default is 1.
`showOverlay` | boolean | Option to show featureinfo in overlay or sidebar. Default is true.
`pinning` | boolean | Option to enable/disable pinning. If enabled a pin will be placed where clicked in places with no identifiable features. Default is true.
`hitTolerance` | number | Option to set the hit tolerance in pixels. Features within this tolerance from a click will be considered. This makes it easier to click features on touch devices. Default is 0.
`selectionStyles` | object | Option to set custom selection style. Optional.

#### Example featureinfoOptions

```json
{
  "featureinfoOptions": {
    "clusterFeatureinfoLevel": 3,
    "showOverlay": false,
    "pinning": false,
    "hitTolerance": 3,
    "selectionStyles": {
      "Point": [{
        "circle": {
          "radius": 5,
          "stroke": {
            "color": [0, 153, 255, 1],
            "width": 0
          },
          "fill": {
            "color": [0, 153, 255, 1]
          }
        }
      }],
      "LineString": [{
        "stroke": {
          "color": [255, 255, 255, 1],
          "width": 5
        }
      },
      {
        "stroke": {
          "color": [0, 153, 255, 1],
          "width": 3
        }
      }],
      "Polygon": [{
        "stroke": {
          "color": [255, 255, 255, 1],
            "width": 5
          }
        },
        {
          "stroke": {
            "color": [0, 153, 255, 1],
            "width": 3
          }
        }
      ]
    }
  }
}
```

### clusterOptions
Can also be set on layer or source level.

Property | Type | Description
---|---|---
`clusterDistance` | number | The distance in pixels within which features will be clustered. Default is 60.
`clusterMaxZoom` | number | The zoom level where the features no longer will be clustered. Default is the last zoom level.

#### Example clusterOptions

```json
{
  "clusterOptions": {
    "clusterDistance" : 40,
    "clusterMaxZoom" : 2
  }
}
```

### tileGrid

Property | Type | Description
---|---|---
`alignBottomLeft` | boolean | Whether to align grid to top or bottom left corner. Default is true.
`tileSize` | array | Size of tiles in the tileGrid. Default is 256

#### Example tileGrid

```json
{
  "tileGrid": {
      "alignBottomLeft": false,
      "tileSize": 512
  }
}
```
