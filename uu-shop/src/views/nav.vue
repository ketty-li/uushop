<template>
  <div id="app">
    <div class="nav">
      <div class="top">
        <i class="iconfont icon-dingwei1"></i>
        <h1><img :src="navImg" alt="" /></h1>
        <!-- 搜索 -->
        <div class="search">
          <span> <i class="iconfont icon-fangdajing"></i></span>
          <input type="text" placeholder="按内容搜索" />
        </div>
        <i class="iconfont icon-dianpu"></i>
      </div>
      <!-- nav -->
      <div class="buttom">
        <span class="line"></span>
        <span class="tuijian">推荐</span>
        <ul>
          <li v-for="item in navlist" :key="item.id">{{ item.name }}</li>
        </ul>
        <span class="yinying"></span>
        <div class="fenlei">
          <i class="iconfont icon-fenlei"></i><span>分类</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navImg: require("../assets/images/index/white.png"),
      navlist: [
        { id: 1, name: "女装" },
        { id: 2, name: "鞋包" },
        { id: 3, name: "居家" },
        { id: 4, name: "母婴" },
        { id: 5, name: "美妆" }
      ]
    };
  }
};
</script>

<style lang="">
/* 
.nav {
  width: 7.5rem;
  height: 1.76rem;
  margin-top: 0.88rem;
  background-image: linear-gradient(180deg, #ff6040 0%, #ff8a80 100%);
  box-shadow: 0 0.04rem 0.12rem 0 rgba(255, 149, 128, 0.5);
}
.nav .top {
  display: flex;
  text-align: center;
}
.nav .top .icon-dingwei1 {
  font-size: 0.44rem;
  color: #fff;
  margin: 0 0.26rem;
  line-height: 0.6rem;
}
.nav .top img {
  width: 1.82rem;
  height: 0.48rem;
}
.nav .top .search {
  display: flex;
  width: 3.4rem;
  height: 0.64rem;
  margin: 0 0.26rem;
}
.nav .top .search span {
  position: relative;
  display: inline-block;
  width: 0.64rem;
  height: 0.64rem;
  background-color: #fff;
}
.nav .top .search span .icon-fangdajing {
  font-size: 0.32rem;
  color: #999;
  position: absolute;
  top: 0.18rem;
  left: 0.16rem;
}
.nav .top .search input {
  width: 2.76rem;
  border: none;
  background-color: #fff;
}
.nav .top .icon-dianpu {
  font-size: 0.4rem;
  color: #fff;
  line-height: 0.6rem;
}
.nav .buttom {
  position: relative;
  margin-top: 0.6rem;
  display: flex;
  color: #fff;
}
.nav .buttom .tuijian {
  display: inline-block;
  width: 0.66rem;
  height: 0.48rem;
  margin-left: 0.2rem;
  font-size: 0.32rem;
}
.nav .buttom .line {
  display: inline-block;
  position: absolute;
  bottom: 0rem;
  left: 0.34rem;
  width: 0.4rem;
  height: 0.06rem;
  background-color: #fff;
}
.nav .buttom ul {
  font-size: 0.28rem;
}
.nav .buttom ul li {
  color: #fff3f2;
  float: left;
  margin-left: 0.52rem;
}
.nav .buttom .yinying {
  display: inline-block;
  width: 0.02rem;
  height: 0.3rem;
  border-left: 0.01rem solid #e41e1e;
  margin: 0.08rem;
  position: absolute;
  top: -0.06rem;
  right: 1rem;
}
.nav .buttom .fenlei {
  font-size: 0.28rem;
  right: 0.12rem;
  top: 0;
  position: absolute;
}
.nav .buttom .fenlei .icon-fenlei {
  margin-right: 0.06rem;
  font-size: 0.32rem;
} */
</style>
