<template>

  <div class="videocontainer">
    <el-card class="card">
      <div class="tubiao">
        <img src="../../assets/img/logo_index.png" alt="">
      </div>
      <el-form>
        <el-form-item>
          <el-input placeholder="请输入手机号"></el-input>
        </el-form-item>
        <el-form-item>
          <el-input placeholder="请输入验证码" style="width:60%"></el-input>
          <el-button plain style="float:right">发送验证码</el-button>
        </el-form-item>
        <el-form-item>
          <el-checkbox style="colo=#ccc">请同意此霸王条款</el-checkbox>
        </el-form-item>
        <el-form-item>
          <el-button style="width:100%" type="primary">登录</el-button>
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

}
</script>

<style lang="less" scoped>
.card{
    width: 400px;
    height: 350px;
    margin-left:74% ;
    margin-top: 10%;
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
    /* background: rgba(25,29,34,.65); */
}
</style>
