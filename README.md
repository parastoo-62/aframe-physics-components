## aframe-physics-components

> Currently depends on aframe-core#dev

> Under development

Physics components for [A-Frame](https://aframe.io) VR using [cannon.js](http://schteppe.github.io/cannon.js/).

### Usage

#### Browser Installation

Install and use by directly including the [browser files](dist):

```html
<head>
  <title>My A-Frame Scene</title>
  <script src="https://aframe.io/releases/latest/aframe.min.js"></script>
  <script src="https://github.com/ngokevin/aframe-physics-components/blob/master/dist/aframe-physics-components.min.js"></script>
</head>

<body>
  <a-scene physics-world="gravity: 0 -9.8 0">
    <a-entity physics-body="boundingBox: 1 1 1; mass: 5; velocity: 0.2 0 0"
              geometry="primitive: box" material="color: red"></a-entity>
  </a-scene>
</body>
```

#### NPM Installation

Install via NPM:

```bash
npm install aframe-physics-component
```

Then register and use.

```js
var AFRAME = require('aframe-core');
var components = require('aframe-physics-components').components;

Object.keys(components).forEach(function (componentName) {
  AFRAME.registerComponent(componentName, components[componentName]);
});
```

### API

#### physics-body Component

| Property        | Description           | Type   | Default Value |
| --------        | -----------           | ----   | ------------- |
| angularVelocity | (in deg/s)            | vec3   | 0 0 0         |
| boundingBox     | Collision box (in m). | vec3   | 0 0 0         |
| mass            | (in kg)               | number | 1             |
| velocity        | (in m/s)              | vec3   | 0 0 0         |

##### applyImpulse (impulseVec3, positionVec3)

Applies an impulse (indicated by `impulseVec3`) at the body's local point
(indicated by `positionVec3`). `forceVec3` is in Force / Time (Newtons /
Seconds).

```
// Applies a small force from left-to-right to the top-left of the body.
var hitMeBody = document.querySelector('#hit-me-entity').components['physics-body'];
hitMeBody.applyImpulse({ x: 10, y: 0, z: 0 }, { x: -1, y: 1, z: 0 });
```

#### physics-world Component

| Property | Description | Default Value |
| -------- | ----------- | ------------- |
| gravity  | vec3        | 0 -9.8 0      |