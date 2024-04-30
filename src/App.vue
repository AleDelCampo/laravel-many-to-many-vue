<script>

import AppHeader from './components/AppHeader.vue';

export default {

  data() {
    return {
      
    }
  },

  components: {
    AppHeader
  },

  mounted() {

    
  },

  methods: {

    
  },
}

</script>

<template>

  <AppHeader></AppHeader>

  <div class="container py-4">

    <router-view></router-view>

  </div>

</template>

<style lang="scss" scoped>

</style>