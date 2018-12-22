<template>
<div class="index">
    <div class="nav">
        <i class="iconfont icon-sousuo"></i>
         <input type="text" placeholder="搜索">
    </div>
    <swiper
       indicator-dots
       autoplay
       circular
       class="swiper"
     >
        <swiper-item v-for="(item,index) in swiperList" :key="index">
           <image mode="aspectFill" 
           :src="item.image_src"
           ></image>
         </swiper-item>
    </swiper>
</div>
</template>

<script>
//导入自己抽取的hxios
import hxios from "../../utils/index.js";
export default {
    data: function(){
        return{
             //轮播图
             swiperList:[]
        };
    },
    //获取数据
    created(){
      hxios.get("api/public/v1/home/swiperdata").then(res=>{
        //   
        this.swiperList=res.data.message;
      })
    }
};
</script>

<style lang="scss">
$uRed:#ff2d4a;
.index{
    padding-top:100rpx;
}
.nav{
    padding: 20rpx 16rpx;
    background-color: $uRed;
    position:fixed;
    width:100%;
    left:0;
    top:0;
    box-sizing:border-box;
    input{
        background-color: white;
        text-align: center;
        font-size: 24rpx;
        color: #bbb;
        height: 60rpx;
    }
    i.icon-sousuo{
        color:#bbb;
        position:absolute;
        top:50%;
        left:50%;
        transform:translate(-220%,-50%);
    }
}
.swiper{
    image{
        width: 100%;
    }
}

</style>
