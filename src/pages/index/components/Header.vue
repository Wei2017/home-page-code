<template>
  <div class="header-outer">
    <div class="header-menu" :class="browserType ==2?'header-menu-center':''">
      <router-link to="/" class="name-logo" :style="browserType == 1?'margin-left:80px;float:left':''">
        XiaoWeiGe's HomePage
        <span>XiaoWeiGe's HomePage</span>
      </router-link>
      <ul class="router-list" v-if="browserType == '1'">
      	<router-link tag="li" to="/" class="list-item"><span class="iconfont">&#xe65e;</span>主页</router-link>
      	<router-link tag="li" to="/about" class="list-item"><span class="iconfont">&#xe68d;</span>关于我</router-link>
      	<router-link tag="li" to="/contact" class="list-item"><span class="iconfont">&#xe607;</span>联系我</router-link>
      </ul>
    </div>
    <div class="header">
      <img src="@img/head.jpg" alt="" class="head-img">
      <p class="home-page-title">晓伟哥的个人主页</p>
      <p class="autograph">小小前端耕耘者</p>
      <nav class="header-nav">
        <a href="https://github.com/Wei2017" title="GitHub" class="iconfont">&#xe600;</a>
        <a href="https://weibo.com/XiaoWeiGe1005" title="SinaWeiBo" class="iconfont">&#xe67a;</a>
        <a href="javascript:;" title="Wechat" class="iconfont" @click="showWxQrcode">&#xe608;</a>
        <a href="https://user.qzone.qq.com/527188405/infocenter" title="QQ" class="iconfont">&#xebb4;</a>
      </nav>
    </div>
    <alert-component :alertInfo="alertInfo" @hide="handleHideAlert"></alert-component>
  </div>
</template>

<script>
import AlertComponent from '@comp/alert/Alert'
export default {
  name: 'IndexHeader',
  props: {
    browserType: Number
  },
  components:{
    AlertComponent
  },
  data () {
    return {
      alertInfo: {
        title: '个人微信',
        content: '<img src="/static/img/wxqrcode.jpg" style="width:200px;height:200px;margin:20px"/>',
        bottomText: '欢迎扫码交流',
        status: false
      },
    }
  },
  methods: {
    showWxQrcode () {
      this.alertInfo.status = true
    },
    handleHideAlert (e) {
      this.alertInfo.status = e
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~@css/mixins.styl'
  .header-outer
    z-index:999
    .header
      z-index:999
      text-align:center
      padding-top:80px
      .head-img
        width:130px
        height:130px
        border-radius:50%
        transition: all 1.6s
      .head-img:hover
        -webkit-transform: rotate(360deg)
        -moz-transform: rotate(360deg)
        -ms-transform: rotate(360deg)
        transform: rotate(360deg)
        -ms-transform: rotate(360deg) /* IE 9 */
        -webkit-transform: rotate(360deg) /* Safari and Chrome */
      .home-page-title
        padding:20px 0
        font-size:40px
        color:#fff
        transition: all 0.5s
        font-weight: 400;
      .home-page-title:hover
        letter-spacing: 5px
      .autograph
        font-size:26px
        color:#666
        letter-spacing: 5px
      .header-nav
        margin:20px 0
        a
          margin:0 8px
          font-size:30px
          color:#696969
          transition: 0.2s ease
        a:hover
          color: #0cc;
    .header-menu-center
      text-align:center
    .header-menu
      position:fixed
      top:0
      left:0
      width:100%
      padding-top:20px
      box-shadow: rgba(14,14,14,0.26) 0px 0px 10px;
      .name-logo
        color: #fff
        font-size: 16px
        text-transform: capitalize
        font-weight: 600
        letter-spacing: 4px
        line-height:20px
        span
          color: rgba(255, 255, 255, 0.2)
          font-size: 16px
          text-transform: capitalize
          font-weight: 600
          letter-spacing: 4px
          display: block
          transform: rotateX(155deg)
          -webkit-transform: rotateX(155deg)
          -o-transform: rotateX(155deg)
          -moz-transform: rotateX(155deg)
          -ms-transform: rotateX(155deg)
      .router-list
        float:right
        margin-right:100px
        .list-item
          display:inline-block
          margin:0 22px
          font-size:15px
          color:#fff
          cursor:pointer
</style>
