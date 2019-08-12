<template>
    <div class="login">
    <div class="content">
      <transition name="fade" mode="in-out">
        <section class="form_contianer">
          <div class="con">
            <el-form  status-icon label-width="6px" class="demo-ruleForm">
              <el-form-item  prop="uname">
                <el-input  placeholder="用户名" v-model="username"></el-input>
              </el-form-item>
              <el-form-item  prop="pass">
                <el-input type="password"  placeholder="密码" autocomplete="off" v-model="password"></el-input>
              </el-form-item>
              <el-form-item>
                <el-button type="primary" @click="dianji">登录</el-button>
              </el-form-item>
            </el-form>
            <div class="red">
              <p>温馨提示:</p>
              <p>未登陆过的新用户，自动注册</p>
              <p>注册过的用户可凭账号密码登录</p>
            </div>
          </div>
        </section>
      </transition>
    </div>
  </div>
</template>
<script>
import axios from "axios"
export default {
  data () {
    return {
       username:"",
       password:""
    }
  },
  methods:{
    
    dianji(){
      let data={
        username:this.username,
        password:this.password
      }
         axios.post("https://test.8boluo.com/index.php/index/wxapp.login/simple",data).then((res)=>{
           if(res.data.code==0){
              localStorage.setItem('user',JSON.stringify(res.data.data))
            this.$router.push("/name")
           }
         })
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  .login{
    position: fixed;
    width:100%;
    height:100%;
    background-color: #324057;
    .content{
      width:420px;
      margin: 0 auto;
      text-align: center;
      padding-top: 140px;
      // animation: fadeInDown 1s ;
      h1{
        font-size: 30px;
        color:#fff;
      }
      .con{
        background-color: #fff;
        border-radius: 5px;
        padding: 15px;
        margin-top: 50px;
        .el-form-item{
          padding: 10px;
          margin: 0;
          .el-input,.el-button{
            width:100%;
          }
        }
      }
      .red{
        width:100%;
        text-align: center;
        font-size: 12px;
        margin-top: 20px;
        p{
          color:#FF0000;
        }
      }
    }
  }


  .fade-enter-active, .fade-leave-active {
    transition: all 1s ;
  }
  .fade-enter, .fade-leave-active{
    transform: translate3d(0,-50px,0);
    opacity: 0;
  }
  .el-notification{
    i{
      font-size: 45px;
    }
    .el-notification__group{
      margin-left: 30px;
    }
  }
  .el-message{
    i{
      font-size: 15px;
    }
    .el-notification__group{
      margin-left: 30px;
    }
  }
</style>
