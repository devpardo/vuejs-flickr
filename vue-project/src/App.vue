<template>
  <div id="app">
    <div class="app-container">
      <Menu @clicked="pick" :activeItem="category"/>
      <Lists :images="images" />
    </div>
  </div>
</template>

<script>
import Menu from './components/Menu';
import Lists from './components/Lists';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Menu,
    Lists
  },
  data() {
    return {
      category: '',
      images : [],
      showDetails : false
    }
  },
  methods: {
    pick(param) {
      this.category = param;
      this.getPhotos().then(result => this.images = result.data.results);
    },
    getPhotos() {
      return axios.get('https://api.unsplash.com/search/photos', {
        params : {
          client_id : 'fygzxU-NJaSPYiUeZDY0ppl7hUXNo2-UYMCDO_3vHPQ',
          query: this.category,
          per_page: 12
        }
      });
    }
  }
}
</script>

<style lang="sass">
* 
  padding: 0
  margin: 0
  box-sizing: border-box
  font-family: Arial, Helvetica, sans-serif

.app-container 
  margin: 0 auto
  margin-top: 50px
  margin-bottom: 50px
  width: 80%
  display: flex

.col-50
  width: 50%
  float: left
  padding: 20px
</style>
