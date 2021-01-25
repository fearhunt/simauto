<template>
  <b-navbar class="fixed-top simauto-border-radius" toggleable="lg" variant="simauto">
    <b-navbar-brand>
      <h3 style="color: white">SimAuto</h3>
      <!-- <nuxt-link to="/"> -->
      <!-- </nuxt-link> -->
    </b-navbar-brand>

    <b-navbar-toggle target="nav-menu-collapse">
      <template>
        <i class="fa fa-bars"></i>        
      </template>
    </b-navbar-toggle>

    <b-collapse id="nav-menu-collapse" is-nav>
      <b-navbar-nav class="ml-auto">
        <b-nav-item href="#introduction">Upload</b-nav-item>
        <b-nav-item href="#how-it-works">How It Works</b-nav-item>
        <b-nav-item href="#our-team">Meet Our Team</b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>
  
<script>
  export default {
    
  }
</script>

<style lang="scss">

</style>