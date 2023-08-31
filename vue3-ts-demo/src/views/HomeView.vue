<template>
    <div class="home">
      <el-container>
        <el-header>
          <el-row :gutter="20">
            <el-col :span="4"><img src="../assets/logo.png" class="logo"/></el-col>
            <el-col :span="16"><h2>後台管理系統</h2></el-col>
            <el-col :span="4"><span class="logout">登出</span></el-col>
          </el-row>
        </el-header>
        <el-container>
          <el-aside width="200px">
            <el-menu
          active-text-color="#ffd04b"
          background-color="#545c64"
          class="el-menu-vertical-demo"
          default-active="2"
          text-color="#fff"
        >
          
          <el-menu-item index="2">
            <span>商品列表</span>
          </el-menu-item>
  
        </el-menu>
          </el-aside>
          <el-main>Main</el-main>
        </el-container>
      </el-container>
    </div>
  </template>
  
  <script lang="ts">
  import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
  import { defineComponent } from "vue";
  import{useRouter} from 'vue-router'; 
  export default defineComponent({
    name: "HomeView",
    setup(){
      const router=useRouter()
      console.log(router.getRoutes());
      // 展示側邊欄數據，返回的也是數組
      const list=router.getRoutes().filter(v=>v.meta.isShow) //若isShow是true才會顯示在畫面上
      console.log(list)
    },
    components: {},
  });
  </script>
  <style lang="scss" scoped>
  .el-header {
    height: 80px;
    background-color: #666;
    .logo {
      height: 80px;
    }
    h2,
    .logout {
      text-align: center;
      height: 80px;
      line-height: 80px;
      color: white;
    }
  }
  .el-aside {
    .el-menu{
      height: calc(100vh - 80px);
    }
  }
  </style>
  