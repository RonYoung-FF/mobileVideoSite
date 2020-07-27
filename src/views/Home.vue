<template>
  <div class="home">
      <!-- 状态栏 -->
      <div class="head-wrap">
        <img src="../assets/logo.png" alt="avatar-img" class="avatar">
        <div class="search-bar">
          <van-icon name="search" size="1.5rem"/>
        </div>
        <van-icon name="aim" size="2.5rem"/>
        <van-icon name="envelop-o" size="2.5rem"/>
      </div>
      <!-- 首页轮播图 -->
      <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
        <van-swipe-item>1</van-swipe-item>
        <van-swipe-item>2</van-swipe-item>
        <van-swipe-item>3</van-swipe-item>
        <van-swipe-item>4</van-swipe-item>
      </van-swipe>
    <van-sticky>
      <van-tabs v-model="currentTabIndex" @click="tabChange">
        <van-tab :key="index" v-for="(item, index) in tabListData" :title="item" >
      </van-tab>
      </van-tabs>
    </van-sticky>
    <!-- 下部内容区域 -->
    <van-swipe class="my-swipe test" :show-indicators="false" @change="contentChange" ref="swipe">
      <van-swipe-item :key="index" v-for="(item, index) in tabListData" >1</van-swipe-item>
    </van-swipe>
    <!-- 底部标签栏 -->
    <van-tabbar v-model="currentBarIndex" class="bth">
      <van-tabbar-item icon="home-o">首页</van-tabbar-item>
      <van-tabbar-item icon="tv-o" dot>频道</van-tabbar-item>
      <van-tabbar-item icon="friends-o" badge="5">动态</van-tabbar-item>
      <van-tabbar-item icon="user-circle-o" badge="20">我的</van-tabbar-item>
    </van-tabbar>
  </div>
</template>
<style lang="less">
  .head-wrap{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 0 1rem;
  }
  .search-bar{
    width: 20rem;
    height: 3rem;
    background: #ebebeb;
    border-radius: 3rem;
    display: flex;
    align-items: center;
    .van-icon{
      margin-left: 0.8rem;
      color:#ccc
    }
  }
  .avatar{
    width: 5rem;
    border-radius: 50%;
    border:1px solid black
  }
  .my-swipe .van-swipe-item {
    color: #fff;
    font-size: 20px;
    line-height: 20rem;
    text-align: center;
    background-color: #39a9ed;
  }
  .test{
    height:200vh
  }
</style>

<script>
export default {
  data () {
    return {
      tabListData: [
        '推荐',
        '热门',
        '追番',
        '影视'
      ],
      currentTabIndex: 0,
      currentBarIndex: 0
    }
  },
  methods: {
    contentChange (index) {
      this.currentTabIndex = index
    },
    tabChange () {
      this.$refs.swipe.swipeTo(this.currentTabIndex)
    }
  }
}
</script>
