<template>
  <div class="overlay-load loading-page" v-if="loading">
    <div class="loader"></div>
  </div>  
</template>

<script>
  export default {
    data() {
      return {
        loading: false
      }
    },

    methods: {
      start() {
        this.loading = true
      },

      finish() {
        this.loading = false
      }
    }
  }
</script>

<style lang="scss" scoped>
  .overlay-load {
    width: 100vw;
    height: 100vh;
    background: rgba(0, 0, 0, 0.69);
    z-index: 9999;
    position: fixed;
    top: 0;

    .loader, .loader::after {
      border-radius: 50%;
      width: 10em;
      height: 10em;
    }

    .loader {
      margin: 60px auto;
      font-size: 10px;
      position: relative;
      top: 30%;
      transform: translateY(-30%);
      text-indent: -9999em;
      border-top: 0.8em solid rgba($secondary-color, 0.2);
      border-right: 0.8em solid rgba($secondary-color, 0.2);
      border-bottom: 0.8em solid rgba($secondary-color, 0.2);
      border-left: 0.8em solid $secondary-color;
      -webkit-transform: translateZ(0);
      -ms-transform: translateZ(0);
      transform: translateZ(0);
      -webkit-animation: load8 1.5s infinite linear;
      animation: load8 1.25s infinite linear;
    }
  }

  @-webkit-keyframes load8 {
    0% {
      -webkit-transform: rotate(0deg);
      transform: rotate(0deg);
    }

    100% {
      -webkit-transform: rotate(360deg);
      transform: rotate(360deg);
    }
  }

  @keyframes load8 {
    0% {
      -webkit-transform: rotate(0deg);
      transform: rotate(0deg);
    }

    100% {
      -webkit-transform: rotate(360deg);
      transform: rotate(360deg);
    }
  }
</style>