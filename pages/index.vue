<template>
  <div id="__layout">
    <HeaderComponent />
    <div class="lg:flex content">
      <div :class="(!full) ? 'lg:w-1/2' : 'lg:w-full'">
        <button class="absolute justify-center items-center w-12 h-12 bg-teal-500 text-white right-0" v-if="!hide" v-on:click="showMap()">
          <span class="material-icons font-material">
            place
          </span>
        </button>
        <div class="cards bg-white">
          <div class="pt-6 lg:overflow-y-auto lg:overflow-x-visible map-content">
            <div>
              <div class="flex flex-wrap justify-center">
                <div v-for="imovel of imoveis" class="card-wrapper">
                  <ImovelCard 
                    :thumbnail='imovel._source.main_picture'
                    :price='imovel._source.price'
                    :title='imovel._source.page_breadcrumb[2].title'
                    :property_type='imovel._source.property_type'
                    :page_title='imovel._source.page_title'
                    :full_address='imovel._source.full_address'
                    :surface_area='imovel._source.surface_area'
                    :bedrooms='imovel._source.bedrooms'
                  />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="lg:w-1/2" v-if="show">
        <button class="absolute justify-center items-center w-12 h-12 bg-teal-500 text-white" id="toggleMap" v-on:click="hideMap()">
          <span class="material-icons font-material">
            format_list_bulleted
          </span>
        </button>
        <MapComponent
          :mapConfig='googleMapsConfig()'
          :apiKey='googleMapsApiKey()'
          :locations='googleMapsPins()'
        />
      </div>
    </div>
  </div>
</template>

<script>
import ImovelCard from '@/components/ImovelCard';
import HeaderComponent from '@/components/HeaderComponent';
import MapComponent from '@/components/MapComponent';

export default {
  components: {
    HeaderComponent,
    ImovelCard,
    MapComponent
  },
  data () {
    return {
      imoveis: [],
      show: true,
      hide: true,
      full: false
    }
  },
  async fetch () {
    const response = await this.$axios.$get('https://api.casafy.com/api/v2/search/elasticsearch/find?q=sp+sao-paulo/venda-direta')
    this.imoveis = response.results
  },
  methods: {
    googleMapsConfig() {
      const lat = this.imoveis[0]._source.lat;
      const lng = this.imoveis[0]._source.lng;
      return {
        center: { lat, lng },
        zoom: 10
      };
    },
    googleMapsApiKey() {
      return '';
    },
    googleMapsPins() {
      const latLng = [];
      this.imoveis.map(function(value){
        latLng.push({
          lat: value._source.lat,
          lng: value._source.lng
        })
      });
      return latLng;
    },
    hideMap() {
      this.show = false;
      this.hide = false;
      this.full = true;
    },
    showMap() {
      this.show = true;
      this.hide = true;
      this.full = false;
    }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans&display=swap');

  body, h1, h2, h3, h4, h5, h6, p {
    font-family: 'Open Sans', sans-serif;
  }

  .content {
    margin-top: 48px;
  }

  .map-content {
    max-height: 85vh;
  }

  .map-content::-webkit-scrollbar {
    width: .25rem;
    --bg-opacity: 1;
    background-color: #d9d9d9;
    background-color: rgba(217,217,217,var(--bg-opacity));
  }

  .map-content::-webkit-scrollbar-thumb {
    --bg-opacity: 1;
    background-color: #fc6360;
    background-color: rgba(252,99,96,var(--bg-opacity));
    border-radius: .5rem;
  }

  .cards {
    z-index: 20;
    height: 100%;
  }

  .card-wrapper {
    max-width: 18rem;
    margin-bottom: 1.5rem;
    margin-left: .5rem;
    margin-right: .5rem;
    width: 100%;
  }

  #toggleMap {
    z-index: 999;
  }

  .font-material {
    font-size: 47px;
  }

  .right-0 {
    right: 0;
    margin-right: .25rem;
  }
</style>