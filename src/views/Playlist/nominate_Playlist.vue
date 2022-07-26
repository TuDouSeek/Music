<template>
      <div>
          <div>
              <router-link to="/" class="iconfont icon-shouyinji"></router-link>
          </div>
          <div class="back">

          </div>
          <div class="play">

          </div>
          <ul>
              <li class="list_li" v-for="(item) in dataSoures" :key="item.id" style="display:flex;align-items: center;padding: 5px;">
                  <div class="list_img">
                      <img style="width:40px;border-radius: 10px;" :src="item.al.picUrl" alt="" srcset="">
                  </div>
                  <div>
                      <h5>{{item.name}} <span>{{ad.mane}}</span></h5>
                      <span style="font-size: 10px;color:red">{{item.ar}}</span>
                  </div>
              </li>
          </ul>
      </div>
  
</template>

<script>
import axios from'axios'
export default {
    data () {
        return {
            dataSoures:[],
            ad:''
        }
    },
    mounted(){
        // var url ="'13547975280Gxl'"
        // const promise = new Promise(function a(resolve,reject){
        //     axios.get('/admin/recommend/songs?phone='+'13547975280'+'&password=' ,+url)
        //     .then(data =>{resolve(data)})
        // })
        // promise.then(function(value){
        //     console.log(value);
        // })

        
    },
   
   created(url){  
       axios.get('/admin/recommend/songs?phone='+'13547975280'+'&password=' ,+'13547975280Gxl')
       .then(data => {
           
           console.log('请求成功');
           const app = data.data.data.dailySongs.map(item=>({
               name: item.name,
               id: item.id,
               al:item.al,
               al:{
                   name:item.al.name,
                   picUrl:item.al.picUrl,
               },
               //获取歌手信息 
               ar:item.ar.map(arItem=>arItem.name).join('/')
           }))
           this.dataSoures=app
          
           console.log(app[0]);
    //     //    
            
    //     //    console.log(data.data.data.dailySongs[1].name);
       })   
       
   },
   
   
}
</script>

<style>

.back{
    
    width: 100%;
    height: 180px;
}.play{
    width: 100%;
    height: 80px;
}

.list_li>.list_img{
    padding: 10px 10px 0px 10px;

    
}
</style>