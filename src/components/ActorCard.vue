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
    <div class="image-container">
      <img 
      :src="actor.img" :alt="actor.name">
    </div>
    <h3>{{actor.name}}</h3>
    <h4>{{actor.category}}</h4>
    <h5>{{actor.status}}</h5>
  </div>
  
</template>


<style lang="scss" scoped>
@use '../styles/partials/vars' as *;
.mb-card {
  width: 19%;
  padding: 1rem;
  margin-bottom: 2rem;
  background-color: $main-color;
  text-align: center;
  &:hover {
    cursor: pointer;
    img {
      transform: scale(1.05);
    }
  }
  .image-container {
    height: 200px;
  }
  h3 {
    padding-top: 1rem
  }
  h4 {
    padding-top: 1.3rem
  }
}

</style>