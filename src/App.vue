<template>
  <div class="about">
    <el-container>
      <el-header class="Header">
      </el-header>
      <el-container>
        <el-aside width="200px"  class="aside" @click="to()" style="">
          <ul class="ul">
            <li class="ul_li"><router-link class="routerlink" to="/FindMusic"><li class="iconfont icon-icon"> 发现音乐</li></router-link></li>
            <li class="ul_li"><router-link class="routerlink" to="/RecommendMsicList"><li class="iconfont icon-tuijianbaobiao"> 推荐歌曲</li></router-link></li>
            <li class="ul_li"><router-link class="routerlink" to="/NewestMusicList"><li class="iconfont icon-bofangliebiao"> 最新歌单</li></router-link></li>
            <li class="ul_li"><router-link class="routerlink" to="/NewestMV"><li class="iconfont icon-bofangMV"> 最新MV</li></router-link></li>
          </ul>
        </el-aside>
        <el-main class="main">
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
       
  </div>
</template>
<script>
import Music from './components/music.vue'
import FindMusic from './views/FindMusic.vue'
export default {
   components:{
      FindMusic,Music
    },
  methods:{
   
  },
  created () {
   
  }
}
</script>
<style>
@import url(//at.alicdn.com/t/font_2872427_5mtqsyys95d.css);
.ul{
  list-style: none;
  padding: 0;
  width: 90%;
  height: 200px;
  box-shadow: #d1d6d9ad 0px 0px 20px 0px;
  margin: 0;
  border-radius: 20px;
 margin: 5%;
}.routerlink{
  height: 50px;
  color: black;
  text-decoration: none;
  line-height: 50px;
  text-align: center;
}
.about{
  height: 98vh;
  
}
.Header{
  background: cadetblue;
}.iconfont:hover{
  color: aqua;
}

.el-container{
  height: 100%;
}
.main{
  
  border-radius: 20px;
  box-shadow: #d1d6d9ad 0px 0px 20px 0px;
}.element::-webkit-scrollbar,.main{ 
width: 0 !important 
}
body::-webkit-scrollbar {
    display: none;
}
.main::-webkit-scrollbar {
    display: none;
}
</style>
