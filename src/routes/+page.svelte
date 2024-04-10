<style>
  @import url("$lib/global.css");
</style>

<script lang="ts">
import mapboxgl from "mapbox-gl";
import "../../node_modules/mapbox-gl/dist/mapbox-gl.css";
import { onMount } from "svelte";
import { PUBLIC_MAPBOX_ACCESS_TOKEN } from '$env/static/public';

let mapContainer;
let lng = -71.224518;
let lat = 42.213995;
let zoom = 9;
mapboxgl.accessToken = PUBLIC_MAPBOX_ACCESS_TOKEN;

onMount(() => {
  const initialState = { lng: lng, lat: lat, zoom: zoom };
	const map = new mapboxgl.Map({
		/* options */
    container: mapContainer,
    style: `mapbox://styles/mapbox/outdoors-v11`,
    center: [initialState.lng, initialState.lat],
    zoom: initialState.zoom,
	});
})
</script>

<div>
  <h1>HDB ColourSG</h1>
  <p>Colors of Housing Development Board (HDB) Blocks in Singapore</p>
  <div id="map" bind:this={mapContainer} />
</div>