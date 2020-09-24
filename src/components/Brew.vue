<template>
  <div class="row mx-3 p-2">
    <div class="col-4">
      <h1 class="text-center text-primary">Breweries List</h1>
      <BrewList :brews="brews"
        @mouse-over-brew="mouseOverBrew"
        @mouse-left-brew="mouseLeftBrew"
      />
    </div>
    <div class="col-8">
      <BrewMap :brews="brews"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import BrewList from './BrewList.vue'
import BrewMap from './BrewMap.vue'

export default {
  name: 'Brew',
  components: {
    BrewList,
    BrewMap,
  },
  data() {
    return {
      brews: [],
      normalIconSize: [20, 20],
      largeIconSize: [50, 50],
    }
  },
  mounted() {
    axios.get('https://api.openbrewerydb.org/breweries') // https://api.openbrewerydb.org/breweries
      .then(response => {
        this.brews = response.data.filter(brew => brew.state == 'Arizona').map(brew => {
          brew.iconSize = this.normalIconSize
          return brew
        })
      })
  },
  methods: {
    mouseOverBrew(index) {
      this.brews[index].iconSize = this.largeIconSize
    },
    mouseLeftBrew(index) {
      this.brews[index].iconSize = this.normalIconSize
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
