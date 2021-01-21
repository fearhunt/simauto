<template>
  <b-navbar class="fixed-top simauto-border-radius" toggleable="lg" variant="simauto">
    <b-navbar-brand>
      <h3 style="color: white">SimAuto</h3>
      <!-- <nuxt-link to="/"> -->
      <!-- </nuxt-link> -->
    </b-navbar-brand>

    <b-nav-toggle target="nav-menu-collapse"></b-nav-toggle>

    <b-collapse id="nav-menu-collapse" is-nav>
      <b-navbar-nav class="ml-auto">
        <a href="#" class="simauto-nav-link">Upload</a>
        <a href="#how-it-works" class="simauto-nav-link">How It Works</a>
        <a href="#our-team" class="simauto-nav-link">Meet Our Team</a>
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