<template>
  <header class='head_top'>
    <slot name='logo'></slot>
    <slot name='search'></slot>
    <section class="head_goback" v-if="goBack" @click="$router.go(-1)">

      <!--<svg width="100%" height="100%">-->
        <!--<use xlink:href="#icon-jiantouzuo1"></use>-->
      <!--</svg>-->
      <!--搜索箭头导航-->
      <svgImage className="search_guide" type='#icon-jiantouzuo1'/>
    </section>
    <router-link class="head_login" :to="userInfo ? '/profile':'/login'" v-if='signinUp'>
      <!--<svg class="user_avatar" v-if="userInfo">-->
        <!--<use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#user"></use>-->
      <!--</svg>-->
      <!--用户名-->
      <svgImage className="user_avatar" v-if="userInfo" type="#icon-wode"/>
      <span class="login_span" v-else>登录|注册</span>
    </router-link>
    <section class="title_head ellipsis" v-if="headTitle">
      <span class="title_text">{{headTitle}}</span>
    </section>
    <slot name="edit"></slot>
    <slot name="msite-title"></slot>
    <slot name="changecity"></slot>
    <slot name="changeLogin"></slot>
  </header>
</template>

<script>
  import { mapState, mapActions } from 'vuex'
  import svgImage from '../../common/svg_image/svg_image.vue'
  export default {
    components: {
      svgImage
    },
    data () {
      return {}
    },
    mounted () {
      //获取用户信息
      this.getUserInfo()
    },
    props: ['signinUp', 'headTitle', 'goBack'],
    computed: {
      ...mapState([
        'userInfo'
      ]),
    },
    methods: {
      ...mapActions([
        'getUserInfo'
      ]),
    }
  }

</script>

<style lang="scss" scoped>
  @import '../../common/style/mixin';

  .head_top {
    background-color: $blue;
    position: fixed;
    z-index: 100;
    left: 0;
    top: 0;
    @include wh(100%, 1.95rem);
    .head_goback {
      left: 0.4rem;
      @include wh(0.6rem, 1rem);
      line-height: 2.2rem;
      margin-left: .4rem;
    }
    .head_login {
      right: 0.55rem;
      @include sc(0.65rem, #fff);
      @include ct;
      .login_span {
        color: #fff;
      }
      .user_avatar {
        fill: #fff;
        @include wh(.8rem, .8rem);
      }
    }
    .title_head {
      @include center;
      width: 50%;
      color: #fff;
      text-align: center;
      .title_text {
        @include sc(0.8rem, #fff);
        text-align: center;
        font-weight: bold;
      }
    }
  }
  .search_guide {
    width:100%;
    height:100%;
  }
</style>
