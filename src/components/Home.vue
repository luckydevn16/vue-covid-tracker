<template>
  <main v-if="!loading">
    <div class="container">
      <div class="select-box">
        <CountrySelect @getCountry="getCountryData" :countries="countries" />
        <button v-if="stats.Country" class="clear-btn" @click="clearCountryData">Clear</button>
      </div>
      <DataTitle :text="title" :dataDate="dataDate" />
      <DataBox :stats="stats" />
    </div>
  </main>
  <main v-else class="loading-block">
    <h3>Loading...</h3>
    <img :src="loadingImage" alt="loading" class="loading-img">
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBox from '@/components/DataBox'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  data() {
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/img/loading.gif')
    }
  },
  components: {
    DataTitle, DataBox, CountrySelect
  },
  methods: {
    async fetchApiData() {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchApiData();
      this.title = 'Global';
      this.stats = data.Global;
      this.loading = false;
    }
  },
  async created() {
    const data = await this.fetchApiData();
    
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  }
}
</script>

<style>
main {
  padding: 2rem 0;
}
.loading-block {
  display: grid;
  place-items: center center;
  padding: 4rem 1rem;
}
.loading-block h3 {
  opacity: .7
}
.loading-img {
  width: 5rem;
  height: auto;
  margin-top: 1rem;
}
.select-box {
    margin: 1rem 0 2rem 0;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
}
.clear-btn {
    min-width: 4rem;
    margin-left: 0.3rem;
    height: 40px;
    padding: 8px;
    background-color: #198754;
    color: #eee;
    border: none;
    border-radius: 4px;
    outline: none;
    cursor: pointer;
}
.clear-btn:active {
    opacity: .5
}
</style>
