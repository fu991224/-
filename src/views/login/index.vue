<template>

  <div class="videocontainer">
    <el-card class="card">
      <div class="tubiao">
        <img src="../../assets/img/logo_index.png" alt="">
      </div>
      <el-form :model="loginForm" :rules="loginRules" ref='myForm'>
        <el-form-item prop="mobile">
          <el-input v-model="loginForm.mobile" placeholder="请输入手机号"></el-input>
        </el-form-item>
        <el-form-item prop="code">
          <el-input v-model="loginForm.code" placeholder="请输入验证码" style="width:60%"></el-input>
          <el-button plain style="float:right">发送验证码</el-button>
        </el-form-item>
        <el-form-item prop="check">
          <el-checkbox v-model="loginForm.check" style="colo=#ccc">请同意此霸王条款</el-checkbox>
        </el-form-item>
        <el-form-item>
          <el-button style="width:100%" type="primary" @click="submitLogin">登录</el-button>
        </el-form-item>
      </el-form>
    </el-card>
    <video class="fullscreenvideo" poster="__ROOT__/Themes/tdt/Asset/images/loginbg.jpg" id="bgvid" playsinline="" autoplay="" muted="" loop="">
        <source src="../../assets/img/saber.mp4" type="video/mp4">
    </video>
</div>
</template>

<script>
export default {
  methods: {
    submitLogin () {
      // 手动校验
      this.$refs.myForm.validate((isOK) => {
        if (isOK) {
          // 说明校验通过 调用登录接口
          // axios body参数 get参数地址参数 路由参数 查询参数
          // get参数 axios params
          this.$axios({
            url: '/authorizations', // 请求地址 axios 没有指定类型 默认get类型
            method: 'post', // post类型
            data: this.loginForm // body参数
          }).then(result => {
            // 只接受正确结果
            // 前端缓存
            window.localStorage.setItem('user-token', result.data.data.token)
            this.$router.push('/home')// 跳转到home
            console.log(result.data.data.token)
          }).catch(() => {
            this.$message({
              type: 'warning',
              message: '你填你妈呢？臭弟弟!'
            })
          })
        }
      })
    }
  },
  data () {
    return {
      loginForm: {
        mobile: '', // 手机号
        code: '', // 验证码
        check: false // 是否勾选 同意被坑
      },
      loginRules: {
        // 验证规则对象key（字段名）：value（规则=>[]）
        mobile: [{ required: true, message: '请输入手机号' }, {
          pattern: /^1[3456789]\d{9}$/, message: '手机号格式不正确'
        }],
        code: [{ required: true, message: '请输入验证码' }, {
          pattern: /^\d{6}$/, message: '验证码格式不正确'
        }],
        check: [{ validator: function (rule, value, callback) {
          // 自定义效验函数
          // rule 规则 没啥用
          // callback 是一个回调函数
          if (value) {
            callback()// 认为当前的规则校验通过了
          } else {
            // 认为没有勾选
            callback(new Error('？'))
          }
        } }]
      }
    }
  }
}
</script>

<style lang="less" scoped>
.el-card{
  border: 0px !important;
}
.card{
    width: 400px;
    height: 350px;
    margin-left:74% ;
    margin-top: 10%;
    background: rgba(25,29,34,.65);
    .tubiao{
      margin-bottom:30px;
    text-align: center;
    img{
      height: 44px;
    }
}
}

.fullscreenvideo {
    position: absolute;
    top: 50%;
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
}

.videocontainer{
    position: fixed;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: -100;
}

.videocontainer:before{
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    display: block;
    z-index: -1;
    top: 0;
    left: 0;

}
</style>
