<!-- .slide: data-background="./../common/slides/section.jpg" -->

# Tom

----
<!-- .slide: data-background="./../common/slides/section.jpg" -->

## Ember

<img src="img/wayson/tomster-sm.png" width="240" class="transparent" />

https://emberjs.com/

----

<iframe src="https://developers.arcgis.com/javascript/latest/guide/ember/#create-a-component" style="width: 600px; height:  600px"></iframe>

[Using the ArcGIS API for JavaScript with Ember](https://developers.arcgis.com/javascript/latest/guide/ember)

----

<!-- .slide: data-transition="fade" -->
### [ember-cli-amd](https://github.com/Esri/ember-cli-amd)
<p>😎 `import Map from 'esri/Map'` 👍</p>
<p>👵 works ArcGIS API 3.x! 👴</p>
<p>... but</p>
<p class="fragment">📵 can **not** lazy-load the ArcGIS API 😦</p>

----

<!-- .slide: data-transition="fade" -->
### [ember-esri-loader](https://github.com/Esri/ember-esri-loader) 

<p>📱 lazy-load the ArcGIS API 👍</p>
<div style="position: relative; width: 240px; margin: 0 auto;">
  <img src="img/wayson/tomster-sm.png" width="240" class="transparent" />
  <img src="img/wayson/esri-loader-band-aid-center-text.png" class="transparent" style="position: absolute;top: 100px;left: 0;width: 240px;height: auto;transform: rotate(-20deg);" />
</div>
----

### [Ember Octane](https://emberjs.com/editions/octane/)

<a href="https://emberjs.com/editions/octane/"><img src="img/wayson/octane.png" height="400" class="transparent" /></a>

----

<!-- .slide: data-transition="fade" -->
### [Element Modifiers](https://guides.emberjs.com/release/components/template-lifecycle-dom-and-modifiers/#toc_calling-methods-on-first-render)

```html
<div style="height: 400px;" {{did-insert this.loadMap}}></div>
```

```js
import Component from "@glimmer/component";
import { loadWebMap } from '../utils/map';

export default class EsriMap extends Component {
  loadMap(element) {
    loadWebMap(element, 'f2e9b762544945f390ca4ac3671cfa72');
  }
}
```
<!-- .element class="fragment" -->

----

<!-- .slide: data-transition="fade" -->
### [Custom Modifiers](https://github.com/ember-modifier/ember-modifier)

```html
<div style="height: 400px;" {{webmap @id}}></div>
```

```js
// app/modifiers/webmap.js
import { modifier } from 'ember-modifier';
import { loadWebMap } from '../utils/map';

export default modifier((element, [id]) => {
  const view = loadWebMap(element, id);
  return function cleanUp () {
    view && view.container = null;
  };
});
```
<!-- .element class="fragment" -->
