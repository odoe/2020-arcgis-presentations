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
<p class="fragment">angular-builders/custom-webpack</p>


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

### Angular with @arcgis/webpack-plugin

@angular-devkit/build-angular

Customize build config without ejecting webpack

```js
        // angular.json - custom configuration

        "build": {
          "builder": "@angular-builders/custom-webpack:browser",
          "options": {
            "customWebpackConfig": {
              "path": "./extra-webpack.config.js"
            },              
          . . .

        "serve": {
          "builder": "@angular-builders/custom-webpack:dev-server",
          "options": {
            "browserTarget": "angular-cli-esri-map:build"
          },          
          . . .        
```

----

### extra-webpack.config.js

```js
const ArcGISPlugin = require('@arcgis/webpack-plugin');
/**
 * Configuration items defined here will be appended to the end of the existing webpack config defined by the Angular CLI.
*/
module.exports = {
  plugins: [new ArcGISPlugin()],
  node: {
    process: false,
    global: false,
    fs: "empty"
  },
  devtool: 'eval'
}
```
----

### Angular with @arcgis/webpack-plugin

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

* RxJS
* RxJS + Redux
* NgRx
* NGXS
* angular-redux
* ?

----

### Example RxJS service

https://github.com/andygup/angular-plus-arcgis-javascript-ds2020

```js
import { Injectable } from '@angular/core';
import {MapStore} from '../map-store.class';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class MapStateService extends MapStore<any[]> {

  getPoints(): Observable<__esri.Graphic[]> {
    return this.getState();
  }

  addPoint(point: __esri.Graphic) {
    const c = this.getValue();

    if(typeof c !== 'undefined'){
      this.setState([...this.getValue(), point]);  
    }
    else {
      this.setState([point]);  
    }

  }
  constructor() { 
    // Important ;-) MapStore needs an initial value of any empty []
    super([]);
  }
}

```

----

### Example service subscriber

https://github.com/andygup/angular-plus-arcgis-javascript-ds2020

```js
  ngOnInit() {
    // deactivate change detection component and children
    this.changeDetect.detach();     
    this.points$ = this.msService.getPoints();
    this.list = this.points$.subscribe({
      next: x => { 
        let finalValue: any[];
        if (x.length) {
          finalValue = x.map((val:any) => {
            return val.geometry.latitude + ", " + val.geometry.longitude;
          });
        }
        this.pMessage = finalValue;
        this.changeDetect.detectChanges();
      },
      error: err => console.error('error in subscriber', err),
      complete: () => console.log('complete')
    })
  }
```