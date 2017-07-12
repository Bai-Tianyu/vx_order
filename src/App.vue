<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <keep-alive>
      <router-view :seller="seller"></router-view>
    </keep-alive>
  </div>
</template>

<script>
import header from './components/header/header'
import axios from 'axios'

const ERR_OK = 0

export default {
  name: 'app',
  data() {
    return {
      seller: {}
    }
  },
  created() {
    axios.get('static/data.json').then((res) => {
      this.seller = res.data.seller
    })
  },
  components: {
    'v-header': header
  }
}
</script>

<style lang="stylus">
  @import './common/stylus/index'
</style>
