<template>
  <div class="home">
    



    
    <Tabbar/>
    <!-- <router-link to="/one">home</router-link>
    <router-link to="/about">about</router-link>
    <router-view></router-view> -->
  </div>
</template>

<script>
// @ is an alias to /src

import Tabbar from '@/components/Tabbar.vue'
export default {
  name: 'Home',
  components: {
    Tabbar
  }
}
</script>

<style scoped>

</style>
