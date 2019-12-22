<template>
<!-- 最大容器 -->
<el-container>
  <!-- 左右布局 -->
  <el-aside>
    <layout-aside style="height:100vh;background-color:#353b4e;width:230px;"></layout-aside>
  </el-aside>
  <!-- 右侧容器 -->
  <el-container>
    <!-- 上下布局 -->
    <el-header>
      <layout-header></layout-header>
    </el-header>
    <el-main>
      <!-- 二级路由容器 -->
         <router-view></router-view>
    </el-main>
  </el-container>
</el-container>
</template>

<script>
export default {

}
</script>

<style>
.el-aside{
  width: 230px !important;
}
</style>
