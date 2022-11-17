<script>
import { store } from "../data/store";
import ActorCard from './ActorCard.vue';

export default {
  name : 'AppMain',
  components : {
    ActorCard
  },
  data() {
    return {
      store
    }
  }
}
</script>


<template>

  <div class="container">
    <div class="row">
      <ActorCard 
        v-for="actor in store.actorsList" 
        :key="actor.char_id" 
        :actor = 'actor'
      />
    </div>
    
  </div>
  
</template>


<style lang="scss" scoped>

</style>