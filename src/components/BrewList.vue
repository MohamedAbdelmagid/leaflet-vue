<template>
  <div class="card brew-list">
      <ul class="list-group">
        <li
          v-for="(brew, i) in brews"
          :key="i"
          class="list-group-item"
        >{{ brew.name }}, {{ brew.state }}</li>
      </ul>
    </div>
</template>

<script>
export default {
  name: "BrewList",
  props: {
    brews: Array
  }
};
</script>

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