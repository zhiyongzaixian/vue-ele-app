<template>
  <section id='foot_guide'>
      <section @click="gotoAddress({path: '/msite', query: {geohash}})" class="guide_item">

          <!--<svg   class="icon_style" >-->
            <!--<use v-if="$route.path.indexOf('msite') !== -1" xlink:href="#icon-waimai3"></use>-->
            <!--<use v-else xlink:href="#icon-waimai2"></use>-->
          <!--</svg>-->
        <!--底部外卖svg-->
          <span  v-if="$route.path.indexOf('msite') !== -1" >
            <svgImage className="icon_style" type="#icon-waimai3"/>
          </span>
          <span  v-else>
            <svgImage className="icon_style" type="#icon-waimai2"/>
          </span>
        <span>外卖</span>
      </section>
      <section @click="gotoAddress({path: '/search/' + geohash})" class="guide_item">
        <!--底部搜索指南svg-->
        <span  v-if="$route.path.indexOf('search') !== -1" >
          <svgImage className="icon_style" type="#icon-fingerpost"/>
        </span>
        <span  v-else>
          <svgImage className="icon_style" type="#icon-iconfontzhinanzhen"/>
        </span>
        <span>搜索</span>
      </section>
      <section @click="gotoAddress('/order')" class="guide_item">

        <!--<svg class="icon_style" >-->
          <!--<use v-if="$route.path.indexOf('order') !== -1" xlink:href="#icon-order"></use>-->
          <!--<use v-else xlink:href="#icon-dingdan"></use>-->
        <!--</svg>-->
        <!--底部订单svg-->
        <span  v-if="$route.path.indexOf('order') !== -1" >
          <svgImage className="icon_style" type="#icon-order"/>
        </span>
        <span  v-else>
          <svgImage className="icon_style" type="#icon-dingdan"/>
        </span>
        <span>订单</span>
      </section>
      <section @click="gotoAddress('/profile')" class="guide_item">
        <!--<svg class="icon_style" >-->
          <!--<use v-if="$route.path.indexOf('profile') !== -1" xlink:href="#icon-wode4"></use>-->
          <!--<use v-else xlink:href="#icon-wode1"></use>-->
        <!--</svg>-->

        <!--底部我的svg-->
        <span  v-if="$route.path.indexOf('profile') !== -1" >
          <svgImage className="icon_style" type="#icon-wode4"/>
        </span>
        <span  v-else>
          <svgImage className="icon_style" type="#icon-wode1"/>
        </span>
        <span>我的</span>
      </section>
  </section>
</template>

<script>
  import {mapState} from 'vuex'
  import svgImage from '../../common/svg_image/svg_image.vue'
  export default {
    components: {
      svgImage
    },
    computed: {
      ...mapState([
        'geohash'
      ]),
    },
    methods: {
      gotoAddress(path) {
        this.$router.push(path)
      }
    }
  }

</script>

<style lang="scss" scoped>
  @import '../../common/style/mixin';

  #foot_guide {
    background-color: #fff;
    position: fixed;
    z-index: 100;
    left: 0;
    right: 0;
    bottom: 0;
    @include wh(100%, 1.95rem);
    display: flex;
    box-shadow: 0 -0.026667rem 0.053333rem rgba(0, 0, 0, .1);
  }

  .guide_item {
    flex: 1;
    display: flex;
    text-align: center;
    flex-direction: column;
    align-items: center;

  .icon_style {
      @include wh(0.9rem, .9rem);
      margin-bottom: .1rem;
      margin-top: .1rem;
      fill: #ccc;
    }
    span {
      @include sc(.50rem, #666);
    }
  }

</style>
