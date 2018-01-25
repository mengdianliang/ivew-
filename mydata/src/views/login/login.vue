<template>
  <div id="login">
    <Avatar icon="person" class="ava" />
    <h3 class="title">用户登录</h3>
    <Form ref="formInline" :model="formInline" :rules="ruleInline" label-position="right">
      <FormItem prop="user">
        <Input type="text" size="large" v-model="formInline.user" placeholder="用户名">
          <Icon type="ios-person-outline" slot="prepend"></Icon>
        </Input>
      </FormItem>
      <FormItem prop="password">
        <Input type="password" size="large" v-model="formInline.password" placeholder="密码">
          <Icon type="ios-locked-outline" slot="prepend"></Icon>
        </Input>
      </FormItem>
      <FormItem prop="Checkbox" class="chk">
        <Checkbox v-model="single"><span class="color">记住账号</span></Checkbox>
      </FormItem>
      <FormItem>
        <Button type="primary" @click="handleSubmit('formInline')" size="large" long>登录</Button>
      </FormItem>
    </Form>
    <div class="to-admin">
      还没有账号？<router-link to='/admin'>去注册一个</router-link>
    </div>
  </div>
</template>

<script>
import {Avatar, Form, FormItem, Input, Icon, Checkbox, Button} from 'iview'
export default {
  data () {
    return {
      single: false,
      formInline: {
        user: '',
        password: ''
      },
      ruleInline: {
        user: [
          { required: true, message: '请填写用户名！', trigger: 'blur' }
        ],
        password: [
          { required: true, message: '请填写密码！', trigger: 'blur' },
          { type: 'string', min: 6, message: '密码长度至少为6！', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    handleSubmit (name) {
      this.$refs[name].validate((valid) => {
        if (valid) {
          this.$Message.success('登录成功!')
        } else {
          this.$Message.error('登录失败!')
        }
      })
    }
  },
  components: {
    Avatar,
    Form,
    FormItem,
    Input,
    Icon,
    Checkbox,
    Button
  }
}
</script>

<style scoped>
#login{
  max-width: 800px;
  width: 80%;
  margin: 20px auto;
  background: #ffffff;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 1px 1px 3px #dddddd;
}
.ava {
  width: 120px;
  height: 120px;
  font-size: 120px;
  line-height: 120px;
  margin: 0 auto;
  display: block;
}
.title{
  text-align: center;
  font-size: 24px;
  line-height: 80px;
  font-weight: normal;
}
.chk{
  text-align: center;
}
.color{
  color: #00ff00;
}
.to-admin{
  line-height: 24px;
  text-align: right;
}
</style>
