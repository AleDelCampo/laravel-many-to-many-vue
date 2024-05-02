<script>

import AppHeader from './components/AppHeader.vue';
import AppFooter from './components/AppFooter.vue';

export default {

  data() {
    return {
      
    }
  },

  components: {
    AppHeader,
    AppFooter
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

  <AppFooter></AppFooter>

</template>

<style lang="scss" scoped>

</style>