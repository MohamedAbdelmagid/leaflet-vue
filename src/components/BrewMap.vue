<template>
  <div class="row mt-2 map">
		<!-- <h2>Center is {{currentCenter}}, Zoom is {{currentZoom}}</h2> -->
		<l-map :zoom="zoom" :center="center"
			@update:zoom="zoomUpdate"
			@update:center="centerUpdate"
		>
			<l-tile-layer :url="url" :attribution="attribution"></l-tile-layer>
			<l-marker
				:key="i"
				v-for="(brew, i) in brews"
				:lat-lng="latLng(brew.latitude, brew.longitude)"
			>
			<l-icon
				:icon-size="iconSize"
				:icon-url="icon"
			></l-icon>
			</l-marker>
		</l-map>
  </div>
</template>

<script>
	import L from 'leaflet'
	import { LMap, LTileLayer, LMarker, LIcon } from 'vue2-leaflet'
	import beer from '../assets/beer-mug.png'

  export default {
		name: 'BrewMap',
		props: {
			brews: Array
		},
		data() {
			return {
				zoom: 7,
				currentZoom: 7,
				center: L.latLng(33.163354, -112.221328),
				currentCenter: L.latLng(33.163354, -112.221328),
				url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
				attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
				marker: L.latLng(47.413220, -1.219482),
				icon: beer,
				iconSize: [15, 15]
			}
		},
		components: {
			LMap,
			LTileLayer,
			LMarker,
			LIcon,
		},
		methods: {
			latLng(lat, lng) {
				return L.latLng(lat, lng)
			},
			centerUpdate(center) {
				this.currentCenter = center.toString()
			},
			zoomUpdate(zoom) {
				this.currentZoom = zoom
			},
		}
  }
</script>

<style lang="scss" scoped>
	.map {
		height: 100vh;
	}
</style>