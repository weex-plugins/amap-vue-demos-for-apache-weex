<template>
  <div class="container">
    <navbar title="设置自定义信息窗体"></navbar>
    <weex-amap class="map" id="map2017" :sdk-key="keys" :zoom="zoom" :center="pos">
      <weex-amap-marker style="z-index:1000" hide-callout="true" :position="marker.position" :icon="marker.icon" :title="marker.title"></weex-amap-marker>
      <weex-amap-marker style="z-index:1000" hide-callout="true" :position="marker2.position" :icon="marker.icon" :title="marker2.title"></weex-amap-marker>
      <weex-amap-info-window class="info-win" :offset="palaceMuseum.offset"  :open="palaceMuseum.open" :position="palaceMuseum.position">
        <info-window src="http://img1.vued.vanthink.cn/vued6dfd998fc0738f7e88d4b66bafc547ce.jpeg" title="The Palace Museum" location="4 Jingshan Front St, Dongcheng Qu, Beijing"></info-window>
      </weex-amap-info-window>
      <weex-amap-info-window class="info-win" :offset="southStation.offset" :open="southStation.open" :position="southStation.position">
        <info-window  src="http://img1.vued.vanthink.cn/vued2de302ef72ae921313a1fa1bbbbd9455.jpeg" title="Beijing South Railway Station" location="Fengtai, Beijing"></info-window>
      </weex-amap-info-window>
    </weex-amap>
    <div class="map-control">
      <text class="title">Component: weex-amap-info-window</text> 
      <text class="tips">在地图上显示自定义窗体</text> 
      <div class="btn-group">
        <div @click="toggleSta" class="btnbox">
          <text v-if="!southStation.open" class="btn" >打开南站信息</text>
          <text v-if="southStation.open" class="btn" >关闭南站信息</text>
        </div>
        <div @click="toggleMus" class="btnbox">
          <text v-if="!palaceMuseum.open" class="btn" >打开故宫信息</text>
          <text v-if="palaceMuseum.open" class="btn" >关闭故宫信息</text>
        </div>
      </div>
      
    </div>
  </div>
</template>

<style scoped>
  .container{
    position: relative; 
    flex:1; 
    background-color: #fff;
  }
  .map{
    flex: 1;
    position: relative;
    background-color: #fff;
    min-height: 800px;
    border-bottom-width: 10px;
    border-bottom-color: #fff;
  }
  .map-control{
    padding-top: 20px;
    min-height: 600px;
  }
  .title{
    margin-left: 20px;
    padding-left: 20px;
    padding-top: 10px;
    padding-bottom: 10px;
    font-size: 36px;
    border-left-width: 6px;
    border-left-color: #0f89f5;
    color: #222;
    text-align: left;
  }
  .tips{
    margin: 20px;
    padding: 10px;
    color:#666;
    font-size: 20px;
  }
  .btn-group{
    flex-direction: row;
  }
  .btn{
    flex: 1;
    margin: 20px;
    padding: 20px;
    background-color: #1ba1e2;
    border-radius: 5px;
    color: #fff; 
    text-align:center;
    cursor: pointer;
    font-size: 28px;
  }
  .info-win{
    width: 500px;
    padding: 5px;
    background-color: #fff;
    border-width: 1px;
    border-color: rgba(0,0,0,.1);
    border-bottom-width: 2px;
    border-bottom-color: rgba(0,0,0,.25);
  }
  
</style>

<script>
  const navbar = require('../include/navbar.vue');
  const infoWindow = require('../include/info-window.vue');
  module.exports = {
    components: {
      infoWindow,
      navbar
    },
    
    data() {
      return {
        keys: {
          h5:'f4b99dcd51752142ec0f1bdcb9a8ec02',
          ios: 'c551f83e1e5b19af89c74096f1c0f007',
          android: 'db6a973159cb0c2639ad02c617a786ae'
        },
        pos: [116.397428, 39.90923],
        zoom: 11,
        marker: {
          position: [116.379278,39.865374],
          title: 'Beijing South Railway Station',
          icon: 'http://img1.vued.vanthink.cn/vuede8f1ae7b454267d75c31c6d46819b597.png',
        },
        marker2: {
          position: [116.397389, 39.908742],
          title: 'The Palace Museum',
          icon: 'http://img1.vued.vanthink.cn/vuede8f1ae7b454267d75c31c6d46819b597.png'
        },
        palaceMuseum: {
          position: [116.397389, 39.908742],
          offset: [0, -80],
          open: false
        },
        southStation: {
          position: [116.379278,39.865374],
          offset: [0, -80],
          open: true
        },
      };
    },
    
    methods: {
      toggleSta() {
        this.southStation.open = !this.southStation.open;
        // only one info window can be opened in the map
        if(this.southStation.open && this.palaceMuseum.open) {
          this.palaceMuseum.open = false;  
        }
      },
      toggleMus() {
        this.palaceMuseum.open = !this.palaceMuseum.open;
        if(this.palaceMuseum.open && this.southStation.open) {
          this.southStation.open = false;  
        }
      }
    }
  }
</script>