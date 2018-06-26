<template>
  <div id="app">
    <mainSkeleton v-if="!init"></mainSkeleton>
    <div v-else>
      <mainHeader></mainHeader>
      <div class="container" v-if="!isIndex">
        <sideNav class="nav"></sideNav>
        <router-view class="view"></router-view>
      </div>
      <router-view class="page" v-else></router-view>
      <mainFooter v-if="!isIndex"></mainFooter>
    </div>
  </div>
</template>

<script>
import mainHeader from './components/header.vue'
import mainFooter from './components/footer.vue'
// 侧面导航件
import sideNav from './components/side-nav.vue'
// 基本骨架件
import mainSkeleton from './main.skeleton.vue'
export default {
  name: 'App',
  data(){
    return{
      init:false,
      isIndex:true
    }
  },
  components:{
    mainHeader,
    mainFooter,
    sideNav,
    mainSkeleton
  },
  watch:{
    $route(){
      this.isIndex=this.$route.name==="index"
    }
  },
  mounted () {
      //  这里模拟数据请求
      setTimeout(() => {
        this.init = true
      }, 250)
    }
}
</script>

<style lang="less">
  @import "./assets/less/index";
  .container {
  margin: 48px auto;
  width: 90%;
  background-color: #fff;
  box-shadow: 0 4px 30px 0 rgba(223, 225, 230, 0.5);
  .nav {
    float: left;
    width: 210px;
  }
  .view {
    float: left;
    width: calc(~'100% - 215px');
    padding: 32px 48px 48px;
    box-sizing: border-box;
  }
  }
  .container:after {
  content: "";
  clear: both;
  display: block;
  }
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
