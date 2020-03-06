<style lang="stylus">
</style>
<template>
  <div id="app">
    <top-nav :is-left-fixed="isLeftFixed" @changeLeft="changeLeft" bgcolor="#333" v-if="isTopShow"></top-nav>
    <left-bar :is-left-fixed="isLeftFixed"></left-bar>
    <div class="container" :class="{'fullContainer': !isLeftFixed}">
      <keep-alive>
        <router-view v-if="$route.meta.keepAlive"></router-view>
      </keep-alive>
      <router-view v-if="!$route.meta.keepAlive"></router-view>
    </div>
    <bottom-footer :is-left-fixed="isLeftFixed"></bottom-footer>
  </div>
</template>

<script>
  import leftBar from '../../../components/leftbar/leftbar.vue';
  import topNav from '../../../components/topnav/topnav.vue';
  import bottomFooter from '../../../components/bottomfooter/bottomfooter.vue';

  export default {
    computed: {
      isLeftFixed () {
        return this.$store.state.isLeftFixed;
      },
      isTopShow () {
        return this.$store.state.isTopShow;
      }
    },

    methods: {
      changeLeft (type) {
        this.$store.commit('SET_LEFTMENU', type);
      }
    },

    components: {
      leftBar,
      topNav,
      bottomFooter
    }
  }
</script>