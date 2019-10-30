<template>
  <div class="login_form">
    <el-form label-position="top" label-width="80px" :model="form" ref="form">
      <el-form-item>
        <el-input placeholder="用户名/手机" v-model="form.username"></el-input>
      </el-form-item>
      <el-form-item>
        <el-input placeholder="密码" v-model="form.password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" style="width:100%;" @click="submitLogin">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      form: {
        username: "15575428880",
        password: "1234567899"
      }
    };
  },
  methods: {
    // submitLogin() {
    //   this.$store.dispatch("user/setUser",this.form).then(res => {
    //     // console.log(res)
    //     this.$router.push('/')
    //     this.$message.success('登入成功')
    //   });
    // },          //有点问提
    submitLogin(){
      this.$axios.post("/accounts/login",this.form)
      .then(res=>{
        if(res.data.token){
          this.$router.push('/')
          this.$message.success('登入成功')
        }else {
          this.$message.success('登入失败')
        }
      })
    }
  }
}
</script>

<style lang="less" scoped>
.login_form {
  padding: 20px;
}
</style>