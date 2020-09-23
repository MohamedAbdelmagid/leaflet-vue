<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-primary">Breweries List</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-6 brew-list">
        <div class="card" style="width: 18rem;">
          <ul class="list-group">
            <li v-for="(brew, i) in brews" :key="i" class="list-group-item">
              {{ brew.name }}, {{ brew.state }}
            </li>
          </ul>
        </div>
      </div>
      <div class="col-6">
        <h2 class="text-center">right</h2>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Brew',
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
.brew-list {
  overflow-y: scroll;
  height: 95vh;
  li {
    &:hover {
      background-color: lightgray;
    }
  }
}
</style>
