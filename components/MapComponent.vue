<template>
    <div class="search-map z-10 w-full h-screen lg:h-full map-screen close">
        <div id="search-map" class="google-map" ref="googleMap"></div>
    </div>
</template>

<script>
import GoogleMapsApiLoader from 'google-maps-api-loader';

export default {
    props: {
        mapConfig: Object,
        apiKey: String,
        locations: Array
    },

    data() {
        return {
            google: null,
            map: null
        }
    },

    async mounted() {
        const googleMapApi = await GoogleMapsApiLoader({
            apiKey: this.apiKey
        })
        this.google = googleMapApi
        this.initializeMap()
    },

    methods: {
        initializeMap() {
            const mapContainer = this.$refs.googleMap
            var map = new this.google.maps.Map(mapContainer, this.mapConfig)
            this.locations.map(function(location){
                var myLatLng = { lat: location.lat, lng: location.lng };
                new google.maps.Marker({
                    position: myLatLng,
                    map: map
                })
            });
            this.map = map;
        }
    }
}
</script>

<style>
    .search-map.close {
        left: 0;
        position: static;
    }

    .search-map.close {
        left: -0;
        position: static;
    }

    .map-screen {
        max-height: 100vh;
    }

    #search-map {
        width: 100%;
        position: relative;
        overflow: hidden;
        height: 100%;
        border-style: none;
        border-width: 0;
    }
</style>