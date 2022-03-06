<template>
  <div>
    
   <div class="swiper">

   </div>
    推荐歌单
   
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data () {
        return {
            list:[]
        }
    },
    created(){
        axios.get('http://localhost:3000/top/playlist/highquality').then(res =>{
            
            var lista = res.data.playlists.slice(0,12)  //表示输出多少个歌单
            
            this.list = lista
            console.log(lista);
        })
    }
}
</script>

<style>
.swiper{
    width: 100%;
    height: 200px;
    background: cornsilk;
}.musiclist_icon{
    width: 150px;
    height: 150px;
    margin: 30px;
    background: rgb(209, 221, 221);
    position: relative;
    border-radius: 20px;
    box-shadow: #d1d6d9ad 0px 0px 20px 0px;
}.musiclist{
    display: flex;
    width: 100%;
    flex-wrap: wrap;

}.imgs{
    width: 50px;
    height: 50px;
    
    transform: translate(10px,100%);
}.img_p{
        width: 75px;
    right: 0;
    float: right;
}
</style>