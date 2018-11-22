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

    <van-list
        v-model="loading"
        :finished="finished"
        @load="onLoad"
        :loading-text="loadingText"
      >
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
      </van-list>
    <!-- <ul class="pro-list">
      <li v-for="item in proList" :key="item.id">
        <a href="">
          <img :src="item.imageURL"/>
          <dl>
            <dt>{{item.title}}</dt>
            <dd>{{item.desc}}</dd>
          </dl>                   
        </a>
      </li>
    </ul> -->
    <p class="bottom-line">我是有底线的</p>
  </div>
</template>

<script>
import Vue from 'vue';
import { Swipe, SwipeItem, Lazyload, Tabbar, TabbarItem, NoticeBar, List} from 'vant';
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
    [List.name]:List,
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
        {'desc':'444444444','title':'dddddddd','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
         {'desc':'1111111111111111111111111111','title':'aaaaaaa','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'2222222','title':'bbbbbb','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'33333333','title':'cccccccc','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'444444444','title':'dddddddd','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'} 
      ,
       {'desc':'1111111111111111111111111111','title':'aaaaaaa','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'2222222','title':'bbbbbb','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'33333333','title':'cccccccc','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'desc':'444444444','title':'dddddddd','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'} 
      
      ],
       list: [],
      loading: false,
      finished: false,
      loadingText: '正在使尽洪荒之力为亲加载更多……'
    }
  },

  methods: {
    onClickCart() {
      this.$router.push('cart');
    },
    onLoad() {
      // 异步更新数据
      setTimeout(() => {
        for (let i = 0; i < 10; i++) {
          this.proList.push(this.proList.length + 1);
        }
        // 加载状态结束
        this.loading = false;

        // 数据全部加载完成
        if (this.proList.length >= 30) {
          this.finished = true;
        }
      }, 500);
    }

  }
};
</script>

<style lang="less">
@themeColor: #f66;
@bgColor: #f7f7f7;
@itemBgColor: #fff;
@fontColorH3: #333;
@fontColorP: #666;
@tipColor:#999;
.index {
  background-color: @bgColor;
  .swipe {
    img {
      width: 100%;
      height: 14.375rem /* 230/16 */;
    }
    .van-swipe__indicator--active {
      background-color: @themeColor;
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
      background-color: @itemBgColor;
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
            color: @fontColorH3;
            font-size: 20px;
          }
          dd {
            color: @fontColorP;
            font-size: 16px;
          }
        }
      }
     
    }
  }
  .notice {
    margin-bottom: 5px;
    color: @themeColor;
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
  .bottom-line {
     margin-top: 0;
     margin-bottom: 3.125rem /* 50/16 */;
     padding-bottom: 5px;
     color: @tipColor;
     font-size: .8rem /* 16/16 */;
     text-align: center;
     line-height: 1;
  }  
}
.van-tabbar-item {
    color: @fontColorH3 !important;
    font-size: .9rem;
    &--active {
      color: @themeColor !important;
    }
}


</style>
