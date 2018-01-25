<template>
  <Row>
    <Col :xs="24" :sm="0" :md="0" :lg="0">
      <Menu mode="horizontal" theme="light">
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
          <MenuItem v-if="!item.bigList" :name="`${item.type}-${index}`" v-for="(product, index) in item.list" :key="`${item.type}-${index}`">
            <a :href="product.url" class="pro-link">{{product.name}}</a>
          </MenuItem>
        </Submenu>
      </Menu>
    </Col>
  </Row>
</template>

<script>
import {Menu, MenuItem, Submenu, MenuGroup, Icon, Row, Col} from 'iview'
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
    MenuGroup,
    Icon,
    Row,
    Col
  }
}
</script>

<style scoped>
.ivu-row{
  border-bottom: 1px solid #f1f1f1;
}
.pro-link{
  display: block;
  width: 100%;
}
@media(max-width:768px) {
  .sider-l{
    display: none;
  }
}
</style>
