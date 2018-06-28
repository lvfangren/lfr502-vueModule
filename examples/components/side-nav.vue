<template lang="html">
  <!-- <div class="side-nav">
    <div class="group-container" v-for="titles in title">
      <p class="side-nav-title">{{titles}}</p>
      <div class="side-nav-items" v-for="nav in navTitle[titles]" v-if="nav.desc">
        {{nav.length}}
        <router-link :to="{ name: 'nav.name'}" v-if="nav.name" :class="$route.name===nav.name ? 'active' : ''">{{nav.desc}}</router-link>
        <p class="side-nav-group" v-else>{{nav.desc}}</p>
        <div class="" v-for="item in nav.items">
          <router-link class="slid-nav-component" :to="{ name: 'item.name'}" v-if="item.name" :class="$route.name===item.name ? 'active' : ''">{{item.desc}}</router-link>
        </div>
      </div>
    </div>
  </div> -->
  <div class="side-nav">
    <div v-for="title in (Object.keys(data))" class="group-container">
      <p class="side-nav-title">{{title}}</p>
      <div class="side-nav-items" v-for="nav in data[title]" v-if="nav.desc">
        <router-link :class="$route.name===nav.name ? 'active' : ''" v-if="nav.name" :to="{name: nav.name}">{{nav.desc}}</router-link>
        <p v-else class="side-nav-group">{{nav.desc}}</p>
        <div v-for="item in nav.items">
          <router-link :to="{name: item.name}" :class="$route.name===item.name ? 'active' : ''" class="slid-nav-component">{{item.desc}}</router-link>
        </div>
      </div>
    </div>
  </div>

</template>

<script>
import data from '../lvModule.json'
export default {
    // data(){
    //   return{
    //     title:[],
    //     navTitle:data
    //   }
    // },
    data(){
      return{
        data:data
      }
    },
    created(){
      this.title=Object.keys(data);
      Object.keys(data).forEach((header)=>{
        console.log(data[header])
      })
    },
    computed:{

    }

}
</script>

<style lang="less" scoped>
  .side-nav{
      display: inline-block;
      margin: 32px 0;
      padding: 0;
      color: #3F536E;
      background-color: #fff;
      z-index: 99;
      .group-container{
        margin-bottom: 32px;
      }
      .side-nav-title{
        padding: 0 24px 8px;
        color: #8DABC4;
        font-size: 12px;
        font-weight: bold;
        letter-spacing: 1px;
        text-transform: uppercase;
      }
      .side-nav-items{
        font-size: 14px;
        font-weight: normal;
        line-height: 1.8;
        a{
          display: block;
          position: relative;
          padding: 8px 24px;
          color: #3F536E;
          font-weight: normal;
          line-height: 1.5;
          cursor: pointer;
        }
        .side-nav-group{
          display: block;
          position: relative;
          padding: 6px 0 6px 24px;
          color: #2C405A;
          font-weight: bold;
        }
        .slid-nav-component{
          display: block;
          position: relative;
          padding: 6px 24px 6px 32px;
          color: #616367;
          font-size: 14px;
        }
        .active{
          color: #3FAAF5;
        }
      }
    }
</style>
