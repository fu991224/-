<template>
  <el-row class="layout-header" type="flex" align="middle">
    <!-- 先定义一行 -->
    <el-col  class="left" :span="12">
      <i class="el-icon-s-fold"></i>
      <span>江苏传智播客教育科技股份有眼公司</span>
    </el-col>
    <el-col :span="12" class="right">
      <el-row type="flex" justify="end" align="middle">
        <img src="../../assets/img/touxiang.png" alt="">
        <!-- 下拉菜单 -->
        <el-dropdown>
          <!-- 匿名插槽 下拉菜单显示的元素内容 -->
          <span>ko no dio da！</span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>个人信息</el-dropdown-item>
            <el-dropdown-item>git地址</el-dropdown-item>
            <el-dropdown-item>退出</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </el-row>
    </el-col>
  </el-row>
</template>

<script>
export default {

}
</script>

<style lang='less' scoped>
.layout-header{
  .left{
    font-size: 20px;
    span{
      color: #2c3e50;
      font-size: 16px;
      margin-left: 4px;
    }
  }
  .right {
    img{
      width: 40px;
      height: 40px;
      border-radius: 50%;
      margin-right:5px ;
    }
  }
}
</style>
