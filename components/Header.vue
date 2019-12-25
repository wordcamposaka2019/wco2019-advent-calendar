<template>
  <nav id="header" class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a href="#" class="navbar-item">
        <img src="~/assets/images/logo.png" alt="">
        <span>WordCamp Osaka 2019 Advent Calendar</span>
      </a>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Header'
}
</script>
<style scoped lang="scss">
@import "../assets/sass/common";

#header {
  background-color: $base-color-deep;
}
</style>
