<template>
  <div class="xyly_index">
    <!-- 轮播图开始 -->
    <div class="index_carousel">
    <el-carousel height="700px">
      <el-carousel-item v-for="(item,index) in swiperList" :key="index">
       <div :style="`background:url(${$axios.defaults.baseURL+item.url}) center center ;height:700px;`"></div>
      </el-carousel-item>
      
    </el-carousel>
    <!-- 轮播图结束 -->
     <div>
       <Tab class="tabs"/>
    </div>
    </div>
  </div>
</template>
<script>
import Tab from '@/components/index/Tab.vue'
export default {
  components:{
    Tab
  },
    data(){
        return{
            swiperList:[]
        }
    },
   mounted(){
      this.$axios.get("/scenics/banners").then(res=>{
          console.log(res)
          this.swiperList = res.data.data
    })
  }
};
</script>

<style lang="less" scoped>
.index_carousel{
  position: relative;
  .tabs{
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 999;
  }
}

</style>