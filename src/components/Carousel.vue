<template>
    <div class="container">
        <el-carousel height="900px" direction="vertical" :autoplay="false">
    <el-carousel-item v-for="item in 1" :key="item">
      <hero/>
    </el-carousel-item>
  </el-carousel>
    </div>
</template>

<script>
import Hero from './Hero'
export default {
    name:'carousel',
    components:{
        Hero
    }
}
</script>

<style lang="scss" scoped>
.el-carousel__item h3 {
    color: #475669;
    font-size: 14px;
    opacity: 0.75;
    line-height: 200px;
    margin: 0;
  }
  
  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }
  
  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }
</style>