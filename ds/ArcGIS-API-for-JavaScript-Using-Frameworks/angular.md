<!-- .slide: data-background="./../common/slides/section.jpg" -->

## Angular

<img src="img/wayson/angular.png" class="transparent" height="250" />

----

## Angular

Angular helped put the 'E' in Enterprise JS frameworks

Very powerful...highly configurable

With great power comes great responsibility. 

<p style='height:20px;'></p>

https://github.com/Esri/angular-cli-esri-map

----

## Angular 

<span style="color: yellow">esri-loader</span> is easist approach.

<p>-------------------</p>

Angular 8 and 9 work with <span style="color: yellow">@arcgis/webpack-plugin</span>

<p class="fragment">Must be using webpack 🙄</p>
<p class="fragment">ArcGIS API 4.7+ only</p>
<p class="fragment">Configure webpack using builders</p>


----

### Angular with esri-loader

```js
import { loadModules } from 'esri-loader';


ngOnInit() {

  loadModules([
    "esri/Map",
    "esri/views/MapView"
  ]).then(([Map, MapView]) => {
    // Code to create the map and view will go here
  });
}
```

----

### Angular Builders

@angular-devkit/build-angular

Customize build config without ejecting webpack

```js
        // angular.json - custom configuration

        "build": {
          "builder": "@angular-builders/custom-webpack:browser",
          . . .

        "serve": {
          "builder": "@angular-builders/custom-webpack:dev-server",
          . . .        
```

----

### Angular Builders

```js
import Map from "esri/Map";
import MapView from "esri/views/MapView";

ngOnInit() {

  this._map = new Map({
    basemap: this._basemap 
  });

  this._view = new MapView({
    container: this.mapViewEl.nativeElement,
    map: this._map
  });
}

```

----

### Angular State Management

* Application state
* Component state
* Shared state
* Router state

### Oh so many choices...!

* RxJS + Redux (popular)
* NgRx
* NGXS
* angular-redux
* ?
