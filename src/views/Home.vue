<template>
  <div class="home">
    <div class="back">
      <div class="herder">
        <ul style="display:flex;justify-content: space-between;">
          <li class=" iconfont icon-caidan1 "></li>
          <div>
            <input class="seek " type="text" value="你">
          </div>
          <li class=" iconfont icon-maikefeng"></li>
        </ul>
      </div>
      <div class="viewpager">
        <ul style="display: -webkit-box;overflow: hidden;">
          <li><img class="viewpager-img" src="../assets/1.jpg" alt=""></li>
          <li><img class="viewpager-img" src="../assets/2.jpg" alt=""></li>
          <li><img class="viewpager-img" src="../assets/3.jpg" alt=""></li>
          <li><img class="viewpager-img" src="../assets/4.jpg" alt=""></li>
        </ul>
      </div>
    <div style="margin-top: 24px;">
      <ul class="inco_ul">
        <li><div class="iconfont icon-tuijianbaobiao"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
        <li><div class="iconfont icon-shouyinji"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
        <li><div class="iconfont icon-gedan"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
        <li><div class="iconfont icon-paihang"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
        <li><div class="iconfont icon-15"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
        <li><div class="iconfont icon-iconfont_guangpan"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
        <li><div class="iconfont icon-diantai"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
        <li><div class="iconfont icon-diantai"></div><span><router-link class="Text" to="/nominate_Playlist">每日推荐</router-link></span></li>
          <li><div class="iconfont icon-diantai"></div></li>
        
      </ul>
    </div>
    </div>
    <div style="margin-top: 55px;">
      <div >
        <div class="nominate_music">
          <div>
            <h3>推荐歌单</h3>
          </div>
          <div class="more"  @click="to('More')">
            <h5>更多></h5>
          </div>
        </div>
        <div style="width: 100%;height: 220px; background-image: linear-gradient(rgb(255, 255, 255),#e5eeef);border-radius: 10px;" >
            <ul class="more_playlist_viewpager" scroll="no" style="margin-top: 10px;">
              <li class="mpv_ul_li" v-for="(index,item) in dataPlaylist" :key="item" @click="to('More')">
                <img style="width: 110px;height: 110px;" :src="index.picUrl" alt="" srcset="">
                <p>{{index.name}}</p>
              </li>
              
            </ul>
            
        </div>
        <div class="music_list">
          <ul class="music_list_ul">
            <li>1</li>
            <li>2</li>
            <li>3</li>
            <li>4</li>
          </ul>
        </div>

      </div>
    </div>
    <Tabbar/>
    <!-- <router-link to="/one">home</router-link>
    <router-link to="/about">about</router-link>
    <router-view></router-view> -->
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Nominate from './Playlist/nominate_Playlist.vue'
import axios from 'axios'
import Tabbar from '@/components/Tabbar.vue'
export default {
  name: 'Home',
  data () {
    return {
      dataPlaylist:[]
    }
  },
  components: {
    HelloWorld,Nominate,Tabbar
  },
  computed:{
    name () {
      return this.$route.name
    }
  },
  methods:{
    a (){
    
      console.log('ok');
    },
    to (name) {
      if (name === this.name) return false
      this.$router.replace({
        name
      })
    }
  },
  created(){  
       axios.get('/admin/recommend/resource?phone=13547975280&password=13547975280Gxl')
       .then(data => {
           console.log('请求成功');
          //  const app = data.data.data.dailySongs.map(item=>({
          //      name: item.name,
          //      id: item.id,
          //      al:item.al,
          //      al:{
          //          name:item.al.name,
          //          picUrl:item.al.picUrl,
          //      }
          //  }))
            this.dataPlaylist=data.data.recommend
           console.log(data.data.recommend);
    //     //    
    //     //    console.log(data.data.data.dailySongs[1].name);
       })   
   }
  }

</script>

<style scoped>
@import url(../PublicCss/public.css);
@import url('//at.alicdn.com/t/font_2872427_5mtqsyys95d.css');
.back{
  z-index: -10;
  margin: 0;
  padding: 0;
  width: 100%;
  height: 300px;
  background-image: linear-gradient(#e5eeef,rgb(255, 255, 255));
}.herder{
  width: 100%;
  height: 80px;

}.Text{
  color: black;
}.music_list{
  width: 100%;
  height: 200px;
  background: #f41392;
  margin-top: 10px;
}.music_list_ul{
  float: left;
  width: 80%;
  height: 200px;
  background: #FDF5F5;
}
.seek{
  border-radius: 20px;
  border: none;
  height: 36px;
  width: 280px;
  margin-top: 6%;
  text-align: center;
  color: antiquewhite;
}.viewpager{
  width: 100%;
  height: 155px;
}.viewpager>ul{
  width: 90%;
  height: 100%;
  margin: auto;
  border-radius: 22px;
}.viewpager-img{
  height: 155px;
  max-width:100%;border-radius: 22px;position: relative;float: left;overflow: hidden;
}.inco_ul{
  height: 90px;
  display: -webkit-box;
  overflow: scroll;
}.inco_ul::-webkit-scrollbar{
  display: none;
}.inco_ul>li{
  width: 20%;
  height: 90px;
  text-align: center;
}.inco_ul>li>div{
  color: #eb4e46;
  background-image: -webkit-linear-gradient(90deg, #abeaf7, #f41392);
  width: 63%;
  height: 52%;
  text-align: center;
  float: left;
  position: relative;
  font-size: 28px;
  background: #FDF5F5;
  border-radius: 50%;
  line-height: 156%;
  right: 50%;
  transform: translate(-50%);
}.inco_ul>li>span{
  display: block;
  width: 50px;
  margin: auto;
  display: table;
  font-size: 10px;
  position: relative;
}.rotlink{
  position: relative;
  width: 50px;
  height: 50px;
}.nominate_music{
  margin-top: 10px;
  display: flex;
  justify-content: space-between;
  line-height: 25px;
}.nominate_musi,.more{
  width: 70px;
  height: 25px;
  border-radius: 30px;
  border: 1px solid rgb(255, 162, 162);
  text-align: center;
  line-height: 25px;
}.mpv_ul_li{
  float: left;
  width: 80px;
  height: 160px;
  padding: 22px;
  text-align: center;
  font-size: 10px;

}.mpv_ul_li>img{
  border-radius: 10px;
}
.more_playlist_viewpager{
  display: flex;
  overflow-x: scroll;
  overflow-y: hidden;
 
}.more_playlist_viewpager::-webkit-scrollbar{
  display: none;
}
.icon-caidan1,.icon-maikefeng{
  line-height: 70px;
  font-size: 30px;
  
}
</style>
