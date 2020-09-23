<template>
  <div class="row mt-2 map">
		<l-map :zoom="zoom" :center="center">
			<l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
			<l-marker
				:key="i"
				v-for="(brew, i) in brews"
				:lat-lng="latLng(brew.latitude, brew.longitude)"
			>
			</l-marker>
		</l-map>
  </div>
</template>

<script>
	import L from 'leaflet'
	import { LMap, LTileLayer, LMarker } from 'vue2-leaflet'

  export default {
		name: 'BrewMap',
		props: {
			brews: Array
		},
		data() {
			return {
				zoom: 13,
				center: L.latLng(47.413220, -1.219482),
				url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
				attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
				marker: L.latLng(47.413220, -1.219482),
			}
		},
		components: {
			LMap,
			LTileLayer,
			LMarker,
		},
		methods: {
			latLng(lat, lng) {
				return L.latLng(lat, lng)
			}
		}
  }
</script>

<style lang="scss" scoped>
	.map {
		height: 100vh;
	}
</style>