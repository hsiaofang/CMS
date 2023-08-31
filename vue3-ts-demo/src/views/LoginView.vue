<template>
    <div class="login-box">
        <el-form
    ref="ruleFormRef"
    :model="ruleForm"
    status-icon
    :rules="rules"
    label-width="60px"
    class="demo-ruleForm"
  >
  <h2>後台管理系統</h2>
    <el-form-item label="帳號" prop="username">
      <el-input v-model="ruleForm.username"  autocomplete="off" />
    </el-form-item>
    <el-form-item label="密碼" prop="password">
      <el-input
        v-model="ruleForm.checkPass"
        type="password"
        autocomplete="off"
      />
    </el-form-item>
   
    <el-form-item>
      <el-button class="loginBtn" type="primary" @click="submitForm(ruleFormRef)"
        >登入</el-button
      >
      <el-button class="loginBtn" @click="resetForm(ruleFormRef)">重置</el-button>
    </el-form-item>
  </el-form>
    </div>
</template>

<script lang="ts">
import { defineComponent,reactive,toRef, toRefs } from 'vue'

export default defineComponent({
    setup () {
        const data=reactive({
            ruleForm:{
                username:"",
                password:""
            },
            rules:{
                username:[
                    {
                        required: true,
                        message: "請輸入帳號",
                        trigger: "blur",
                    },
                    {
                        min: 3,
                        max: 10,
                        message: "帳號長度在3到10之間 ",
                        trigger: "blur",
                    },
                ],
                password:[
                    {
                        required: true,
                        message: "請輸入帳號",
                        trigger: "blur",
                    },
                    {
                        min: 3,
                        max: 5,
                        message: "帳號長度在3到10之間",
                        trigger: "blur",
                    },
                ],

            }
        })
        
        // 將data解構
        return {...toRefs(data)};
    }
})
</script>

<!-- css預處理器 -->
<style lang='scss' scoped>
    .login-box {
        width: 100%;
        height: 100%;
        background:url("../assets/bg.jpg");
        padding: 1px; //父元素會受到子元素影響
        text-align: center ;
        .demo-ruleForm{
            width:500px;
            margin: 200px auto;
            background-color: white;
            padding: 40px;
            border-radius: 20px;
        }
        .loginBtn{
            width: 48%;
        }
        h2{
            margin-bottom: 5px;
        }
    } 
</style>