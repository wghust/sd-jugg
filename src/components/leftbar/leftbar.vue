<style lang="stylus">
.leftBar
  position fixed
  left 0
  top 50px
  height calc(100% - 50px)
  width 200px
  background-color #fff
  box-shadow 0 1px 1px rgba(0, 0, 0, 0.15)
  overflow auto
  
.leftBarNav
  box-shadow none !important

.efLeft-enter-active
  transition all 0.25s
  opacity 0
  left -200px
.efLeft-enter-to
  opacity 1
  left 0
.efLeft-leave-active
  opacity 1
  left 0
.efLeft-leave-to
  transition all 0.25s
  opacity 0
  left -240px
</style>

<template>
  <transition name="efLeft">
    <div class="leftBar" v-if="isLeftFixed">
      <tb-card class="leftBarNav tb-m-t-20">
        <tb-card-body>
          <tb-menu class="tb-p-b-20">
            <tb-menu-item label="首页" :index="1" icon="view-list" :is-router="true" url="/index"></tb-menu-item>
            <tb-menu-item label="表单例子" :index="1" icon="view-list">
              <tb-menu>
                <tb-menu-item label="基础表单" :index="2" :is-router="true" url="/form"></tb-menu-item>
                <tb-menu-item label="数据列表" :index="2" :is-router="true" url="/data"></tb-menu-item>
              </tb-menu>
            </tb-menu-item>
            <tb-menu-item label="个人信息" :index="1" icon="view-list" :is-router="true" url="/profile"></tb-menu-item>
            <tb-menu-item label="登录" :index="1" icon="view-list" :is-router="true" url="/login"></tb-menu-item>
            <tb-menu-item label="404" :index="1" icon="view-list" :is-router="true" url="/404"></tb-menu-item>
          </tb-menu>
        </tb-card-body>
      </tb-card>
    </div>
  </transition>
</template>

<script>
  export default {
    props: {
      isLeftFixed: {
        type: Boolean,
        default: true
      }
    },

    data () {
      return {
        pathName: window.location.pathname
      }
    },

    created () {
    },

    methods: {
    }
  }
</script>