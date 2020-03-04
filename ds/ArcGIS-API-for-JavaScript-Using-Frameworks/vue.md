<!-- .slide: data-background="./../common/slides/section.jpg" -->

## Vue

<img alt="Vue" src="../common/images/vue-logo.png" class="transparent" height="250" />

----

### Can use the CLI

```sh
arcgis create geo-vue -t vue
```

----

### Can use vue-cli

* Requires a little config
* [Working user repo](https://github.com/crackernutter/arcgis-webpack-vue-calcite)

----

### Add a Map

```tsx
export default {
    name: 'WebMap',
    async mounted() {
        // Load the API modules
        const { default: WebMap } = await import('esri/WebMap');
        const { default: MapView } = await import('esri/views/MapView');
        const view = new MapView({
          map: new WebMap({ ... }),
          container: this.$el
        });
    }
};
```

----

### State Management

* [Vuex](https://vuex.vuejs.org/)

<img alt="Vuex" src="../common/images/vuex-flow.png" class="transparent" height="350" />

----

### State Management

* [XState](https://xstate.js.org/)

<img alt="XState" src="../common/images/xstate.png" class="transparent" height="350" />

----
<!-- .slide: data-background="./../common/slides/demo.jpg" -->

### Vue Demo

<a href="https://jsapi-map-vue.surge.sh/" target="_blank" rel="noopener">
  <img alt="Map Vue" src="../common/images/mapvue.png" class="transparent" height="500" />
</a>
