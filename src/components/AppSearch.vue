<script>

import { store } from "../data/store";
export default {
  name : 'AppSearch',
  data() {
    return {
      store
    }
  },
  methods : {
    reset() {
      store.categoryToSearch = ''
    }
  }
}
</script>


<template>

<div class="container d-flex">
  <div class="row">
    <div class="col-auto">
      <select @change="$emit('startSearch')" v-model="store.categoryToSearch" class="select form-select">
        <option value="" selected>Select Series</option>
        <option v-for="(category, index) in store.listCategory" :key="index" :value="category">{{category}}</option>
      </select>
    </div>
    <!-- <div class="col-auto">
      <button @click="reset()" type="button" class="btn btn-warning">Reset</button>
    </div> -->
  </div>
</div>
  
</template>


<style lang="scss" scoped>
.select {
  margin: 0 1rem 1rem 0;
}
</style>