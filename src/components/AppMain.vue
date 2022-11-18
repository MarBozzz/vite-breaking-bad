<script>
import { store } from "../data/store";
import ActorCard from './ActorCard.vue';
import AppLoading from "./AppLoading.vue";

export default {
  name : 'AppMain',
  components : {
    ActorCard,
    AppLoading
  },
  data() {
    return {
      store
    }
  },
  computed : {
    searchResponse(){
      if (store.actorsList.length > 0){
        return 'found ' + store.actorsList.length + ' characters';
      }
      return 'Sorry, no results available for this research, try another one'
    }
  }
}
</script>


<template>
<main class="d-flex justify-content-center">
  <div v-if="store.isLoaded" class="wrapper d-flex flex-column align-items-center">
    <div class="upperband">
      <p>{{searchResponse}}</p>
    </div>
    <div class="container d-flex justify-content-center">
      <div class="row d-flex justify-content-between">
        <ActorCard 
          v-for="actor in store.actorsList" 
          :key="actor.char_id" 
          :actor = 'actor'
        />
      </div>
    </div>
  </div>
  <div v-else>
    <AppLoading title="Loading....." />
  </div>
</main>
  
</template>


<style lang="scss" scoped>
main {
  .wrapper {
    background-image: url(../assets/img/wallpaperflare.com_wallpaper.jpg);
    background-size: cover;
    background-repeat: no-repeat;
    background-attachment: fixed;
    max-width: 70%;
    .upperband {
      height: 60px;
      width: 90%;
      background-color: #212529;
      margin-top: 3rem;
      line-height: 60px;
      padding-left: 1rem;
      font-weight: bold;
    }
    .container {
      max-width: 100%;
      padding: 1rem 5rem;
      .row {
      width: 100%;
      }
    }
  }
}


</style>