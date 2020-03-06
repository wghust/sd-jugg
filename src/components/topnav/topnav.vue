<style lang="stylus">
  .tb-nav
    // box-shadow 0 1px 1px rgba(0,0,0,.1) !important
    // background-color #ffc107 !important
    box-shadow none !important
    z-index 999
  
  .logoCon
    width 200px
    background-color #fff
    margin-left -15px
    padding-left 15px
    float left
    border-bottom 1px solid #f2f2f2

  .logo
    display inline-block
    height 50px
    line-height 50px
    color #333
    img
      height 40px
      margin-top -14px
    span
      color #333
      font-size 24px
      margin-left 10px
  .subLogo
    color #333
    font-size 12px
  
  .topTool
    display block
    height 50px
    float right
</style>
<template>
  <div>
    <tb-nav :position="false" class="clearfix" :style="{'background-color': bgcolor}">
      <div class="logoCon" :style="{position: isLeftFixed ? 'fixed' : 'relative'}">
        <a href="" class="logo"><img src="http://cdn2.tecclass.cn/doom_1x_new.png"><span>天龙</span></a>
        <a href="" class="subLogo">主宰</a>
      </div>
      <cur-user></cur-user>
      <div class="topTool">
        <tb-switch class="tb-m-t-15 tb-m-r-30" bgmcolor="red" v-model="curLeftShow"></tb-switch>
      </div>
    </tb-nav>
  </div>
</template>

<script>
  import curUser from '../curuser/curuser.vue';

  export default {
    props: {
      isLeftFixed: {
        type: Boolean,
        default: true
      },

      bgcolor: {
        type: String,
        default: '#4285f4'
      }
    },

    data () {
      return {
        curLeftShow: true
      }
    },

    created () {
      this.curLeftShow = this.isLeftFixed;
      this.$watch('curLeftShow', (val) => {
        this.$emit('changeLeft', val);
      });
    },

    components: {
      curUser
    }
  }
</script>