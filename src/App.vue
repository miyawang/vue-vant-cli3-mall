<template>
  <div id="app">
    <router-view/>
    <van-tabbar v-model="active" class="nav">
      <van-tabbar-item icon="chat" to="/">首页</van-tabbar-item>
      <van-tabbar-item icon="records" to="/category">分类</van-tabbar-item>
      <van-tabbar-item icon="chat" to="/cart" info="3">购物车</van-tabbar-item>
      <van-tabbar-item icon="records" to="user">我的</van-tabbar-item>
    </van-tabbar>
  </div>
</template>
<script>
import { Tabbar, TabbarItem } from 'vant';
// Vue.use(Tabbar).use(TabbarItem);
export default {
   components: {
    [Tabbar.name]: Tabbar,
    [TabbarItem.name]: TabbarItem,

  },
  data() {
    return {
      active: 0,
      icon: {
        normal: '//img.yzcdn.cn/icon-normal.png',
        active: '//img.yzcdn.cn/icon-active.png'
      }
    }
  }
}
</script>
<style lang="less">
@import url("./assets/reset.css");
@import url("./assets/iconfont/iconfont.css");


</style>

