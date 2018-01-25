<template>
  <div class="board">
    <Row v-if="boardList.length">
      <Col :xs="24" :sm="12" :md="8" :lg="6" v-for='item in boardList' :key="item.id">
        <div class="card">
          <Card>
            <div slot="title">
              <img :src="item.img"/>
            </div>
            <div class="title">
              <a :href="item.url" target="_blank">{{ item.title }}</a>
              <span class="star-color">
                <Icon type="ios-star" v-for="n in 4" :key="n"></Icon><Icon type="ios-star" v-if="item.star >= 9.5"></Icon><Icon type="ios-star-half" v-else></Icon>
                {{ item.star }}
              </span>
            </div>
            <div class="desc">
              {{item.description}}
              <Button type="primary" class="cli">查看详情</Button>
            </div>
          </Card>
        </div>
      </Col>
    </Row>
  </div>
</template>

<script>
import {Row, Col, Card, Icon, Button} from 'iview'
import axios from 'axios'
export default {
  data () {
    return {
      boardList: []
    }
  },
  created () {
    axios.get('https://easy-mock.com/mock/5a2fd09f2704c108b1d12b23/example/api/boardList')
      .then(res => {
        // console.log(res)
        this.boardList = res.data.boardList
      }).catch(err => {
        console.log(err)
      })
  },
  components: {
    Row,
    Col,
    Card,
    Icon,
    Button
  }
}
</script>

<style scoped>
.board{
  padding: 20px;
  background: #f1f1f1;
}
.card{
  padding: 20px;
}
img {
  display: block;
  width: 100%;
}
.title{
  overflow: hidden;
  line-height: 30px;
}
.star-color{
  float: right;
  color: #ffac2d;
}
.desc{
  height: 80px;
  line-height: 40px;
  overflow: hidden;
  text-indent: 20px;
}
.cli{
  float: right;
}
</style>
