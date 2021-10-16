<template>
  <div id="app">
      <navbar />
    <router-view />
  </div>
</template>
<script>
import Navbar from '@/components/Navbar.vue'

export default {
    /**
     * The component's registered child components.
     *
     * @type {Object}
     */
    components: {
       Navbar, 
    },
    
}
</script>
