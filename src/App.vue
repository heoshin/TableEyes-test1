<template>
  <div class="map"></div>

  <SortSelector id="sort-selector" />
  
  <Card class="card" v-for="data in stores" :key="data" :data="data" />
</template>

<script>
import stores from './assets/data.js'
import Card from './Card.vue'
import SortSelector from './SortSelector.vue'

export default {
  name: 'App',
  data() {
    data : [
      mounted() {
        stores = 
      },
    ]
    return {
      oriStores: stores,
      stores: [...stores],
      curKindIdx: 0,
    }
  },
  methods : {
    setCurKind(idx) {
      this.curKindIdx = idx;
      if(this.curKindIdx == 0) {
        this.stores.sort((a, b) => a.count / a.countMax - b.count / b.countMax);
      }
      else if (this.curKindIdx == 1) {
        this.stores.sort((a, b) => a.distance - b.distance);
      }
    },
    getCurKindMargin() {
      return { marginLeft : this.curKindIdx * 150 + 'px' }
    },
  },
  components: {
    Card : Card,
    SortSelector : SortSelector,
  }
}
</script>

<style>
* {
  margin: 0;
}
.map {
  width: 90%; height: 400px;
  margin: 0 auto;
  background: lightgray;
}
#sort-selector {
  position: sticky;
  z-index: 1;
  top: 10px;
  margin-top: 10px;
}
.card {
  margin-top: 10px;
}
</style>
