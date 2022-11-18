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
      axios.get(store.apiUrl, {
        params : {
          category : store.categoryToSearch
        }
      })
      .then(function (response) {
        store.actorsList = response.data
        if(store.listCategory.length === 0){
          store.actorsList.forEach(actor => {
            if(!store.listCategory.includes(actor.category)) store.listCategory.push(actor.category);
          })
        }
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
  <AppSearch @startSearch = 'getActors()'/>
  <AppMain />
  
</template>


<style lang="scss">

@use './styles/general' as *;

</style>