---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

 <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
     integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
     crossorigin=""/>

 <!-- Make sure you put this AFTER Leaflet's CSS -->
 <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
     integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
     crossorigin=""></script>


<script>

document.addEventListener("DOMContentLoaded",  function () {
	doMapSetup();
});

let data = {% include metadata/data.json %};
data.person = "Person";
data.coordinates = "Coordinates";
data.description = "Description";


function doMapSetup(Opts) {
	let map = L.map('map').setView([50, 12], 4);

	L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);

	for (let i=0; i<data.length; i++) {
		let location = data[i][data.coordinates].split(/,?\s+,?/);
		let person = data[i][data.person];
		let description = data[i][data.description];

		L.marker(location)
			.addTo(map)
			.bindPopup(`<b>${person}</b>: ${description}`);

	}
	
}

</script>

<style>
	#map { height: 500px; }
</style>

<div id="map"></div>

