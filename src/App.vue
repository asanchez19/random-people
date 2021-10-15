<template>
  <div id="app" class="container">
      <navbar/>
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
        Navbar
    },

    /**
     * The component's name used for debugging.
     *
     * @type {String}
     */
    name: 'App',
}
</script>
<style lang="scss">
@import './sass/app.scss';
</style>
