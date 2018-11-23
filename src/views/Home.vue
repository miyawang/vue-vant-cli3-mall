<template>
  <div class="index">
    <van-swipe class="swipe">
      <van-swipe-item class="swipe-item" v-for="(image, index) in swipeImages" :key="index">
        <img v-lazy="image" />
      </van-swipe-item>
    </van-swipe> 
    <van-search
    v-model="searchValue"
    placeholder="请输入搜索关键词"
    @search="onSearch"
    show-action
    >
    <div slot="action" @click="onSearch">搜索</div>
    </van-search>
    <ul class="grid">
      <li v-for="item in grid" :key="item.id">
        <a href="">
          <img :src="item.imageURL"/>
           <h3>{{item.title}}</h3>     
        </a>
      </li>
    </ul>
    <ul class="banner">
      <li><a href=""><span></span>常购清单<span></span></a></li>
      <li>
        <a href="">销量TOP</a>
        <a href="">进店必Buy</a>
      </li>

    </ul>
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
                <dt>西冷牛排</dt>
                <dd>推荐指数：
                  <i class="icon iconfont icon-xingxing">
                    <i class="icon iconfont icon-xingxing">
                      <i class="icon iconfont icon-xingxing">
                        <i class="icon iconfont icon-xingxing">
                          <i class="icon iconfont icon-xingxing"></i>
                        </i>
                      </i>
                    </i>
                  </i>
                </dd>
              </dl> 
              <ul>
                <li>10kg起送</li>
                <li>售价:<span>￥90</span>/kg</li>
              </ul>                  
            </a>
          </li>
        </ul>        
      </van-list>
    <p class="bottom-line">我是有底线的</p>
  </div>
</template>

<script>
import Vue from 'vue';
import { Swipe, SwipeItem, Lazyload, 
Tabbar, TabbarItem, NoticeBar, List,
Search,
} from 'vant';
Vue.use(Lazyload, {});
export default {
  components: {
    [Swipe.name]: Swipe,
    [SwipeItem.name]: SwipeItem,
    [Tabbar.name]: Tabbar,
    [NoticeBar.name]: NoticeBar,
    [List.name]:List,
    [Search.name]:Search,
  },
  data() {
    return {
      swipeImages: [
        'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg',
        'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg',
      ],
      grid: [
        {'title':'牛肉','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'title':'羊肉','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'title':'鸡肉','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'title':'海鲜','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},
        {'title':'更多','imageURL':'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1542631960883&di=2b898862da84f7f4ca497421fcc60227&imgtype=0&src=http%3A%2F%2Fimg.tukexw.com%2Fimg%2F134ea407a06ec41f.jpg'},

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
      loadingText: '正在使尽洪荒之力为亲加载更多……',
      searchValue:'',
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
    },
    onSearch(){

    },
    onCancel() {

    },

  }
};
</script>

<style lang="less">
@themeColor: #f66;
@bgColor: #f7f7f7;
@itemBgColor: #fff;
@fontColorH3: #444;
@fontColorP: #666;
@tipColor:#999;
// @fontSizeH3: 16px;
// 字体
.font-dpr(@font-size){
    font-size:@font-size;
    [data-dpr="2"] &{
        font-size:@font-size*2;
    }
    [data-dpr="3"] &{
        font-size:@font-size*3;
    }
}
// 1px border
.setTopLine(@c:#e5e5e5){
    position:relative;
    &:before{
        content:"";
        position:absolute;
        left:0;top:0;width:100%;
        height:1px;
        border-top:1px solid @c;
    }
    [data-dpr="1"] &:before {
        transform-origin: 0 0;
        -webkit-transform-origin:0 0;
        transform: scaleY(0.5);
        -webkit-transform:scaleY(0.5);
      }
}
.index {
  background-color: @bgColor;
  .swipe {
    position: relative; 
    img {
      width: 100%;
    }
  }
  .van-search {
      position: absolute;
      top: 10px;
      left: 2%;
      width: 96%;
      border-radius: 8px;
      background-color: rgba(255,255,255,.4)!important;
      padding: 0;
      .van-cell {
          background-color:transparent !important;
          padding: 4px;
      }
    }
  .grid {
    box-sizing: border-box;
    display: flex;
    justify-content: space-between;
    align-items: center;
    text-align: center;
    background-color: #fff;
    height: 88px;
    padding: 8px 16px;
    img {
      height: 48px;
      width: 48px;
      border-radius: 50%;
    }
    h3 {
      .font-dpr(16px);
      color: @fontColorH3;
      font-weight: 400;
      line-height: 1.2;
    }
  }
  .banner {
    display: flex;
    margin:4px 0 /* no */;
    padding: 0 16px;
    background-color: #fff;
    height: 110px;
    li {
      display: flex;
      flex-direction: column;
      flex:2;
      // height: 100px;
      &:first-child  {
        flex:3;
        margin-right: 4px;
        a {
          font-size: 24px;
        span {
            border-top: 1px solid #aaa;;
            border-bottom: 1px solid #aaa;
            height: 6px;
            width: 20%;
          }
        }
      }
      a {
        flex: 1;
        background: url("../assets/1.jpg")  no-repeat;
        background-size: 100% 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        color: @bgColor;
        .font-dpr(14px);
        &:nth-child(2) {
          margin-top: 4px;
        }
      }
    }
  }
  .pro-list {
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    // border: 1px solid #333;

    >li {
      background-color: #fff;
      padding: 4px 16px;
    }
    li {
      flex-basis: 100%;          
      box-sizing: border-box;
      display: flex;
      justify-content: space-between;
      margin-bottom: 2px;   
      height: 70px;   
      a {
        flex: 1;
        display: flex;
        justify-content: center;
        align-items: center;
        // border: 1px solid red;
        color: @fontColorP;
        img {
          flex: 2;
          height: 60px;
          width: 90px;          
        }
        dl {
          flex: 3;
          margin: 0 4px;     
          height: 100%;
          dt {
            color: @fontColorH3;
            .font-dpr(18px);
          }
          dd {
            color: @fontColorP;
            .font-dpr(12px);
            i {
              flex: 1;
              color: @themeColor;
              margin-left: -2px  /* no */;
            }
          }
        }
        ul {
          flex:2;
          // border: 1px solid red;
          display: flex;
          flex-direction: column;
          align-items: flex-end;          
          height: 100%; 
          >li {
            flex: 1;
            .font-dpr(12px);
            span {
              .font-dpr(16px);
              color: @themeColor;
              transform: translateY(-2px);
            }

          }   
        }
      }     
    }
  }
  .bottom-line {
     margin-top: 2px;
     margin-bottom: 50px;
     padding-bottom: 4px;
     color: @tipColor;
     .font-dpr(10px);
     text-align: center;
     line-height: 1;
  }  
}
.van-tabbar {
  height: 48px; 
  // transform: translateY(-50%);
  &-item {
    color: @fontColorH3 !important;
    &--active {
      color: @themeColor !important;
    }
    &__icon {
      .font-dpr(20px) !important;
    }
    &__text {
      .font-dpr(12px) !important;
    }
  }
}

</style>
