<template>
  <div class="row mx-3 p-2">
    <div class="col-4">
      <h1 class="text-center text-primary">Breweries List</h1>
      <BrewList :brews="brews"/>
    </div>
    <div class="col-8">
      <BrewMap/>
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
      brews: []
    }
  },
  mounted() {
    axios.get('https://api.openbrewerydb.org/breweries') // https://api.openbrewerydb.org/breweries
      .then(response => {
        this.brews = response.data
      })
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
