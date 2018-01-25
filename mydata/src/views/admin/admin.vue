<template>
  <div id="admin">
    <Avatar icon="person" class="ava" />
    <h3 class="title">用户注册</h3>
    <Form ref="formValidate" :model="formValidate" :rules="ruleValidate" :label-width="100">
      <FormItem label="Name" prop="name">
        <Input v-model="formValidate.name" placeholder="Enter your name" type="password" />
      </FormItem>
      <FormItem label="Password" prop="password">
        <Input v-model="formValidate.password" placeholder="Enter your password" type="password" />
      </FormItem>
      <FormItem label="rePassword" prop="repassword">
        <Input v-model="formValidate.repassword" placeholder="Enter your repassword" />
      </FormItem>
      <FormItem label="E-mail" prop="mail">
        <Input v-model="formValidate.mail" placeholder="Enter your e-mail" />
      </FormItem>
      <FormItem label="City" prop="city">
        <Select v-model="formValidate.city" placeholder="Select your city">
          <Option value="beijing">New York</Option>
          <Option value="shanghai">London</Option>
          <Option value="shenzhen">Sydney</Option>
        </Select>
      </FormItem>
      <FormItem label="Date">
        <Row>
          <Col span="11">
            <FormItem prop="date">
              <DatePicker type="date" placeholder="Select date" v-model="formValidate.date"></DatePicker>
            </FormItem>
          </Col>
          <Col span="2" style="text-align: center">-</Col>
          <Col span="11">
            <FormItem prop="time">
              <TimePicker type="time" placeholder="Select time" v-model="formValidate.time"></TimePicker>
            </FormItem>
          </Col>
        </Row>
      </FormItem>
      <FormItem label="Gender" prop="gender">
        <RadioGroup v-model="formValidate.gender">
          <Radio label="male">Male</Radio>
          <Radio label="female">Female</Radio>
        </RadioGroup>
      </FormItem>
      <FormItem label="Hobby" prop="interest">
        <CheckboxGroup v-model="formValidate.interest">
          <Checkbox label="Eat"></Checkbox>
          <Checkbox label="Sleep"></Checkbox>
          <Checkbox label="Run"></Checkbox>
          <Checkbox label="Movie"></Checkbox>
        </CheckboxGroup>
      </FormItem>
      <FormItem label="Desc" prop="desc">
        <Input v-model="formValidate.desc" type="textarea" :autosize="{minRows: 2,maxRows: 5}" placeholder="Enter something..."></Input>
      </FormItem>
      <FormItem>
        <Button type="primary" @click="handleSubmit('formValidate')">Submit</Button>
        <Button type="ghost" @click="handleReset('formValidate')" style="margin-left: 8px">Reset</Button>
      </FormItem>
    </Form>
    <div class="to-admin">
      已有账号？<router-link to='/login'>直接登录</router-link>
    </div>
  </div>
</template>

<script>
import {Avatar, Form, FormItem, Input, Icon, Checkbox, Button, Row, Col, CheckboxGroup, DatePicker, TimePicker, RadioGroup, Radio} from 'iview'
export default {
  data () {
    return {
      formValidate: {
        name: '',
        mail: '',
        city: '',
        gender: '',
        interest: [],
        date: '',
        time: '',
        desc: ''
      },
      ruleValidate: {
        name: [
          { required: true, message: 'The name cannot be empty', trigger: 'blur' }
        ],
        password: [
          { required: true, message: 'The password cannot be empty', trigger: 'blur' }
        ],
        repassword: [
          { required: true, message: 'The repassword cannot be empty', trigger: 'blur' }
        ],
        mail: [
          { required: true, message: 'Mailbox cannot be empty', trigger: 'blur' },
          { type: 'email', message: 'Incorrect email format', trigger: 'blur' }
        ],
        city: [
          { required: true, message: 'Please select the city', trigger: 'change' }
        ],
        gender: [
          { required: true, message: 'Please select gender', trigger: 'change' }
        ],
        interest: [
          { required: true, type: 'array', min: 1, message: 'Choose at least one hobby', trigger: 'change' },
          { type: 'array', max: 2, message: 'Choose two hobbies at best', trigger: 'change' }
        ],
        date: [
          { required: true, type: 'date', message: 'Please select the date', trigger: 'change' }
        ],
        time: [
          { required: true, type: 'date', message: 'Please select time', trigger: 'change' }
        ],
        desc: [
          { required: true, message: 'Please enter a personal introduction', trigger: 'blur' },
          { type: 'string', min: 20, message: 'Introduce no less than 20 words', trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    handleSubmit (name) {
      this.$refs[name].validate((valid) => {
        if (valid) {
          this.$Message.success('Success!')
        } else {
          this.$Message.error('Fail!')
        }
      })
    },
    handleReset (name) {
      this.$refs[name].resetFields()
    }
  },
  components: {
    Avatar,
    Form,
    FormItem,
    Input,
    Icon,
    Checkbox,
    Button,
    Row,
    Col,
    CheckboxGroup,
    DatePicker,
    TimePicker,
    RadioGroup,
    Radio
  }
}
</script>

<style scoped>
#admin{
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
