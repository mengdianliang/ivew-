<template>
  <Layout :style="{padding: '0', background: '#ffffff', minWidth: '480px'}">
    <Content class="main-inner">
      <top-nav />
      <sider-iv />
      <Content class="main-con">
        <banner :img-source="imgSource" :autoplay="autoplay" :loop="loop" :autoplay-peed="autoplaySpeed"/>
      </Content>
    </Content>
    <Board />
  </Layout>
</template>

<script>
import {Layout, Content} from 'iview'
import Banner from '@/components/banner/banner'
import SiderIv from '@/components/sider/sider'
import TopNav from '@/components/top-nav/top-nav'
import Board from '@/components/board/board.vue'
import axios from 'axios'
export default {
  data () {
    return {
      imgSource: [],
      autoplay: true,
      loop: true,
      autoplaySpeed: 5000
    }
  },
  created () {
    axios.get('https://easy-mock.com/mock/5a2fd09f2704c108b1d12b23/example/api/imgSource')
      .then(res => {
        // console.log(res)
        this.imgSource = res.data.imgSource
      }).catch(err => {
        console.log(err)
      })
  },
  components: {
    Layout,
    Content,
    Banner,
    SiderIv,
    TopNav,
    Board
  }
}
</script>

<style scoped>
.main-inner{
  background: #ffffff;
  display: flex;
}
.main-con{
  background: #ffffff;
  overflow-x: hidden;
}
@media(max-width:768px) {
  .main-inner,.main-con{
    display: block;
  }
}
</style>
