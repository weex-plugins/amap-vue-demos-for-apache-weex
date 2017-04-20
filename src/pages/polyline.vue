<template>
  <div class="container">
    <navbar title="设置折线"></navbar>
    <weex-amap class="map" id="map2017" :sdk-key="keys" :zoom="zoom" :center="pos">
      <weex-amap-polyline :path="path" stroke-style="solid" stroke-opacity="0.7" stroke-color="#000000" stroke-width="2"></weex-amap-polyline>
    </weex-amap>
    <div class="map-control">
      <text class="title">Component weex-amap-polyline</text> 
      <text class="tips">在地图上绘制折线</text>
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
</style>

<script>
  const navbar = require('../include/navbar.vue');
  
  module.exports = {
    components: {
      navbar,
    },
    data() {
      return {
        keys: {
          h5:'f4b99dcd51752142ec0f1bdcb9a8ec02',
          ios: '',
          android: 'db6a973159cb0c2639ad02c617a786ae'
        },
        pos: [116.397428, 39.90923],
        path: [  
          [116.368904, 39.913423],
          [116.382122, 39.901176],
          [116.387271, 39.912501],
          [116.398258, 39.904600]],
        zoom: 13
      };
    }
  }
</script>