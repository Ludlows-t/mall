<template>
  <div>
    <nav-bar class="home-nav"><div slot="center">购物车</div></nav-bar>
    <home-swiper :banners='banners'></home-swiper>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwiper from './childComps/HomeSwiper';
import {getHomeMultidata} from 'network/home.js'

export default {
    name: "Home",
    components: {
      NavBar,
      HomeSwiper
    },
    data(){
      return {
        banners:[],
        recommends: []
      }
    },
    created() {
      //请求多个数据
      getHomeMultidata().then(res => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
.home-nav{
  background-color: var(--color-tint);
  color: #ffffff;
}

</style>