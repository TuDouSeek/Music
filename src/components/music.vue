<template>
  <div>
      
      <div class="Views">
          <div class="listMusic">
              
              <div class="listMusiczh" v-for="item in musicName" :key="item.id">
               <span class="playInco iconfont icon-tuijianbaobiao" @click="plays(item.id),play,textMusic(item.id)"></span>
                 <p class="text">{{item.name}}</p>
                    
                  <img class="imgsIcon" :src="item.al.picUrl" alt="" srcset="">
                <audio src=""></audio>
              </div>
          </div>
          <div class="MusicView">
              <p></p>
                <span>
                    <p>{{musicText}}</p>
                </span>
              <audio
                    class="audioMusic"
                    autoplay
                    controls
                    :src="musicUrl"
                    ref="audio"
                    @ended="audioEnd"
                ></audio>
          </div>
      </div>
  </div>
</template>


<script>
import axios from 'axios'
export default {
    name:"Music",
    data () {
        return {
            videoState: false,  // 播放状态
            paths:'',
            musicName:[],
            imgs:[],
            musicUrl:'',
            musicText:''
        }
    },
    components:{
        
    },
   created () {
    this.getViewDataId()
   },
    methods: {
        
        



        getViewDataId(){ 
            var ids =  this.$route.params.id
                axios.get('http://localhost:3000/playlist/track/all?id=' + ids +'&limit=10&offset=1').then(data =>{
                console.log(data);
                this.musicName = data.data.songs
                this.imgs = data.data.songs.al
                console.log(data.data.songs);
                console.log(ids);
            })
        },
        plays(id){
             axios.get('http://localhost:3000/song/url?id='+id+'').then( data =>{
                 var a = data.data.data[0].url
                 this.musicUrl = a.toString()
             }) 
        },
        textMusic(id){
            axios.get('http://localhost:3000/lyric?id='+id+'').then( data =>{
                  
                var lararr= {}
                var larstring = data.data.lrc.lyric.split("\n")
                    var reg = /\[\d*:\d*(\.|:)\d*]/g;
                    for(var i = 0; i<larstring.length;i++){
                        var timeReg = larstring[i].match(reg)
                        // console.log(timeReg);
                        if (!timeReg) continue;
                        //取出分钟
                        var t = timeReg[0]
                        var min = Number(t.match(/\[\d*/i).toString().slice(1))
                        var second = Number(t.match(/\:\d*/i).toString().slice(1))
                             console.log(second);
                        //文本歌词
                        // var content = larstring[i].replace(timeReg,"")
                         
                        //     lararr[time] = content
                             

                    }
                     var time = min  + screen
                    console.log(Number(time));
             })

        },
        play(){
            this.$refs.audio.play()
            this.videoState = true
        },
        audioEnd(){
            this.videoState = false
        }

    },
    mounted(){
        
        
    },
    
}
</script>

<style scoped>
    .Views{
        display: flex;
        justify-content: space-around;
    }
    .listMusic{
        border-radius: 30px;
        width: 60%;
        height: 87vh;
        box-shadow: 0px 0px 20px 8px #dfcef0bd;
    
    }
    .MusicView{
        border-radius: 30px;
        width: 30%;
        box-shadow: 0px 0px 20px 8px #dfcef0bd;
        height: 87vh;
        
    }.imgsIcon{
        width: 40px;
        height: 40px;
        
    }.listMusic{
        overflow: auto;
    }
    .listMusic::-webkit-scrollbar{
        display: none;
    }.listMusiczh{
        display: flex;
        font-size: 10px;
        width: 90%;
        height: 80px;
        border-radius: 10px;
        transform: translate(5%);
        box-shadow: 0px 0px 20px 8px #dfcef0bd;
        flex-direction: row-reverse;
        justify-content: flex-end;
        align-items: center;
        margin: 10px 0px;
    }.playInco{
        right: 100px;
        position: absolute;
    }.audioMusic{
        position: absolute;
        bottom: 50px;
        right: 0;
        width: 100%;
    }.MusicView{
        position: relative;
    }
</style>