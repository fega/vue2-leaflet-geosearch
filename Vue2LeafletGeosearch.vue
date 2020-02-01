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

  mounted() {
    this.add();
  },

  beforeDestroy() {
    this.remove();
  },

  data(){
    return {
      searchControl: null,
    }
  },

  methods: {
    add() {
      if(this.$parent._isMounted) {

        this.searchControl = new GeoSearchControl(this.options)

        this.$parent.mapObject.addControl(this.searchControl);      
        this.searchControl.getContainer().onclick = e => { e.stopPropagation(); };
      }
    },

    remove() {
      if (this.markerCluster) {
        this.$parent.removeLayer(this.markerCluster);
      }      

      if(this.searchControl){
        this.$parent.mapObject.removeControl(this.searchControl);
        this.searchControl = null
      }
    },
  },

  watch: {
    options:{
      deep: true,
      handler(){
        this.remove()
        this.add()
      }
    }
  }
};
</script>
