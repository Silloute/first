<template>
  <div id="app">
    <audio controls>
  <source :src=m type="audio/mpeg">
  您的浏览器不支持 audio 元素。
</audio>
    <button @click="btnclick">获取</button>
  </div>
</template>a

<script>
import axios from "axios";
export default {
  name: "App",
  data(){
    return {
      m:{
        type:String,
        default:""
      }
    }
  },
  methods: {
    btnclick() {
      function request(config) {
        //检测当前环境是否为生产环境
        const instance = axios.create({
          //由于有跨域问题，所以调试和打包用不同的baseURL
          baseURL: "https://api.imjad.cn/cloudmusic/",
          // baseURL: "https://autumnfish.cn/",
          timeout: 5000,
        });
        return instance(config);
      }
      request({
        url: "?type=search&search_type=1&s=cocoon",
        // withCredentials: true
      }).then(res=>{
      // this.m = res.data.data[0].url;
      console.log(res);
      });

    },
  },
};
</script>

<style>
</style>
