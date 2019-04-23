# vue2-leaflet-geosearch

This is a [GeoSearch plugin](https://github.com/smeijer/leaflet-geosearch) extension for [vue2-leaflet package](https://github.com/KoRiGaN/Vue2Leaflet)

## Install
```sh
npm install --save vue2-leaflet-geosearch leaflet-geosearch
# or
yarn add vue2-leaflet-geosearch leaflet-geosearch
```
## Usage

Use something like this, where geosearchOptions is the [GeoSearch plugin Options](https://github.com/smeijer/leaflet-geosearch), Also dont forget to add the CSS file `  <link rel="stylesheet" href="https://unpkg.com/leaflet-geosearch@2.6.0/assets/css/leaflet.css">`

``` html
<v-map :zoom=3 :center="location">
  <v-tilelayer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></v-tilelayer>
  <!-- IMPORTANT PART HERE -->
  <v-geosearch :options="geosearchOptions" ></v-geosearch>
  <!-- /IMPORTANT PART HERE -->
</v-map>

<script>
import Vue from 'vue';
import Vue2Leaflet from 'vue2-leaflet';
import { OpenStreetMapProvider } from 'leaflet-geosearch';
import VGeosearch from 'vue2-leaflet-geosearch';

Vue.component('v-map', Vue2Leaflet.Map);
Vue.component('v-tilelayer', Vue2Leaflet.TileLayer);

export default {
  components: { VGeosearch },
  data() {
    return {
      geosearchOptions: { // Important part Here
        provider: new OpenStreetMapProvider(),
      },
    };
  },
};
</script>
```

# License

MIT

# Contribute

Of course :D
