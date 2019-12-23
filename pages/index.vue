<template>
  <div id="main" class="container">
    <div v-for="item in items" class="box">
      <div class="content">
        <template v-if="item.url && item.visible">
          <h4>
            <a :href="item.url" target="_blank" rel="noopener"><span class="date">{{ item.date }}</span> {{ item.title }} <span class="name">by {{ item.name }}</span></a>
          </h4>
          <p>{{ item.description }}</p>
        </template>
        <template v-else>
          <h4><span class="date">{{ item.date }}</span> {{ item.title }} <span class="name">by {{ item.name }}</span></h4>
        </template>
      </div>
    </div>
  </div>
</template>

<script>

import moment from 'moment'

export default {
  components: {},
  computed: {
  },
  async asyncData ({ app }) {
    app.$axios.setHeader('Access-Control-Allow-Origin', '*')
    // const items = await app.$axios.$get('/macros/s/AKfycbwelLPq7f-yeMs4M7tIRVQmzO-DRojXuurJUwxsStQ3oo1VFkb3/exec', {
    const items = await app.$axios.$get('/api')
    const now = moment().format('YYYYMMDD')
    for (let i = 0; i < items.length; i++) {
      items[i].visible = false
      // eslint-disable-next-line nuxt/no-this-in-fetch-data
      const date1 = moment(items[i].date, 'YYYY-MM-DD').format('YYYYMMDD')
      if (date1 <= now) {
        items[i].visible = true
      }
    }
    return {
      items
    }
  },
  isShow (date) {
    const date1 = moment(date, 'YYYY-MM-DD').format('YYYYMMDD')
    const now = moment().format('YYYYMMDD')
    return date1 <= now
  }
}
</script>

<style scoped lang="scss">
  @import "../assets/sass/common";

  .box {
    background-color: $base-color-deep;
  }

</style>
