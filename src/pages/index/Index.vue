<template>
  <div class="container">
    <img src="@img/bj.jpg" alt="" class="index-bj">
    <index-header :browserType="browserType"></index-header>
    <alert-component :alertInfo="alertInfo" @hide="handleHideAlert"></alert-component>
  </div>
</template>

<script>
import IndexHeader from './components/Header'
import AlertComponent from '@comp/alert/Alert'
export default {
  name: 'Index',
  components: {
    IndexHeader,
    AlertComponent
  },
  data () {
    return {
      alertInfo: {
        title: '友情提示',
        content: '谢谢关注,本站正在努力建设中...敬请期待!!!',
        bottomText: '加油',
        status: true
      },
      browserType:-1  /* -1获取中 1为pc端 2为手机端 */
    }
  },
  methods: {
    handleHideAlert (e) {
      this.alertInfo.status = e
    },
    
    browserRedirect () {
      var sUserAgent = navigator.userAgent.toLowerCase();
      var bIsIpad = sUserAgent.match(/ipad/i) == "ipad";
      var bIsIphoneOs = sUserAgent.match(/iphone os/i) == "iphone os";
      var bIsMidp = sUserAgent.match(/midp/i) == "midp";
      var bIsUc7 = sUserAgent.match(/rv:1.2.3.4/i) == "rv:1.2.3.4";
      var bIsUc = sUserAgent.match(/ucweb/i) == "ucweb";
      var bIsAndroid = sUserAgent.match(/android/i) == "android";
      var bIsCE = sUserAgent.match(/windows ce/i) == "windows ce";
      var bIsWM = sUserAgent.match(/windows mobile/i) == "windows mobile";
      if (bIsIpad || bIsIphoneOs || bIsMidp || bIsUc7 || bIsUc || bIsAndroid || bIsCE || bIsWM) {
          this.browserType = 2
      } else {
          this.browserType = 1
      }
    },
  },
  mounted () {
    this.browserRedirect()
  }
}
</script>

<style scoped lang="stylus">
  .container
    display:flex
    flex-direction: column
    align-items:center
    .index-bj
      position:fixed
      left:0
      top:0
      right:0
      width:100%
      height:100%
</style>