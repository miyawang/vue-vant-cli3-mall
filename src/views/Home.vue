<template>
  <div class="index">
    <van-swipe class="swipe">
      <van-swipe-item class="swipe-item" v-for="(image, index) in swipeImages" :key="index">
        <img v-lazy="image" />
      </van-swipe-item>
    </van-swipe> 
    <ul class="grid">
      <li v-for="item in grid" :key="item.id">
        <a href="">
          <img :src="item.imageURL"/>
          <dl>
            <dt>{{item.title}}</dt>
            <dd>{{item.desc}}</dd>
          </dl>                   
        </a>
      </li>
    </ul>
    <van-notice-bar :left-icon="noticeIcon" mode="link" :scrollable="true" class="notice">
      {{noticeText}}
    </van-notice-bar>
    <section class="hot">
      <h3>热门贷款</h3>
      <span>更多>></span>
    </section>
    <ul class="pro-list">
      <li v-for="item in proList" :key="item.id">
        <a href="">
          <img :src="item.imageURL"/>
          <dl>
            <dt>{{item.title}}</dt>
            <dd>{{item.desc}}</dd>
          </dl>                   
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
import Vue from 'vue';
import { Swipe, SwipeItem, Lazyload, Tabbar, TabbarItem, NoticeBar} from 'vant';
// Vue.use(Swipe).use(SwipeItem);
Vue.use(Lazyload, {});
// Vue.use(Tabbar).use(TabbarItem);

// import {  Lazyload} from 'vant';
// Vue.use(Swipe).use(SwipeItem);
// import {
//   Tag,
// } from 'vant';
export default {
  components: {
    [Swipe.name]: Swipe,
    [SwipeItem.name]: SwipeItem,
    [Tabbar.name]: Tabbar,
    [NoticeBar.name]: NoticeBar,
  },

  data() {
    return {
      swipeImages: [
        'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg',
        'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960882&di=5f198d168b4debf8589ed1e0f1f38814&imgtype=0&src=http%3A%2F%2Fimg5.duitang.com%2Fuploads%2Fitem%2F201410%2F14%2F20141014102519_niZhB.jpeg'
      ],
      grid: [
        {'desc':'1111111111111111111111111111','title':'aaaaaaa','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'2222222','title':'bbbbbb','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'33333333','title':'cccccccc','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'444444444','title':'dddddddd','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'}
      ],
      noticeText:'zzzzbbbbbbbbbzzzzzzzhhhhhhhhhhhhhhhhhhhhh',
      noticeIcon:'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg',
      proList: [
        {'desc':'1111111111111111111111111111','title':'aaaaaaa','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'2222222','title':'bbbbbb','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'33333333','title':'cccccccc','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'444444444','title':'dddddddd','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'} 
      ]
    }
  },

  methods: {
    onClickCart() {
      this.$router.push('cart');
    },

  }
};
</script>

<style lang="less">
.index {
  background-color: #f7f7f7;
  .swipe {
    img {
      width: 100%;
      height: 14.375rem /* 230/16 */;
    }
  }
  .grid , .pro-list {
    display: flex;
    // justify-content: center;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    li {
      flex-basis:49.3%;
      background-color: #fff;
      // border: 1px solid red;
      box-sizing: border-box;
      padding: 10px;
      display: flex;
      justify-content: space-between;
      margin-bottom: 5px;      
      a {
        display: flex;
        justify-content: center;
        align-items: center;
        img {
          width: 3.125rem /* 50/16 */;
          height: 3.125rem /* 50/16 */;
          border-radius: 50%;
          margin-right: 5px;
        }
        dl {
          list-style: none;
          padding: 0;
          margin: 0;     
          // border: 1px solid blue;
          flex:1;
          overflow: hidden;
          
          dt, dd {
            padding: 0;
            margin: 0; 
            width: 100px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            // display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
          }
          dt {
            color: #333;
            font-size: 20px;
          }
          dd {
            color: #666;
            font-size: 16px;
          }
        }
      }
     
    }
  }
  .notice {
    margin-bottom: 5px;
  }
  .hot {
    display: flex;
    margin: 5px 0;
    justify-content: space-between;
    align-items: center;
    background-color: #fff;
    padding: 0 20px;
    height: 2.75rem /* 44/16 */;
    h3 {
      color: #0c0c0c;
      font-size: 20px;
    }
    span {
      color: #444;
      font-size: 14px;
    }
  }
  .pro-list {
    li {
      flex-basis:100%;
    }
  }
}
</style>
