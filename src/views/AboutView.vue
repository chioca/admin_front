<template>
    <el-button type="primary" @click="handle_login">测试登录</el-button>
    <el-button type="success" @click="handle_user">测试请求</el-button>


</template>

<script  setup>
import request from '@/util/request';
const handle_login = async()=>{
  let result = await request.get('user/jwt_test');
  let data = result.data;
  if(data.code==200)
  {
    const token = data.token
    console.log("登录成功token="+token)
    window.sessionStorage.setItem('token',token)

  }else {
    console.log("请求出错")
  } 
}
const handle_user = async()=>{
  const result = await request.get('user/test')
  let data = result.data
  if(data.code == 200){
    console.log("用户信息列表",data.data)
  }else {
    console.log("请求出错")
  } 
}
</script>
