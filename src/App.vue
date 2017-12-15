<template>
  <div>
    <transition name="router-fade" mode="out-in">
      <keep-alive v-if="$route.meta.keepAlive">
        <router-view></router-view>
      </keep-alive>
      <router-view v-if="!$route.meta.keepAlive"></router-view>
    </transition>

    <footGuide v-show="$route.meta.isTop"></footGuide>
    <!--<svgIcon></svgIcon>-->
  </div>
</template>



<script>
  // 引入iconfont中svg图标js部分
  import './common/svg_image/iconfont'
  import svgIcon from 'components/common/svg'
  import footGuide from 'components/footer/footGuide2'


  export default {
    components: {
      svgIcon,
      footGuide
    },
  }
</script>

<style lang="scss">
  .router-fade-enter-active, .router-fade-leave-active {
    transition: opacity .3s;
  }

  .router-fade-enter, .router-fade-leave-to {
    opacity: 0;
  }
</style>
