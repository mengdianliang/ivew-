<template>
  <div id="app">
    <div class="layout">
      <Layout>
        <head-iv></head-iv>
        <div class="main">
          <keep-alive>
            <router-view></router-view>
          </keep-alive>
        </div>
        <foot-iv />
      </Layout>
    </div>
  </div>
</template>

<script>
import {Layout} from 'iview'
import HeadIv from '@/components/header/header'
import FootIv from '@/components/footer/footer'
export default {
  components: {
    Layout,
    HeadIv,
    FootIv
  }
}
</script>

<style scoped>
#app{
  min-width: 480px;
}
.layout{
  border: 1px solid #d7dde4;
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.main{
  margin-top: 66px;
}
</style>
