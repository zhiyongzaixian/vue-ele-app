<template>
  <div class="rating_container">
    <section class="star_container">
      <svgImage className="grey_fill " type="#icon-star" v-for="num in 5" :key="num"/>
    </section>
    <div :style="'width:' + rating*2/5 + 'rem'" class="star_overflow">
      <section class="star_container">
        <svgImage className="orange_fill" type="#icon-starrating_comment" v-for="num in 5" :key="num"/>
      </section>
    </div>
  </div>
</template>

<script>
  import svgImage from '../../common/svg_image/svg_image.vue'

  export default {
    components: {
      svgImage
    },
    data () {
      return {}
    },
    mounted () {

    },
    props: ['rating'],
  }
</script>

<style lang="scss" scoped>
  @import '../../common/style/mixin';

  .rating_container {
    position: relative;
    top: .2rem;
    @include wh(2rem, .4rem);
    .star_overflow {
      overflow: hidden;
      position: relative;
      height: 100%;
    }
    .star_container {
      position: absolute;
      display: flex;
      width: 2rem;
      height: 0.4rem;
      top: -0.02rem;
      left: -0.02rem;
      .grey_fill {
        fill: #d1d1d1;
      }
      .orange_fill {
        fill: #ff9a0d;
      }
      .iconfont {
        font-size: 0.01rem;
      }
    }
  }
</style>
