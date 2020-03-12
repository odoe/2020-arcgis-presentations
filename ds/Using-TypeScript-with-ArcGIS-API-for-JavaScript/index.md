<!-- .slide: data-background="../common/slides/intro.jpg" -->
<!-- .slide: class="title" -->

<h1 style="text-align: left; font-size: 80px;">Using TypeScript</h1>
<h2 style="text-align: left; font-size: 60px;">with ArcGIS API for JavaScript</h2>
<p style="text-align: left; font-size: 30px;">Noah Sager | René Rubalcava</p>
    <p style="text-align: left; font-size: 30px;">slides: <a href="https://git.io/JvVmE" target="_blank">https://git.io/JvVmE</a></p>

----
<!-- .slide: data-background="./../common/slides/section.jpg" -->

# Noah

<img src="../common/images/noah.jpg" alt="Where is Noah?">

----

### **Agenda**
</br>
 - What is TypeScript?
 - Why use TypeScript?
 - Setup and First steps
 - Live Action Demo
 - Where can I get more info?

----

### **What is TypeScript?**
<a href="https://www.typescriptlang.org/" target="_blank">
<img style="float:bottom;" src="../common/images/TypeScript_Superset_JavaScript.png" alt="TypeScript_Superset_JavaScript">
</a>

----

### **Where do I begin?**
<a href="https://www.typescriptlang.org/" target="_blank">
<img src="../common/images/ts.png" alt="TypeScript landing page" height="516">
</a>

----

### **Developer Setup**
<a href="https://developers.arcgis.com/javascript/latest/guide/typescript-setup/index.html" target="_blank">
<img style="float:bottom;" src="../common/images/Setup_TS.png" alt="Setup_TS" height="600">
</a>

----

### **Why use TypeScript?**
</br>
TypeScript adds **type** support to JavaScript
</br>
</br>
<img src="../common/images/TS_1a.png" alt="TypeScript_Example1">

----

### **Why use TypeScript?**
</br>
Enhanced IDE support
</br>
<img src="../common/images/TS_2.png" alt="TypeScript_Example2">

----

### **Why use TypeScript?**
</br>
Makes use of the latest JavaScript features - async/await
</br>
</br>
<img src="../common/images/promise_async_await_carbon4.png" alt="TypeScript_Example3">

----

### **Why use TypeScript?**
</br>
Makes use of the latest JavaScript features - dynamic module loading
</br>
</br>
<img src="../common/images/dynamicModule2.png" alt="TypeScript_Example4">

----

### **Why use TypeScript?**
</br>
Makes use of the latest JavaScript features - optional chaining
</br>
</br>
<img src="../common/images/optional-chaining.png" alt="TypeScript_Example5">

----

### **Why use TypeScript?**
</br>
Makes use of the latest JavaScript features - nullish coalescing
</br>
</br>
<img src="../common/images/nullish-coalescing.png" alt="TypeScript_Example6">

----
### **Why use TypeScript?**

> Types allow me to define where I start and where I want to go. It's about the journey of how I get from one to the other.
</br>

```ts
type Data = {
  coordinates: number[];
  placeName: string;
};

type Asset = {
  location: esri.Point;
  name: string;
};

type DataToAsset = (a: Data) => Asset;

```

----

### **Setup and First steps**

1. The recommended way to install TypeScript is via `node` and `npm`.

2. Make sure to install TypeScript globally: <br>
```bash
npm install -g typescript
```
3. Install the ArcGIS API for JavaScript Typings: <br>
```bash
npm install --save @types/arcgis-js-api
```

----

<!-- .slide: data-background="./../common/slides/section.jpg" -->

# Rene

<img src="../common/images/wheres_rene.png" alt="Where is Rene?">

----

## Tip!

* [ArcGIS API for JavaScript Snippets](https://marketplace.visualstudio.com/items?itemName=Esri.arcgis-jsapi-snippets)

----

## index.html

> Snippet shortcuts

* `!`
* `getApi`

```html
<body>
  <div id="viewDiv"></div>
  <script>
    require(["app/main"]);
  </script>
</body>
```

----

## tsconfig.json

```json
{
  "compilerOptions": {
    "lib": ["dom", "es2015.promise", "es5"],
    "module": "amd", // output files as AMD modules
    "sourceMap": true,
    "target": "es5",
    "noImplicitAny": true,
    "suppressImplicitAnyIndexErrors": true,
    "esModuleInterop": true
  }
}
```

----

### **Tip: Hide .js and .jsmap files **

- Reduce clutter
- VSCode: Add below to user preferences in files.exclude

```json
 "**/*.js.map": true,
        "**/*.js": {
            "when": "$(basename).ts"

```

----

### **Tip: Debugging with source maps**
  - Enable source maps in browser dev tools
  - Set breakpoints in .ts instead of .js

  <img alt="Vue" src="../common/images/transpiled.png" class="transparent" height="450" />

----

### **Tip: Use __esri instead of import**
- Only contains type interfaces
- Can use when not instantiating type

```ts
import esri = __esri;

const layerList = new LayerList({
  view,
  listItemCreatedFunction: event => {
    const item = event.item as esri.ListItem;
  }
});
```

----

### **Where can I get more info?**

- SDK Documentation
- Esri-related training and webinars
- ArcGIS Blogs
- GeoNet, StackExchange, Spatial Community in Slack, etc.</br>
</br>
<a href="https://www.esri.com/arcgis-blog/products/js-api-arcgis/mapping/using-typescript-with-the-arcgis-api-for-javascript/" target="_blank">
<img style="float:bottom;" src="../common/images/Using_TS_blog.png" alt="Using_TS_blog">

----

<!-- .slide: data-background="../common/slides/demo.jpg" -->

### **Demo: Build a TypeScript app from scratch**

----

<img src="../common/images/esri-science-logo-white.png" style="border: 0px; background:none; box-shadow: none;">
