<template>
    <div class="mask" v-if="alertInfo.status">
      <div class="alert-model">
        <div class="alert-hader">{{alertInfo.title}}</div>
        <div class="alert-content" v-html="alertInfo.content">
        </div>
        <div class="alert-footer">
          <div class="alert-sure" @click="handleHideModel">{{alertInfo.bottomText}}</div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'AlertComponent',
  props: {
    alertInfo: Object
  },
  methods: {
    /* 隐藏弹出层 */
    handleHideModel () {
      this.$emit('hide',false)
    }
  }
}
</script>

<style lang="stylus" scoped>
  .mask
    position:fixed
    top:0
    left:0
    right:0
    width:100%
    height:100%
    background:rgba(0,0,0,.5)
    z-index:99999
    display:flex
    flex-direction: column
    align-items:center
    justify-content:center
    .alert-model
      min-height:160px
      padding:20px 40px
      background:#fff
      border-radius:20px
      z-index:9
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items:center
      .alert-hader
        font-size:18px
        font-weight:600
      .alert-content
        font-size:14px
      .alert-footer
        .alert-sure
          padding:0 20px
          height:40px
          line-height:40px
          background:#de2418
          border-radius:15px
          cursor:pointer
          color:#fff
          text-align:center
</style>