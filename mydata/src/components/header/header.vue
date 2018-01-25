<template>
  <Header class="header">
    <Row>
      <Col :xs="20" :sm="4" :md="4" :lg="4">
        <div class="layout-logo">
            <router-link to="/home" />
          </div>
      </Col>
      <Col :xs="0" :sm="16" :md="12" :lg="12">
        <Menu mode="horizontal" theme="light" active-name="home">
          <div class="layout-nav">
            <MenuItem name="home">
              <router-link to='/home'>
                <Icon type="home"></Icon>
                首页
              </router-link>
            </MenuItem>
            <MenuItem name="about">
              <router-link to='/about'>
                <Icon type="ios-keypad"></Icon>
                关于
              </router-link>
            </MenuItem>
          </div>
        </Menu>
      </Col>
      <Col :xs="0" :sm="0" :md="8" :lg="8">
        <Menu mode="horizontal" theme="light" active-name="1">
          <div class="layout-r-nav">
            <ButtonGroup>
              <Button type="ghost">
                <router-link to='/login'>
                  <Icon type="log-in"></Icon>
                  登录
                </router-link>
              </Button>
              <Button type="ghost">
                <router-link to='/admin'>
                  <Icon type="person"></Icon>
                  注册
                </router-link>
              </Button>
            </ButtonGroup>
          </div>
        </Menu>
      </Col>
      <Col :xs="4" :sm="4" :md="0" :lg="0">
        <Dropdown placement="bottom-end">
          <a href="javascript:void(0)" :style="{display: 'inline-block', width: '40px', color: '#666666'}">
              <Icon type="navicon-round" size="30"></Icon>
          </a>
          <DropdownMenu slot="list">
            <DropdownItem>
              <router-link to='/login'>
                <Icon type="log-in"></Icon>
                登录
              </router-link>
            </DropdownItem>
            <DropdownItem>
              <router-link to='/admin'>
                <Icon type="person"></Icon>
                注册
              </router-link>
            </DropdownItem>
          </DropdownMenu>
          <DropdownMenu slot="list" class="the">
            <DropdownItem divided>
              <router-link to='/home'>
                <Icon type="home"></Icon>
                首页
              </router-link>
            </DropdownItem>
            <DropdownItem>
              <router-link to='/about'>
                <Icon type="ios-keypad"></Icon>
                关于
              </router-link>
            </DropdownItem>
          </DropdownMenu>
      </Dropdown>
      </Col>
    </Row>
  </Header>
</template>

<script>
import {Layout, Menu, MenuItem, Header, Icon, Row, Col, Dropdown, DropdownMenu, DropdownItem, ButtonGroup, Button} from 'iview'
export default {
  components: {
    Layout,
    Menu,
    MenuItem,
    Header,
    Icon,
    Row,
    Col,
    Dropdown,
    DropdownMenu,
    DropdownItem,
    ButtonGroup,
    Button
  }
}
</script>

<style scoped>
.header{
  position: fixed;
  width: 100%;
  z-index: 9999;
  box-shadow: 0 1px 3px #f1f1f1;
}
.ivu-layout-header{
  background: #ffffff;
}
.layout-logo{
  width: 100px;
  height: 60px;
  border-radius: 3px;
  background: url('../../assets/logo.png');
  background-size: 100%;
  background-position: 0 10px;
  margin: 0 auto;
}
.layout-logo a{
  display: block;
  height: 60px;
}
.ivu-menu-horizontal{
  height: auto;
}
.layout-nav{
  height: 100%;
  float: left;
  margin-left: 20px;
}
.layout-r-nav{
  height: 100%;
  float: right;
}
.ivu-dropdown{
  text-align: center;
  float: right;
}
.ivu-dropdown-rel{
  width: 100%;
}
.ivu-dropdown-item{
  padding: 7px 40px;
}
.the{
  display: none;
}
@media(max-width:768px) {
  .the{
    display: block;
  }
}
</style>
