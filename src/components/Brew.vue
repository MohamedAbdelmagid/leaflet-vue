<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-primary">Breweries List</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-6">
        <BrewList :brews="brews"/>
      </div>
      <div class="col-6">
        <h2 class="text-center">right</h2>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import BrewList from './BrewList.vue'

export default {
  name: 'Brew',
  components: {
    BrewList
  },
  data() {
    return {
      brews: []
    }
  },
  mounted() {
    axios.get('https://api.openbrewerydb.org/breweries')
      .then(response => {
        this.brews = response.data
        console.log(this.brews);
      })
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
</style>
