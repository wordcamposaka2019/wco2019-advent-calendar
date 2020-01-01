<template>
  <div>
    <Header />
    <nuxt />
    <Footer />
  </div>
</template>

<style lang="scss">
  @import "../assets/sass/common";
  body {
    background-color: $main-color;
    font-size: 1rem;
    color: $body-fontcolor;
    font-family: $ff-base, sans-serif;
  }

  // Links
  a {
    color: $link-color-light;
    font-family: $ff-base, sans-serif;
  }

  a:visited {
    color: $link-color-light;
  }

  a:hover,
  a:active {
    color: $link-color;
  }

  a:focus {
    outline: thin dotted;
    text-decoration: underline;
  }

</style>
<script>
import Header from '../components/Header'
import Footer from '../components/Footer'
export default {
  components: { Footer, Header }
}
</script>
