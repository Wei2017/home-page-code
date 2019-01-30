<template>
  <div>
    <alert-component :alertInfo="alertInfo" @hide="handleHideAlert"></alert-component>
  </div>
</template>

<script>
import AlertComponent from '@comp/alert/Alert'
export default {
  name: 'Contact',
   data () {
    return {
      alertInfo: {
        title: '友情提示',
        content: '页面建设ing...',
        bottomText: '加油',
        status: true
      },
    }
  },
  components: {
    AlertComponent
  },
  methods: {
    handleHideAlert (e) {
      this.$router.push({
          path: '/',
          query: {
            status: false
          }
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
  
</style>