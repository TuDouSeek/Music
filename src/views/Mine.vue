<template>
  <div class="home">
      <div style="display:flex;justify-content: space-between;">
          <div class="iconfont icon-caidan" style="font-size: 20px;padding: 10px;">

          </div>
          <div class="iconfont icon-lishibofang" style="font-size: 20px;padding: 10px;">
            
          </div>
      </div>
      <div class="a" style="background: white;
        height: 120px;
        width: 94%;
        border-radius: 10px;margin-top: 30px;
        box-shadow: #83838326 0 0 20px 10px;
        transform: translate(10px, 10px);">
        <div class="b" style="height: 50px;">
          <input type="text" class="tx_input" value="hello" >
          <img @click="to('Login')" style="width: 70px;height: 70px;border-radius: 50%;position: relative;margin: auto;left: 50%;transform: translate(-50%);background: blueviolet;top: -35px;" src="https://img0.baidu.com/it/u=1056811702,4111096278&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500" alt="" srcset="">
        </div>
        <div>
          <h3 style="text-align: center;">dawd</h3>
          <div>
            <ul style="display:flex;justify-content: center;">
              <li class="fsgzdj">4 关注</li>
              <li class="fsgzdj">2 粉丝</li>
              <li class="fsgzdj">Lv.8</li>
            </ul>
          </div>
        </div>
      </div>
      <div style="width:94%;height: 300px;mga;margin: auto;transform: translateY(10px);border-radius: 10px;box-shadow: 1px 1px 8px 0px #d3d3d380;">
      <div style="display:flex; flex-wrap: wrap;margin-top: 10px;">
        <router-link to="/" class="home_list iconfont "  style="border-radius: 10px 0px 0px 0px;"><div><div class=" home_lest_icon iconfont icon-bofang"></div><p>最近播放</p></div></router-link>
        
        <router-link to="/" class="home_list iconfont "><div class=" home_lest_icon iconfont icon-a-yinleshangdianbanquanyinle"></div><p>本地/下载</p></router-link>
        <router-link to="/" class="home_list iconfont "><div class=" home_lest_icon iconfont icon-qiyeyunpan"></div><p>云盘</p></router-link>
        <router-link to="/" class="home_list iconfont "  style="border-radius: 0px 10px 0px 0px;"><div><div class=" home_lest_icon iconfont icon-gouwu"></div><p>已购</p></div></router-link>
        <router-link to="/" class="home_list iconfont "  style="border-radius: 10px 0px 0px 0px;"><div><div class=" home_lest_icon iconfont icon-haoyou"></div><p>我的好友</p></div></router-link>
        <router-link to="/" class="home_list iconfont "><div class=" home_lest_icon iconfont icon-shoucang1"></div><p>收藏和赞</p></router-link>
        <router-link to="/" class="home_list iconfont "><div class=" home_lest_icon iconfont icon-bokeblogger3"></div><p>我的博客</p></router-link>
        <router-link to="/" class="home_list iconfont "  style="border-radius: 10px 0px 0px 0px;"><div><div class=" home_lest_icon iconfont icon-yinle1"></div><p>音乐罐子</p></div></router-link>
      </div>
      </div>
      <div class="mymusic_like">
        <div ><img src="https://img01.dmhmusic.com/0103/M00/A3/CE/ChR45WHer-KAA1UBAAFNEjG4Ft8724.jpg@w_200,h_200" style="width:70px;padding:20px" alt="" srcset=""></div>
        <div class="mymusiclink_text">
          <h5>我喜欢的音乐</h5>
          <p>115首</p>
        </div>
        <div class="mymusiclink_moshi">
          <div class="mymusiclink_moshi_xd iconfont icon-a-yinleshangdianbanquanyinle" ></div>
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

import Tabbar from '@/components/Tabbar.vue'
export default {
  name: 'Home',
  components: {
    Tabbar
  },
  methods:{
    to (name) {
      if (name === this.name) return false
      this.$router.replace({
        name
      })
    }
  }
}
</script>

<style scoped>
.mymusiclink_moshi_xd{
  width:90px;height:30px;transform: translateY(100%);border: 1px solid rgb(141, 141, 141);border-radius: 15px;
}
.tx_input{
      box-shadow: rgb(131 131 131 / 15%) 0px 0px 20px 3px;
    outline: none;
    border: none;
    transform: translate(-50%);
    top: -50%;
    width: 70px;
    /* list-style: none; */
    border-radius: 8px;
    height: 16px;
    left: 50%;
    position: absolute;
    float: revert;
    color: aqua;
    text-align: center;
}
.fsgzdj{
  width: 50px;
  float: left;
  font-size: 10px;
  color: rgb(163, 172, 172);
}.home_list{
  width: 25%;
  height: 125px;
     background: rgb(255 255 255);
}.home_lest_icon{
  font-size: 40px;
  text-align: center;
  line-height: 100px;
  color: rgba(196, 4, 4, 0.782);
}.home_lest,p{
  text-align: center;
}.mymusic_like{
  transform: translate(0px, 25px);
  display: flex;
  height: 110px;
  width: 94%;
  margin: auto;
  box-shadow: rgb(131 131 131 / 15%) 0px 0px 20px 3px;
  border-radius: 10px;
}.mymusiclink_text{
  display: flex;
  width: 40%;
  height: 110px;
  align-items: flex-start;
  flex-direction: column;
  justify-content: center;
}.mymusiclink_moshi{
  width: 30%;
  height: 110px;
}
</style>
