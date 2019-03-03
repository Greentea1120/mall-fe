<template>
  <div>
    <div class="search-bar">
      <van-row gutter="5">
        <van-col span="3">
          <img :src="locationIcon" alt="" width="60%" class="location-icon">
        </van-col>
        <van-col span="16">
          <input type="text" class="search-input">
        </van-col>
        <van-col span="5">
          <van-button size="mini">查找</van-button>
        </van-col>
      </van-row>
    </div>
    <div class="swiper-area">
      <van-swipe :autoplay="1000">
        <van-swipe-item v-for="(banner,index) in bannerPicArray" :key="index">
          <img v-lazy="banner.imageUrl" width="100%"/>
        </van-swipe-item>
      </van-swipe>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
import axios from 'axios'
export default {
  created() {
    axios({
      url: 'https://www.easy-mock.com/mock/5c7bfb7e852a035c430117a1/mall/index',
      method: 'get'
    }).then(res => {
      console.log(res)
    })
  },
  data() {
    return {
      msg: 'Shopping Mall',
      locationIcon: require('../../assets/images/location.png'),
      bannerPicArray: [
        { imageUrl: 'https://miniyx.oss-cn-beijing.aliyuncs.com/data/upload/content/20190124/5c4967c876404.gif' },
        { imageUrl: 'https://miniyx.oss-cn-beijing.aliyuncs.com/data/upload/content/20190124/5c4967c876404.gif' },
        { imageUrl: 'https://miniyx.oss-cn-beijing.aliyuncs.com/data/upload/content/20190124/5c4967c876404.gif' }
      ]
    }
  },
  components: {

  }
}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
.search-bar{
  // height: 2.2rem;
  background-color: #e5017d;
  line-height: 2.2rem;
}
.search-input{
  width:100%;
  height: 1.3rem;
  border-top:0px;
  border-left:0px;
  border-right:0px;
  border-bottom: 1px solid 1px !important ;
  background-color: #e5017d;
  color:#fff;
}
.location-icon{
  padding-top: .2rem;
  padding-left: .3rem;
}
.swiper-area{
  width:20rem;
  clear:both;
  max-height 15rem;
  overflow hidden
}
</style>
