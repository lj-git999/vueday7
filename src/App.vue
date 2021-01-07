<template>
  <div id="app">
    <h3>百知教育信息管理系统</h3>
    <router-link to="/first">用户管理</router-link>
    <router-link to="/second">学生管理</router-link>
    <router-link to="/third">查看信息</router-link>

    <router-view></router-view>
  </div>
</template>

<script>
import First from "./components/First";
import Second from "./components/Second";
import Third from "./components/Third";

export default {
  name: 'App',
  components:{
    first:First,
    second:Second,
    third:Third
  }
}
</script>

<style>

</style>
