<template>
  <el-container>
    <el-header>Welcome To Todo List</el-header>
    <el-main><Login/></el-main>
  </el-container>
</template>

<script>
    import Login from "./Login";
    export default {
        name: "Home",
      components: {Login}
    }
</script>

<style>
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #303133;
    font-size: large;

    text-align: center;
    line-height: 60px;
  }

  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 500px;
  }

</style>
