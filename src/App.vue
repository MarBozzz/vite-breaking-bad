<script>
import axios from 'axios';
import {store} from './data/store'

import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import AppMain from './components/AppMain.vue';

export default {
  name : 'App',
  data() {
    return {
      store
    }
  },
  components : {
    AppHeader,
    AppSearch,
    AppMain
  },
  methods: {
    getActors() {
      store.isLoaded = false;
      axios.get(store.apiUrl)
      .then(function (response) {
        store.actorsList = response.data
        store.isLoaded = true
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      })
    }
  },
  mounted() {
    this.getActors();
  }
}
</script>


<template>

  <AppHeader />
  <AppSearch />
  <AppMain />
  
</template>


<style lang="scss">

@use './styles/general' as *;

</style>