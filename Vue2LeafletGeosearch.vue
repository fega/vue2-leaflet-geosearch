<template>
  <div>

  </div>
</template>

<script>
// import L from 'leaflet';
import { GeoSearchControl } from 'leaflet-geosearch';


export default {
  props: {
    options: {
      required: true,
    },
  },
  name: 'v-geosearch',
  data() {
    return {
      control: null
    }
  },
  mounted() {
    this.add();
  },
  beforeDestroy() {
    this.remove();
  },
  methods: {
    deferredMountedTo(parent) {
      const searchControl = new GeoSearchControl(this.options);
      parent.addControl(searchControl);
      this.control = searchControl;
    },
    remove() {
      this.$parent.mapObject.removeControl(this.control);
      this.control = null;

      if (this.markerCluster) {
        this.$parent.removeLayer(this.markerCluster);
      }      
    },
    add() {
      if (this.$parent._isMounted) {
        this.deferredMountedTo(this.$parent.mapObject);
      }
    },
  },
};
</script>
