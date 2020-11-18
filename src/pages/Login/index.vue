<!-- 登录 -->

<template>
  <div class="login-page">
    
    <div id="left">
    </div>
    <el-form
      :model="loginForm"
      status-icon
      :rules="rules"
      ref="loginForm"
      label-width="100px"
      class="demo-loginForm"
    >
    <h1 class="title">千峰管理系统</h1>
      <!-- prop校验 -->
      <el-form-item label="用户名" prop="username">
        <el-input
       
          type="text"
          v-model="loginForm.username"
          autocomplete="off"
        ></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input
        
          type="password"
          v-model="loginForm.password"
          autocomplete="off"
        ></el-input>
      </el-form-item>

      <el-form-item>
        <el-button type="success" @click="submitForm('loginForm')"
          >提交</el-button
        >
      </el-form-item>
     
    </el-form>
     <video src="./bg_video.d2d602a9.mp4" muted="muted" autoplay="autoplay" loop="loop" preload="auto" class="bg_video"></video>
  </div>

</template>
<script>
export default {
  data() {
    // jsDoc方式  注释
    /**
     * @param {Object} rule 就是一个表单验证对象
     * @param {string} value 输入值
     * @param {function} callback  效验通过不传参 不通过传参
     */

    var validateUsername = (rule, value, callback) => {
      // 用value 效验焦点
      // 普通
      // console.log(rule);
      // console.log(value);
      // if (value === "") {
      //   callback(new Error("请输入用户名"));
      // } else {
      //   if (this.loginForm.password !== "") {
      //     this.$refs.loginForm.validateField("password");
      //   }
      //   callback(); // 通过效验不用传
      // }

      // 高级点
      //用户名正则，4到16位（字母，数字，下划线，减号）
      // var uPattern = /^[a-zA-Z0-9_-]{4,16}$/;
      // if(!uPattern.test(value)){    //不通过
      //   callback('4到16位（字母，数字，下划线，减号）')
      // }else{
      //   callback() //通过不传参
      // }

      // 普通测试
       if(!value){    //不通过
        callback('4到16位（字母，数字，下划线，减号）')
      }else{
        callback() //通过不传参
      }
    };
    var validatePassword = (rule, value, callback) => {
      // if (value === "") {
      //   callback(new Error("请输入密码"));
      // } else if (value !== this.loginForm.username) {
      //   callback(new Error("两次输入密码不一致!"));
      // } else {
      //   callback();
      // }

      // 普通测试
      if(!value){    //不通过
        callback('请输入密码')
      }else{
        callback() //通过不传参
      }
    };
    return {
      //收集值
      loginForm: {
        username: "",
        password: "",
        // age: "",
      },
      rules: {
        username: [
          // 传入校验函数            触发的条件    失去焦点
          { validator: validateUsername, trigger: "blur" },
        ],
        password: [{ validator: validatePassword, trigger: "blur" }],
      },
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) { //本地效验通过 发送请求去效验用户名密码  写这里
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    },
  },
};
</script>

<style scoped>
/* 表单样式 */ 
    .el-form{
     width: 400px;
 }
 /* 表单输入框样式 */


 .el-input__inner {
    width: 83% ;
    
    width: 250px;
    transition: all .5s;
    height: 40px;
    line-height: 100%;
    overflow: hidden;
   
    border: .04761905rem solid #fff;
   
    padding-left: .95238095rem;
    
    

    /* 样式不起作用  1 类名 2 权重 !important  3 去掉scoped试一下 如果可以了就是scoped局部造成的 把这个写到全局*/
 }

.title{
      color: #fff;
        display: block;
    font-size: 2em;
    margin-block-start: 0.67em;
    margin-block-end: 0.67em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    font-weight: bold;
        color: #fff;
    margin-top: 100px;
    margin-bottom: 50px;
}

.el-form{
      position: relative;
    z-index: 9;
    width: 25rem;
    height: 30.47619048rem;
    position: absolute;
    top: 50%;
    left: 75%;
    transform: translate(-50%,-50%);
    border-radius: 11px;
    background: rgba(83,107,182,.46);
    background: rgba(0,0,0,.2);
    text-align: center;
    
     /* position: fixed; */
    /* width: 100%; */
    /* height: 100%; */
    /* overflow: hidden; */
    /* z-index: -100;  */

}
/* .el-form:before{
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    display: block;
    z-index: -1;
    top: 0;
    left: 0;
    background: rgba(25,29,34,.65);
} */


/* .bg_video{
  
    /* top: 50%;
    left: 50%;
    min-width: 100%;
    min-height: 100%;
    width: auto;
    height: auto;
    z-index: -100;
    -webkit-transform: translateX(-50%) translateY(-50%);
    transform: translateX(-50%) translateY(-50%);
    -webkit-transition: 1s opacity;
    transition: 1s opacity;
    opacity: .7;
        height: 100%;
    width: 100%;
    overflow: hidden; */
/* }  */

#left{
      width: 50%;
    height: 100%;
    background-image: url(./123.png);
    background-repeat: no-repeat;
    background-size: 50%;
    position: absolute;
    opacity: .9;
    background-position: 60% 65%;
}


</style>
