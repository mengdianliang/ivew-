<template>
  <div class="sider-l" :style="{flex: '0 0 240px'}">
    <Menu theme="light" accordion v-if="slideList.length">
      <Submenu :name="item.type" v-for="item in slideList" :key="item.type">
        <template slot="title">
          <Icon :type="item.icon"></Icon>
          {{item.bigTitle}}
        </template>
        <MenuGroup v-if="item.bigList" v-for="typ in item.bigList" :title="typ.title" :key="typ.title">
          <MenuItem :name="`${item.type}-${index}`" v-for="(product, index) in typ.list" :key="`${item.type}-${index}`">
            <a :href="product.url" class="pro-link">{{product.name}}</a>
          </MenuItem>
        </MenuGroup>
        <MenuItem v-if="!item.bigList" :name="`${item.type}-${index}`" v-for="(product, index) in item.list"  :key="`${item.type}-${index}`">
          <a :href="product.url" class="pro-link">{{product.name}}</a>
        </MenuItem>
      </Submenu>
    </Menu>
  </div>
</template>

<script>
import {Menu, MenuItem, Submenu, Icon, MenuGroup} from 'iview'
import axios from 'axios'
export default {
  data () {
    return {
      slideList: []
    }
  },
  created () {
    axios.get('https://easy-mock.com/mock/5a2fd09f2704c108b1d12b23/example/api/producList')
      .then(res => {
        // console.log(res)
        this.slideList = res.data.slideList
      }).catch(err => {
        console.log(err)
      })
  },
  components: {
    Menu,
    MenuItem,
    Submenu,
    Icon,
    MenuGroup
  }
}
</script>

<style scoped>
.ivu-menu-vertical .ivu-menu-item-group-title {
  height: 24px;
  line-height: 24px;
}
.ivu-menu-vertical .ivu-menu-item, .ivu-menu-vertical .ivu-menu-submenu-title{
  padding: 3px 24px;
}
@media(max-width:768px) {
  .sider-l{
    display: none;
  }
}
</style>
