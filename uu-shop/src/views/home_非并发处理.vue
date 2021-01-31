<template>
  <div class="mbClass">
    <!-- 导航栏 -->
    <van-nav-bar title="小U商城" left-arrow />
    <!-- 
        轮播图
        autoplay 自动播放
    -->
    <van-swipe :autoplay="2000">
      <van-swipe-item v-for="item in bannerList" :key="item.id">
        <img class="swiperImg" :src="$imgUrl + item.img" alt="" />
      </van-swipe-item>
    </van-swipe>
    <!-- 
        宫格 
    gutter 间距   格子之间的间距，默认单位为px 
    -->
    <!-- <van-grid :gutter="10">
      <van-grid-item icon="photo-o" text="文字" />
      <van-grid-item icon="photo-o" text="文字" />
      <van-grid-item icon="photo-o" text="文字" />
      <van-grid-item icon="photo-o" text="文字" />
      <van-grid-item icon="photo-o" text="文字" />  <van-grid-item icon="photo-o" text="文字" />  <van-grid-item icon="photo-o" text="文字" />  <van-grid-item icon="photo-o" text="文字" />  <van-grid-item icon="photo-o" text="文字" />  <van-grid-item icon="photo-o" text="文字" />
    </van-grid> -->
    <!-- 
        自定义内容 根据你的需求 渲染列数 
        在vant中引入图片无法渲染，必须通过require的方式
        -->
    <van-grid :border="false" :column-num="5">
      <van-grid-item v-for="item in brandList" :key="item.title">
        <van-image :src="item.brandImg" />
        <p class="titleName">{{ item.title }}</p>
      </van-grid-item>
      <!-- <van-grid-item>
        <van-image :src="require('../assets/images/icon/top.png')" />
        <p>畅销商品</p>
      </van-grid-item>
      <van-grid-item>
        <van-image :src="require('../assets/images/icon/brand.png')" />
      </van-grid-item>
      <p>品质打牌</p>
      <van-grid-item>
        <van-image :src="require('../assets/images/icon/selfsupport.png')" />
        <p>小U自营</p>
      </van-grid-item>

      <van-grid-item>
        <van-image :src="require('../assets/images/icon/integral.png')" />
        <p>积分商城</p>
      </van-grid-item> -->
    </van-grid>
    <!-- 商品列表切换  3种：一、所有产品列表 二、是新品的列表  三、是热卖的列表-->
    <van-tabs type="card">
      <van-tab title="最新商品">
        <van-card
          v-for="newGoods in newList"
          :key="newGoods.id"
          :price="newGoods.price.toFixed(2)"
          desc="描述信息"
          :title="newGoods.goodsname"
          :thumb="
            newGoods.img
              ? $imgUrl + newGoods.img
              : 'https://img.yzcdn.cn/vant/ipad.jpeg'
          "
        />
      </van-tab>
      <van-tab title="爆款商品">
        <van-card
          v-for="hotGoods in hotList"
          :key="hotGoods.id"
          :price="hotGoods.price.toFixed(2)"
          desc="描述信息"
          :title="hotGoods.goodsname"
          :thumb="
            hotGoods.img
              ? $imgUrl + hotGoods.img
              : 'https://img.yzcdn.cn/vant/ipad.jpeg'
          "
        />
      </van-tab>
      <van-tab title="所有商品">
        <van-card
          v-for="goods in goodsList"
          :key="goods.id"
          :price="goods.price.toFixed(2)"
          desc="描述信息"
          :title="goods.goodsname"
          :thumb="
            goods.img
              ? $imgUrl + goods.img
              : 'https://img.yzcdn.cn/vant/ipad.jpeg'
          "
        />
      </van-tab>
    </van-tabs>
  </div>
</template>

<script>
//引入接口文档
import { getBanner, getIndexGoodsList } from "../util/axios";
export default {
  data() {
    return {
      bannerList: [], //轮播图列表
      hotList: [], //热门商品
      newList: [], //最新商品
      goodsList: [], //所有商品
      brandList: [
        //品牌集合
        {
          title: "限时秒杀",
          brandImg: require("../assets/images/icon/seckill.png")
        },
        {
          title: "畅销商品",
          brandImg: require("../assets/images/icon/top.png")
        },
        {
          title: "品质大牌",
          brandImg: require("../assets/images/icon/brand.png")
        },
        {
          title: "小U自营",
          brandImg: require("../assets/images/icon/selfsupport.png")
        },
        {
          title: "积分商城",
          brandImg: require("../assets/images/icon/integral.png")
        }
      ]
    };
  },
  mounted() {
    //页面一加载就调取轮播图接口
    this.getBannerList();
    //页面一加载就调用商品列表
    this.getGoodsList();
  },
  methods: {
    //封装一个获取轮播图事件
    getBannerList() {
      getBanner().then(res => {
        if (res.code == 200) {
          this.bannerList = res.list;
        }
      });
    },
    //封装一个获取商品列表的事件
    getGoodsList() {
      getIndexGoodsList().then(res => {
        if (res.code == 200) {
          this.hotList = res.list[0].content;
          this.newList = res.list[1].content;
          this.goodsList = res.list[2].content;
        }
        console.log(res, "首页的商品列表");
      });
    }
  }
};
</script>

<style lang="" scoped>
.swiperImg {
  width: 100%;
  height: 3.9rem;
}
.titleName {
  font-size: 14px;
}
.mbClass{
    margin-bottom: 60px;
}
</style>
