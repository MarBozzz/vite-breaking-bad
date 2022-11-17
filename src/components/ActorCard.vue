<script>
export default {
  name : 'ActorCard',
  props : {
    actor : Object
  }
}
</script>


<template>
  <div class="mb-card col-2">
    <img 
      :src="actor.img" :alt="actor.name">
      <h3>{{actor.name}}</h3>
      <h4>{{actor.category}}</h4>
      <h5>{{actor.status}}</h5>
  </div>
  
</template>


<style lang="scss" scoped>

</style>