<!--  -->
<template>
<div class="box">
 <el-col :span="24"><div class="grid-content bg-purple-dark" >
    <el-carousel indicator-position="outside">
    <el-carousel-item v-for="(item, index) in shufflingImg" :key="index">
      <img class="imgShu" :src="item.image" alt="">
    </el-carousel-item>
  </el-carousel></div></el-col>

  <div>
    <van-button type="primary">主要按钮</van-button>
  </div>
  <div>
    <van-swipe :autoplay="3000">
      <van-swipe-item v-for="(item, index) in shufflingImg" :key="index">
        <img class="imgShu" v-lazy="item.image" />
      </van-swipe-item>
    </van-swipe>
  </div>
  <div> <van-button loading type="primary" loading-type="spinner" /></div>
</div>
 

 
</template>

<script>
export default {
  data () {
    return {
      // 轮播图
   
shufflingImg:'',
    };
  },
  mounted(){
    // 获取数据
    let url = 'https://www.imovietrailer.com/superhero/index/carousel/list?qq=2478029182'
    this.axios.post(url).then(({data,status}) => {
      this.shufflingImg = data.data
      console.log(this.shufflingImg);
    })
  }
}

</script>

<style  scoped>
.imgShu{
  width: 100%;
  height: 100%;
}


.el-carousel__item h3 {
    color: #475669;
    font-size: 18px;
    opacity: 0.75;
    line-height: 20%;
    margin: 0;
  }
  
  .el-carousel__item:nth-child(2n) {
    background-color: pink;
  }
  
  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }
 
</style>
<style>
 .el-carousel__container{
    height: 6.25rem
  }
</style>
