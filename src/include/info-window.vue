<template>
  <div class="info-win">
    <image class="cover" :src="src"/>
    <text class="desc">{{title}}</text>
    <text class="address">{{location}}</text>
  </div>
</template>

<style scoped>
  .info-win{
    width: 500px;
    padding: 5px;
    background-color: #fff;
    border-width: 1px;
    border-color: rgba(0,0,0,.1);
    border-bottom-width: 2px;
    border-bottom-color: rgba(0,0,0,.25);
  }
  .cover{
    flex: 1;
    height: 180px;
  }
  .desc{
    font-size: 20px;
    background-color: #fff;
    padding: 5;
  }
  .address{
    font-size: 16px;
    color: #999;
    background-color: #fff;
    padding: 5px;
    padding-bottom: 10px;
  }
</style>

<script>
  export default {
    props: {
      src: {
        type: String,
        default: '',
      },
      title: {
        type: String,
        default: '',
      },
      location: {
        type: String,
        default: ''
      }
    }
  };
</script>