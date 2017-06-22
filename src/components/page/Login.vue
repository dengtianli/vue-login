<template>
  <div calss="login-wrap">
    <div class="vl-title">vue 登录系统页面</div>
    <div class="vl-login">
      <el-form  :model="form" ref="form" :rules="rules" label-width="0px"  class="demo-ruleForm">
        <el-form-item prop="name">
          <el-input v-model="form.name" placeholder="请填写用户名"></el-input>
        </el-form-item>
        <el-form-item  prop="password">
          <el-input type="password" v-model="form.password" auto-complete="off" placeholder="请填写密码"></el-input>
        </el-form-item>
        <div class="login-btn">
          <el-button type="primary" @click="submitForm('form')">登录</el-button>
        </div>
      </el-form>
    </div>
  </div>
</template>
<script>
  export default {
    data: function () {
      return {
        form: {
          name: '',
          password: ''
        },
        rules: {
          password: [
            { required: true, message: '请输入密码', trigger: 'blur' }
          ],
          name: [
            { required: true, message: '请输入用户名', trigger: 'blur' },
            { min: 1, max: 12, message: '长度在 1 到 12 个字符', trigger: 'blur' }
          ]
        }
      }
    },
    methods: {
      submitForm (form) {
        this.$refs[form].validate((valid) => {
          if (valid) {
            localStorage.setItem('vl_name', this.form.name)
            this.$router.push('/dashboard')
          } else {
            console.log('error submit!!')
            return false
          }
        })
      }
    }
  }
</script>

<style scoped>
    .login-wrap{
        position: relative;
        width:100%;
        height:100%;
    }
    .vl-title{
        position: absolute;
        top:50%;
        width:100%;
        margin-top: -230px;
        text-align: center;
        font-size:30px;
        color: #fff;

    }
    .vl-login{
        position: absolute;
        left:50%;
        top:50%;
        width:300px;
        height:160px;
        margin:-150px 0 0 -190px;
        padding:40px;
        border-radius: 5px;
        background: #fff;
    }
    .login-btn{
        text-align: center;
    }
    .login-btn button{
        width:100%;
        height:36px;
    }
</style>