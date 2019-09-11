react-globe.gl
==============

[![NPM package][npm-img]][npm-url]
[![Build Size][build-size-img]][build-size-url]
[![Dependencies][dependencies-img]][dependencies-url]

React bindings for the [globe.gl](https://github.com/vasturiano/globe.gl) UI component.

<p align="center">
   <a href="//vasturiano.github.io/react-globe.gl/example/world-population/"><img width="48%" src="https://vasturiano.github.io/react-globe.gl/example/world-population/preview.png"></a>
   <a href="//vasturiano.github.io/react-globe.gl/example/airline-routes/us-international-outbound.html"><img width="48%" src="https://vasturiano.github.io/react-globe.gl/example/airline-routes/preview.png"></a>
   <a href="//vasturiano.github.io/react-globe.gl/example/countries-population/"><img width="48%" src="https://vasturiano.github.io/react-globe.gl/example/countries-population/preview.png"></a>
   <a href="//vasturiano.github.io/react-globe.gl/example/volcanoes/"><img width="48%" src="https://vasturiano.github.io/react-globe.gl/example/volcanoes/preview.png"></a>
</p>

A React component to represent data visualization layers on a 3-dimensional globe in a spherical projection, using [ThreeJS](https://github.com/mrdoob/three.js/)/WebGL for 3D rendering.

Check out the examples:
* [Basic](https://vasturiano.github.io/react-globe.gl/example/basic/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/basic/index.html))
* [Arc Links](https://vasturiano.github.io/react-globe.gl/example/random-arcs/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/random-arcs/index.html))
* [Highlight links](https://vasturiano.github.io/react-globe.gl/example/airline-routes/highlight-links.html) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/airline-routes/highlight-links.html))
* [Choropleth](https://vasturiano.github.io/react-globe.gl/example/choropleth-countries/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/choropleth-countries/index.html))
* [Elevated Polygons](https://vasturiano.github.io/react-globe.gl/example/countries-population/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/countries-population/index.html))
* [Map Labels](https://vasturiano.github.io/react-globe.gl/example/world-cities/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/world-cities/index.html))
* [Custom Layer](https://vasturiano.github.io/react-globe.gl/example/custom-layer/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/custom-layer/index.html))
* [World Population](https://vasturiano.github.io/react-globe.gl/example/world-population/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/world-population/index.html))
* [Recent Earthquakes](https://vasturiano.github.io/react-globe.gl/example/earthquakes/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/earthquakes/index.html))
* [World Volcanoes](https://vasturiano.github.io/react-globe.gl/example/volcanoes/) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/volcanoes/index.html))
* [US outbound international airline routes](https://vasturiano.github.io/react-globe.gl/example/airline-routes/us-international-outbound.html) ([source](https://github.com/vasturiano/react-globe.gl/blob/master/example/airline-routes/us-international-outbound.html))

## Quick start

```
import Globe from 'react-globe.gl';
```

or using a script tag

```
<script src="//unpkg.com/react-globe.gl"></script>
```

then

```
ReactDOM.render(
  <Globe
    pointsData={myData}
  />, 
  myDOMElement
);
```

## API reference

### Container layout

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>width</b> | <i>number</i> | *&lt;window width&gt;* | Getter/setter for the canvas width. |
| <b>height</b> | <i>number</i> | *&lt;window height&gt;* | Getter/setter for the canvas height. |
| <b>backgroundColor</b> | <i>string</i> | `#000011` | Getter/setter for the background color. |
| <b>animateIn</b> | <i>bool</i> | `true` | Whether to animate the globe initialization, by scaling and rotating the globe into its inital position. This prop only has an effect on component mount. |

### Globe Layer

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>globeImageUrl</b> | <i>string</i>| *-* |Getter/setter for the URL of the image used in the material that wraps the globe. If no image is provided, the globe is represented as a black sphere. |
| <b>bumpImageUrl</b> | <i>string</i>| *-* |Getter/setter for the URL of the image used to create a [bump map](https://threejs.org/docs/#api/en/materials/MeshStandardMaterial.bumpMap) in the material, to represent the globe's terrain. |
| <b>showAtmosphere</b> | <i>bool</i> | `true` | Getter/setter for whether to show a bright halo surrounding the globe, representing the atmosphere. |
| <b>showGraticules</b> | <i>bool</i> | `false` | Getter/setter for whether to show a graticule grid demarking latitude and longitude lines at every 10 degrees. |

### Points Layer

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>pointsData</b> | <i>array</i> | `[]` | Getter/setter for the list of points to represent in the points map layer. Each point is displayed as a cylindrical 3D object rising perpendicularly from the surface of the globe. |
| <b>pointLabel</b> | <i>string</i> or <i>func</i> | `name` | Point object accessor function or attribute for label (shown as tooltip). Supports plain text or HTML content. |
| <b>pointLat</b> | <i>number</i>, <i>string</i> or <i>func</i> | `lat` | Point object accessor function, attribute or a numeric constant for the cylinder's center latitude coordinate. |
| <b>pointLng</b> | <i>number</i>, <i>string</i> or <i>func</i> | `lng` | Point object accessor function, attribute or a numeric constant for the cylinder's center longitude coordinate. |
| <b>pointColor</b> | <i>string</i> or <i>func</i> | `() => '#ffffaa'` | Point object accessor function or attribute for the cylinder color. |
| <b>pointAltitude</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0.1 | Point object accessor function, attribute or a numeric constant for the cylinder's altitude in terms of globe radius units (`0` = 0 altitude (flat circle), `1` = globe radius). |
| <b>pointRadius</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0.25 | Point object accessor function, attribute or a numeric constant for the cylinder's radius, in angular degrees. |
| <b>pointResolution</b> | <i>number</i> | 12 | Getter/setter for the radial geometric resolution of each cylinder, expressed in how many slice segments to divide the circumference. Higher values yield smoother cylinders. |
| <b>pointsMerge</b> | <i>bool</i> | `false` | Getter/setter for whether to merge all the point meshes into a single ThreeJS object, for improved rendering performance. Visually both options are equivalent, setting this option only affects the internal organization of the ThreeJS objects. |
| <b>pointsTransitionDuration</b> | <i>number</i> | 1000 | Getter/setter for duration (ms) of the transition to animate point changes involving geometry modifications. A value of `0` will move the objects immediately to their final position. New objects are animated by scaling them from the ground up. Only works if `pointsMerge` is disabled. |
| <b>onPointClick</b> | <i>func</i>| *-* |Callback function for point (left-button) clicks. The point object is included as single argument: `onPointClick(point)`. Only works if `pointsMerge` is disabled. |
| <b>onPointRightClick</b> | <i>func</i>| *-* |Callback function for point right-clicks. The point object is included as single argument: `onPointRightClick(point)`. Only works if `pointsMerge` is disabled. |
| <b>onPointHover</b> | <i>func</i>| *-* |Callback function for point mouse over events. The point object (or `null` if there's no point under the mouse line of sight) is included as the first argument, and the previous point object (or `null`) as second argument: `onPointHover(point, prevPoint)`. Only works if `pointsMerge` is disabled. |

### Arcs Layer

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>arcsData</b> | <i>array</i> | `[]` | Getter/setter for the list of links to represent in the arcs map layer. Each link is displayed as an arc line that rises from the surface of the globe, connecting the start and end coordinates. |
| <b>arcLabel</b> | <i>string</i> or <i>func</i> | `name` | Arc object accessor function or attribute for label (shown as tooltip). Supports plain text or HTML content. |
| <b>arcStartLat</b> | <i>number</i>, <i>string</i> or <i>func</i> | `startLat` | Arc object accessor function, attribute or a numeric constant for the line's start latitude coordinate. |
| <b>arcStartLng</b> | <i>number</i>, <i>string</i> or <i>func</i> | `startLng` | Arc object accessor function, attribute or a numeric constant for the line's start longitude coordinate. |
| <b>arcEndLat</b> | <i>number</i>, <i>string</i> or <i>func</i> | `endLat` | Arc object accessor function, attribute or a numeric constant for the line's end latitude coordinate. |
| <b>arcEndLng</b> | <i>number</i>, <i>string</i> or <i>func</i> | `endLng` | Arc object accessor function, attribute or a numeric constant for the line's end longitude coordinate. |
| <b>arcColor</b> | <i>string</i>, <i>[string, ...]</i> or <i>func</i> | `() => '#ffffaa'` | Arc object accessor function or attribute for the line's color. Also supports color gradients by passing an array of colors. |
| <b>arcAltitude</b> | <i>number</i>, <i>string</i> or <i>func</i>| `null` |Arc object accessor function, attribute or a numeric constant for the arc's maximum altitude (ocurring at the half-way distance between the two points) in terms of globe radius units (`0` = 0 altitude (ground line), `1` = globe radius). If a value of `null` or `undefined` is used, the altitude is automatically set proportionally to the distance between the two points, according to the scale set in `arcAltitudeAutoScale`. |
| <b>arcAltitudeAutoScale</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0.5 | Arc object accessor function, attribute or a numeric constant for the scale of the arc's automatic altitude, in terms of units of the great-arc distance between the two points. A value of `1` indicates the arc should be as high as its length on the ground. Only applicable if `arcAltitude` is not set. |
| <b>arcStroke</b> | <i>number</i>, <i>string</i> or <i>func</i>| `null` |Arc object accessor function, attribute or a numeric constant for the line's diameter, in angular degrees. A value of `null` or `undefined` will render a [ThreeJS Line](https://threejs.org/docs/#api/objects/Line) whose width is constant (`1px`) regardless of the camera distance. Otherwise, a [TubeGeometry](https://threejs.org/docs/#api/en/geometries/TubeGeometry) is used. |
| <b>arcCurveResolution</b> | <i>number</i> | 64 | Getter/setter for the arc's curve resolution, expressed in how many straight line segments to divide the curve by. Higher values yield smoother curves. |
| <b>arcCircularResolution</b> | <i>number</i> | 6 | Getter/setter for the radial geometric resolution of each line, expressed in how many slice segments to divide the tube's circumference. Only applicable when using Tube geometries (defined `arcStroke`). |
| <b>arcDashLength</b> | <i>number</i>, <i>string</i> or <i>func</i> | 1 | Arc object accessor function, attribute or a numeric constant for the length of the dashed segments in the arc, in terms of relative length of the whole line (`1` = full line length). |
| <b>arcDashGap</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0 | Arc object accessor function, attribute or a numeric constant for the length of the gap between dash segments, in terms of relative line length. |
| <b>arcDashInitialGap</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0 | Arc object accessor function, attribute or a numeric constant for the length of the initial gap before the first dash segment, in terms of relative line length. |
| <b>arcDashAnimateTime</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0 | Arc object accessor function, attribute or a numeric constant for the time duration (in `ms`) to animate the motion of dash positions from the start to the end point for a full line length. A value of `0` disables the animation. |
| <b>arcsTransitionDuration</b> | <i>number</i> | 1000 | Getter/setter for duration (ms) of the transition to animate arc changes involving geometry modifications. A value of `0` will move the arcs immediately to their final position. New arcs are animated by rising them from the ground up. |
| <b>onArcClick</b> | <i>func</i>| *-* |Callback function for arc (left-button) clicks. The arc object is included as single argument: `onArcClick(arc)`. |
| <b>onArcRightClick</b> | <i>func</i>| *-* |Callback function for arc right-clicks. The arc object is included as single argument: `onArcRightClick(arc)`. |
| <b>onArcHover</b> | <i>func</i>| *-* |Callback function for arc mouse over events. The arc object (or `null` if there's no arc under the mouse line of sight) is included as the first argument, and the previous arc object (or `null`) as second argument: `onArcHover(arc, prevArc)`. |

### Polygons Layer

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>polygonsData</b> | <i>array</i> | `[]` | Getter/setter for the list of polygon shapes to represent in the polygons map layer. Each polygon is displayed as a shaped cone that extrudes from the surface of the globe. |
| <b>polygonLabel</b> | <i>string</i> or <i>func</i> | `name` | Polygon object accessor function or attribute for label (shown as tooltip). Supports plain text or HTML content. |
| <b>polygonGeoJsonGeometry</b> | <i>string</i> or <i>func</i> | `geometry` | Polygon object accessor function or attribute for the GeoJson geometry specification of the polygon's shape. The returned value should have a minimum of two fields: `type` and `coordinates`. Only GeoJson geometries of type `Polygon` or `MultiPolygon` are supported, other types will be skipped. |
| <b>polygonCapColor</b> | <i>string</i> or <i>func</i> | `() => '#ffffaa'` | Polygon object accessor function or attribute for the color of the top surface. |
| <b>polygonSideColor</b> | <i>string</i> or <i>func</i> | `() => '#ffffaa'` | Polygon object accessor function or attribute for the color of the cone sides. |
| <b>polygonAltitude</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0.1 | Polygon object accessor function, attribute or a numeric constant for the polygon cone's altitude in terms of globe radius units (`0` = 0 altitude (flat polygon), `1` = globe radius). |
| <b>polygonsTransitionDuration</b> | <i>number</i> | 1000 | Getter/setter for duration (ms) of the transition to animate polygon altitude changes. A value of `0` will size the cone immediately to their final altitude. New polygons are animated by rising them from the ground up. |
| <b>onPolygonClick</b> | <i>func</i>| *-* |Callback function for polygon (left-button) clicks. The polygon object is included as single argument: `onPolygonClick(polygon)`. |
| <b>onPolygonRightClick</b> | <i>func</i>| *-* |Callback function for polygon right-clicks. The polygon object is included as single argument: `onPolygonRightClick(polygon)`. |
| <b>onPolygonHover</b> | <i>func</i>| *-* |Callback function for polygon mouse over events. The polygon object (or `null` if there's no polygon under the mouse line of sight) is included as the first argument, and the previous polygon object (or `null`) as second argument: `onPolygonHover(polygon, prevPolygon)`. |

### Hex Bin Layer

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>hexBinPointsData</b> | <i>array</i> | `[]` | Getter/setter for the list of points to aggregate using the hex bin map layer. Each point is added to an hexagonal prism 3D object that represents all the points within a tesselated portion of the space. |
| <b>hexLabel</b> | <i>string</i> or <i>func</i>| *-* |Hex object accessor function or attribute for label (shown as tooltip). An hex object includes all points binned, and has the syntax: `{ points, sumWeight, center: { lat, lng } }`. Supports plain text or HTML content. |
| <b>hexBinPointLat</b> | <i>number</i>, <i>string</i> or <i>func</i> | `lat` | Point object accessor function, attribute or a numeric constant for the latitude coordinate. |
| <b>hexBinPointLng</b> | <i>number</i>, <i>string</i> or <i>func</i> | `lng` | Point object accessor function, attribute or a numeric constant for the longitude coordinate. |
| <b>hexBinPointWeight</b> | <i>number</i>, <i>string</i> or <i>func</i> | 1 | Point object accessor function, attribute or a numeric constant for the weight of the point. Weights for points in the same bin are summed and determine the hexagon default altitude. |
| <b>hexBinResolution</b> | <i>number</i> | 4 | The geographic binning resolution as defined by [H3](https://uber.github.io/h3/#/documentation/core-library/resolution-table). Determines the area of the hexagons that tesselate the globe's surface. Accepts values between `0` and `15`. Level 0 partitions the earth in 122 (mostly) hexagonal cells. Each subsequent level sub-divides the previous in roughly 7 hexagons. |
| <b>hexMargin</b> | <i>number</i> or <i>func</i> | 0.2 | The radial margin of each hexagon. Margins above `0` will create gaps between adjacent hexagons and serve only a visual purpose, as the data points within the margin still contribute to the hexagon's data. The margin is specified in terms of fraction of the hexagon's surface diameter. Values below `0` or above `1` are disadvised. This property also supports using an accessor method based on the hexagon's aggregated data, following the syntax: `hexMargin(({ points, sumWeight, center: { lat, lng }}) => ...)`. This method should return a numeric constant. |
| <b>hexAltitude</b> | <i>number</i> or <i>func</i> | `({ sumWeight }) => sumWeight * 0.01` | The altitude of each hexagon, in terms of globe radius units (`0` = 0 altitude (flat hexagon), `1` = globe radius). This property also supports using an accessor method based on the hexagon's aggregated data, following the syntax: `hexAltitude(({ points, sumWeight, center: { lat, lng }}) => ...)`. This method should return a numeric constant. |
| <b>hexTopColor</b> | <i>func</i> | `() => '#ffffaa'` | Accessor method for each hexagon's top color. The method should follow the signature: `hexTopColor(({ points, sumWeight, center: { lat, lng }}) => ...)` and return a color string. |
| <b>hexSideColor</b> | <i>func</i> | `() => '#ffffaa'` | Accessor method for each hexagon's side color. The method should follow the signature: `hexSideColor(({ points, sumWeight, center: { lat, lng }}) => ...)` and return a color string. |
| <b>hexBinMerge</b> | <i>bool</i> | `false` | Getter/setter for whether to merge all the hexagon meshes into a single ThreeJS object, for improved rendering performance. Visually both options are equivalent, setting this option only affects the internal organization of the ThreeJS objects. |
| <b>hexTransitionDuration</b> | <i>number</i> | 1000 | Getter/setter for duration (ms) of the transition to animate hexagon changes related to geometry modifications (altitude, radius). A value of `0` will move the hexagons immediately to their final position. New hexagons are animated by scaling them from the ground up. Only works if `hexBinMerge` is disabled. |
| <b>onHexClick</b> | <i>func</i>| *-* |Callback function for hexagon (left-button) clicks. The hex object including all points binned is included as single argument: `onHexClick({ points, sumWeight, center: { lat, lng } })`. Only works if `hexBinMerge` is disabled. |
| <b>onHexRightClick</b> | <i>func</i>| *-* |Callback function for hexagon right-clicks. The hex object including all points binned is included as single argument: `onHexRightClick({ points, sumWeight, center: { lat, lng } })`. Only works if `hexBinMerge` is disabled. |
| <b>onHexHover</b> | <i>func</i>| *-* |Callback function for hexagon mouse over events. The hex object (or `null` if there's no hex under the mouse line of sight) is included as the first argument, and the previous hex object (or `null`) as second argument: `onHexHover(hex, prevHex)`. Each hex object includes all points binned, and has the syntax: `{ points, sumWeight, center: { lat, lng } }`. Only works if `hexBinMerge` is disabled. |

### Labels Layer

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>labelsData</b> | <i>array</i> | `[]` | Getter/setter for the list of label objects to represent in the labels map layer. |
| <b>labelLabel</b> | <i>string</i> or <i>func</i>| *-* |Label object accessor function or attribute for its own tooltip label. Supports plain text or HTML content. |
| <b>labelLat</b> | <i>number</i>, <i>string</i> or <i>func</i> | `lat` | Label object accessor function, attribute or a numeric constant for the latitude coordinate. |
| <b>labelLng</b> | <i>number</i>, <i>string</i> or <i>func</i> | `lng` | Label object accessor function, attribute or a numeric constant for the longitude coordinate. |
| <b>labelText</b> | <i>string</i> or <i>func</i> | `text` | Label object accessor function or attribute for the label text. |
| <b>labelColor</b> | <i>string</i> or <i>func</i> | `() => 'lightgrey'` | Label object accessor function or attribute for the label color. |
| <b>labelAltitude</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0 | Label object accessor function, attribute or a numeric constant for the label altitude in terms of globe radius units. |
| <b>labelSize</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0.5 | Label object accessor function, attribute or a numeric constant for the label text height, in angular degrees. |
| <b>labelTypeFace</b> | <i>typeface object </i> | [helvetiker regular](https://github.com/mrdoob/three.js/blob/dev/examples/fonts/helvetiker_regular.typeface.json) | Getter/setter for the text font typeface JSON object. Supports any typeface font generated by [Facetype.js](http://gero3.github.io/facetype.js/). |
| <b>labelRotation</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0 | Label object accessor function, attribute or a numeric constant for the label rotation in degrees. The rotation is performed clockwise along the axis of its latitude parallel plane. |
| <b>labelResolution</b> | <i>number</i> | 3 | Getter/setter for the text geometric resolution of each label, expressed in how many segments to use in the text curves. Higher values yield smoother labels. |
| <b>labelIncludeDot</b> | <i>bool</i>, <i>string</i> or <i>func</i> | `true` | Label object accessor function, attribute or a bool constant for whether to include a dot marker next to the text indicating the exact `lat`, `lng` coordinates of the label. If enabled the text will be rendered offset from the dot. |
| <b>labelDotRadius</b> | <i>number</i>, <i>string</i> or <i>func</i> | 0.1 | Label object accessor function, attribute or a numeric constant for the radius of the dot marker, in angular degrees. |
| <b>labelDotOrientation</b> | <i>string</i> or <i>func</i> | `() => 'bottom'` | Label object accessor function or attribute for the orientation of the label if the dot marker is present. Possible values are `right`, `top` and `bottom`. |
| <b>labelsTransitionDuration</b> | <i>number</i> | 1000 | Getter/setter for duration (ms) of the transition to animate label changes involving position modifications (`lat`, `lng`, `altitude`, `rotation`). A value of `0` will move the labels immediately to their final position. New labels are animated by scaling their size. |
| <b>onLabelClick</b> | <i>func</i>| *-* |Callback function for label (left-button) clicks. The label object is included as single argument: `onlabelClick(label)`. |
| <b>onLabelRightClick</b> | <i>func</i>| *-* |Callback function for label right-clicks. The label object is included as single argument: `onlabelRightClick(label)`. |
| <b>onLabelHover</b> | <i>func</i>| *-* |Callback function for label mouse over events. The label object (or `null` if there's no label under the mouse line of sight) is included as the first argument, and the previous label object (or `null`) as second argument: `onlabelHover(label, prevlabel)`. |

### Custom Layer

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>customLayerData</b> | <i>array</i> | `[]` | Getter/setter for the list of items to represent in the custom map layer. Each item is rendered according to the `customThreeObject` method. |
| <b>customLayerLabel</b> | <i>string</i> or <i>func</i> | `name` | Object accessor function or attribute for label (shown as tooltip). Supports plain text or HTML content. |
| <b>customThreeObject</b> | <i>Object3d</i>, <i>string</i> or <i>func</i>| *-* |Object accessor function or attribute for generating a custom 3d object to render as part of the custom map layer. Should return an instance of [ThreeJS Object3d](https://threejs.org/docs/index.html#api/core/Object3D). The callback method's signature includes the object's data as well as the globe radius: `customThreeObject((objData, globeRadius) => { ... })`. |
| <b>customThreeObjectUpdate</b> | <i>string</i> or <i>func</i>| *-* |Object accessor function or attribute for updating an existing custom 3d object with new data. This can be used for performance improvement on data updates as the objects don't need to be removed and recreated at each update. The callback method's signature includes the object to be update, its new data and the globe radius: `customThreeObjectUpdate((obj, objData, globeRadius) => { ... })`. |
| <b>onCustomLayerClick</b> | <i>func</i>| *-* |Callback function for custom object (left-button) clicks. The custom object is included as single argument: `onCustomLayerClick(obj)`. |
| <b>onCustomLayerRightClick</b> | <i>func</i>| *-* |Callback function for custom object right-clicks. The custom object is included as single argument: `onCustomLayerRightClick(obj)`. |
| <b>onCustomLayerHover</b> | <i>func</i>| *-* |Callback function for custom object mouse over events. The custom object (or `null` if there's no object under the mouse line of sight) is included as the first argument, and the previous custom object (or `null`) as second argument: `onCustomLayerHover(obj, prevObj)`. |

### Render control

| Prop | Type | Default | Description |
| --- | :--: | :--: | --- |
| <b>rendererConfig</b> | <i>object</i> | `{ antialias: true, alpha: true }` | Configuration parameters to pass to the [ThreeJS WebGLRenderer](https://threejs.org/docs/#api/en/renderers/WebGLRenderer) constructor. This prop only has an effect on component mount. |
| <b>enablePointerInteraction</b> | <i>bool</i> | `true` | Getter/setter for whether to enable the mouse tracking events. This activates an internal tracker of the canvas mouse position and enables the functionality of object hover/click and tooltip labels, at the cost of performance. If you're looking for maximum gain in your globe performance it's recommended to switch off this property. |

| Method | Arguments | Description |
| --- | :--: | --- |
| <b>pointOfView</b> | { <i>lat</i>, <i>lng</i>, <i>altitude</i> } [,<i>ms</i>=`0`] | By default the camera will aim at the cross between the equator and the prime meridian (`0,0` coordinates), at an altitude of `2.5` globe radii. | Getter/setter for the camera position, in terms of geographical `lat`, `lng`, `altitude` coordinates. Each of the coordinates is optional, allowing for motion in just some direction. The 2nd optional argument defines the duration of the transition (in ms) to animate the camera motion. A value of 0 (default) moves the camera immediately to the final position. |
| <b>pauseAnimation</b>| *-* |Pauses the rendering cycle of the component, effectively freezing the current view and cancelling all user interaction. This method can be used to save performance in circumstances when a static image is sufficient. |
| <b>resumeAnimation</b>| *-* |Resumes the rendering cycle of the component, and re-enables the user interaction. This method can be used together with `pauseAnimation` for performance optimization purposes. |
| <b>scene</b>| *-* |Access the internal ThreeJS [Scene](https://threejs.org/docs/#api/scenes/Scene). Can be used to extend the current scene with additional objects not related to globe.gl. |
| <b>camera</b>| *-* |Access the internal ThreeJS [Camera](https://threejs.org/docs/#api/cameras/PerspectiveCamera). |
| <b>renderer</b>| *-* |Access the internal ThreeJS [WebGL renderer](https://threejs.org/docs/#api/renderers/WebGLRenderer). |
| <b>controls</b>| *-* |Access the internal ThreeJS [orbit controls object](https://threejs.org/docs/#examples/controls/OrbitControls). |

### Utility

| Method | Arguments | Description |
| --- | :--: | --- |
| <b>getCoords</b> | <i>lat</i>, <i>lng</i> [,<i>altitude</i>=`0`] | Utility method to translate spherical coordinates. Given a pair of latitude/longitude coordinates and optionally altitude (in terms of globe radius units), returns the equivalent `{x, y, z}` cartesian spatial coordinates. |
| <b>toGeoCoords</b> | { <i>x</i>, <i>y</i>, <i>z</i> } | Utility method to translate cartesian coordinates to the geographic domain. Given a set of 3D cartesian coordinates `{x, y, z}`, returns the equivalent `{lat, lng, altitude}` spherical coordinates. Altitude is defined in terms of globe radius units. |

## Giving Back

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=L398E7PKP47E8&currency_code=USD&source=url) If this project has helped you and you'd like to contribute back, you can always [buy me a ☕](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=L398E7PKP47E8&currency_code=USD&source=url)!

[npm-img]: https://img.shields.io/npm/v/react-globe.gl.svg
[npm-url]: https://npmjs.org/package/react-globe.gl
[build-size-img]: https://img.shields.io/bundlephobia/minzip/react-globe.gl.svg
[build-size-url]: https://bundlephobia.com/result?p=react-globe.gl
[dependencies-img]: https://img.shields.io/david/vasturiano/react-globe.gl.svg
[dependencies-url]: https://david-dm.org/vasturiano/react-globe.gl