<template>
  <div style="background: #F3F4F5;position: absolute;height: 100%;width: 100%;" @touchmove="goTop">
    <CardHeader></CardHeader>
    <div class="headerType" :style="{top:top+'px'}">
      <div class="headertabs">
        <div class="item_tab" @click="headerClick(0)">
          <div class="line" :class="headerchoose==0?'active':''">
            拼多多
          </div>
        </div>
        <div class="item_tab" @click="headerClick(1)">
          <div class="line" :class="headerchoose==1?'active':''">
            京东
          </div>
        </div>
        <div class="item_tab" @click="headerClick(2)">
          <div class="line" :class="headerchoose==2?'active':''">
            蘑菇街
          </div>
        </div>
      </div>
    </div>
    <!--ending-->
      <!--搜索狂-->
    <div class="modcontent" style="margin-top: 96px;">
      <div style="margin-top: 30px;">
          <div style="background: white;width: 100%;height: 2px;"></div>
          <div style="background: white;padding-left: 12px;padding-right: 12px;height: auto;">
            <div class="search">
              <img src="/static/search/search.png" alt="">
              <input type="text" placeholder="搜所你感兴趣的商品" disabled="disabled">
            </div>
          </div>
    <!--搜索框ending-->
          <!--图片轮播-->
          <div style="background: white;">
            <swiper :indicator-dots="swiperParams.indicatorDots"
                    :autoplay="swiperParams.autoplay"
                    :interval="swiperParams.interval"
                    indicator-color="rgba(255, 255, 255, .5)"
                    indicator-active-color="rgba(255, 255, 255, 1)"
                    :duration="swiperParams.duration"
                    :circular="swiperParams.circular" style="height: 118px;width: 100%;">
              <swiper-item>
                <div style="padding-left: 15px;padding-right: 15px;">
                  <div style="width: 100%;height: 118px;">
                    <image lazy-load="true" src="/static/slider/slider.png" class="slide-image">
                    </image>
                  </div>
                </div>
              </swiper-item>
              <swiper-item>
                <div style="padding-left: 15px;padding-right: 15px;">
                  <div style="width: 100%;height:118px;">
                    <image lazy-load="true" src="/static/slider/slider.png" class="slide-image">
                    </image>
                  </div>
                </div>
              </swiper-item>
            </swiper>
          </div>
          <!--图片轮播ending-->

          <!--广播兰-->
          <div class="vioce">
            <img src="/static/search/Rectangle.png" alt="">
            <ul>
              <li><span>播播酱</span>&nbsp;|&nbsp;雪诺 刚获得了推荐奖励1.88元</li>
              <li><span>播播酱</span>&nbsp;|&nbsp;时仅有 刚获得了推荐奖励1.88元</li>
              <li><span>播播酱</span>&nbsp;|&nbsp;拜拜 刚获得了推荐奖励1.88元</li>
              <li><span>播播酱</span>&nbsp;|&nbsp;小红花 刚获得了推荐奖励1.88元</li>
            </ul>
          </div>
          <!--广播兰ending-->
        </div>
    </div>
    <!--列表数据-->
    <div class="top" :class="isFixed?'fixedpost':''" :style="{top:scrolltop+'px'}">
      <scroll-view scroll-x="true" :scroll-left="scrollLeft" scroll-with-animation="true" style="border-bottom: 1px solid #EBEBEB">
        <div class="tabbar" v-for="(item,index) in navList" :key="index" :class="currentTab==index?'activetab':''" @click="tabClick(index)">
          <div v-show="currentTab==index" class="line"></div>
          {{item.name}}
        </div>
      </scroll-view>
      <div class="choosetype">
        <div>综合</div>
        <div>销量</div>
        <div>
          <span>价格</span>
          <img src="/static/search/chooseprice.png" alt="" style="width: 7px;height: 12px">
        </div>
      </div>
    </div>

    <swiper class="tab-content" :current="currentTab" :scroll-left="scrollLeft" @change="switchTab" duration="300" style="height: 800px;background:#F3F4F5">
      <swiper-item>
        <ul class="swipercontent">
          <li>
            <div class="imgbg">
              <img src="http://192.168.2.23/list.png" alt="">
            </div>
            <div class="discon">
              <p style="height: 14px;margin-top: 8px;">
                <img src="http://192.168.2.23/taobao.png" alt="" class="headerimg">
                <span class="name">小香风毛呢连衣裙冬小香风毛呢连衣裙冬</span>
              </p>
             <p style="height: 16px;padding-left: 5px;margin-top: 4px;">
               <span style="padding: 2px 5px 2px 5px;color: #FF0279;background: #FBDCDC;font-size: 10px;border-radius: 5px;">推荐奖 ¥6.88</span>
               <span style="padding: 2px 5px 2px 5px;color: #68501A;font-size: 10px;background-image: url('http://192.168.2.23/quan.png');margin-left: 6px;background-size: 100% 100%;">券 ¥66.88</span>
             </p>
              <p class="taobaoprice" style="height: 22px;line-height: 22px;padding-left: 5px;margin-top: 8px;">淘宝价12.1</p>
              <p style="height: 30px;line-height: 15px;">
                <span style="color: #FF0279;font-size: 12px;padding-left: 5px">券后</span>
                <span style="color: #FF0279;font-size: 16px;padding-left: 5px">¥12.1</span>
                <span style="color: #CCCCCC;font-size: 12px;float: right;margin-right: 5px;">月销1.2万</span>
              </p>
            </div>
          </li>
          <li>
            <div class="imgbg">
              <img src="http://192.168.2.23/list.png" alt="">
            </div>
            <div class="discon">
              <p style="height: 14px;margin-top: 8px;">
                <img src="http://192.168.2.23/taobao.png" alt="" class="headerimg">
                <span class="name">小香风毛呢连衣裙冬小香风毛呢连衣裙冬</span>
              </p>
              <p style="height: 16px;padding-left: 5px;margin-top: 4px;">
                <span style="padding: 2px 5px 2px 5px;color: #FF0279;background: #FBDCDC;font-size: 10px;border-radius: 5px;">推荐奖 ¥6.88</span>
                <span style="padding: 2px 5px 2px 5px;color: #68501A;font-size: 10px;background-image: url('http://192.168.2.23/quan.png');margin-left: 6px;background-size: 100% 100%;">券 ¥66.88</span>
              </p>
              <p class="taobaoprice" style="height: 22px;line-height: 22px;padding-left: 5px;margin-top: 8px;">淘宝价12.1</p>
              <p style="height: 30px;line-height: 15px;">
                <span style="color: #FF0279;font-size: 12px;padding-left: 5px">券后</span>
                <span style="color: #FF0279;font-size: 16px;padding-left: 5px">¥12.1</span>
                <span style="color: #CCCCCC;font-size: 12px;float: right;margin-right: 5px;">月销1.2万</span>
              </p>
            </div>
          </li>
          <li>
            <div class="imgbg">
              <img src="http://192.168.2.23/list.png" alt="">
            </div>
            <div class="discon">
              <p style="height: 14px;margin-top: 8px;">
                <img src="http://192.168.2.23/taobao.png" alt="" class="headerimg">
                <span class="name">小香风毛呢连衣裙冬小香风毛呢连衣裙冬</span>
              </p>
              <p style="height: 16px;padding-left: 5px;margin-top: 4px;">
                <span style="padding: 2px 5px 2px 5px;color: #FF0279;background: #FBDCDC;font-size: 10px;border-radius: 5px;">推荐奖 ¥6.88</span>
                <span style="padding: 2px 5px 2px 5px;color: #68501A;font-size: 10px;background-image: url('http://192.168.2.23/quan.png');margin-left: 6px;background-size: 100% 100%;">券 ¥66.88</span>
              </p>
              <p class="taobaoprice" style="height: 22px;line-height: 22px;padding-left: 5px;margin-top: 8px;">淘宝价12.1</p>
              <p style="height: 30px;line-height: 15px;">
                <span style="color: #FF0279;font-size: 12px;padding-left: 5px">券后</span>
                <span style="color: #FF0279;font-size: 16px;padding-left: 5px">¥12.1</span>
                <span style="color: #CCCCCC;font-size: 12px;float: right;margin-right: 5px;">月销1.2万</span>
              </p>
            </div>
          </li>
          <li>
            <div class="imgbg">
              <img src="http://192.168.2.23/list.png" alt="">
            </div>
            <div class="discon">
              <p style="height: 14px;margin-top: 8px;">
                <img src="http://192.168.2.23/taobao.png" alt="" class="headerimg">
                <span class="name">小香风毛呢连衣裙冬小香风毛呢连衣裙冬</span>
              </p>
              <p style="height: 16px;padding-left: 5px;margin-top: 4px;">
                <span style="padding: 2px 5px 2px 5px;color: #FF0279;background: #FBDCDC;font-size: 10px;border-radius: 5px;">推荐奖 ¥6.88</span>
                <span style="padding: 2px 5px 2px 5px;color: #68501A;font-size: 10px;background-image: url('http://192.168.2.23/quan.png');margin-left: 6px;background-size: 100% 100%;">券 ¥66.88</span>
              </p>
              <p class="taobaoprice" style="height: 22px;line-height: 22px;padding-left: 5px;margin-top: 8px;">淘宝价12.1</p>
              <p style="height: 30px;line-height: 15px;">
                <span style="color: #FF0279;font-size: 12px;padding-left: 5px">券后</span>
                <span style="color: #FF0279;font-size: 16px;padding-left: 5px">¥12.1</span>
                <span style="color: #CCCCCC;font-size: 12px;float: right;margin-right: 5px;">月销1.2万</span>
              </p>
            </div>
          </li>
        </ul>
      </swiper-item>
    </swiper>
    <Card @fetch-index="clickIndexNav" :selectNavIndex="selectNavIndex"></Card>
  </div>
</template>

<script>
  import CardHeader from '@/components/CardHeader'
  import Card from '@/components/card'
export default {
  data () {
    return {
      top:0,//头部距离设置
      scrolltop:0,//小分类距离
      selectNavIndex: 0,
      btnText: "首页",
      //头部大分类
      headerchoose: 0,
      // 轮播参数
      swiperParams: {
        indicatorDots: true,
        autoplay: true,
        interval: 5000,
        duration: 900,
        circular: true
      },
      // 页面混动
      currentTab: 0,//分类点击下表
      scrollLeft: 0,//小分类滚动距离
      isFixed: false,
      navList: [{
        name: '精选'
      },{
        name: '女装'
      },{
        name: '男装'
      },{
        name: '美妆'
      },{
        name: '母婴'
      },{
        name: '零食'
      },{
        name: '酒类'
      },{
        name: '酒类'
      },{
        name: '酒类'
      },{
        name: '酒类'
      },{
        name: '酒类'
      }],
      topHeight: 0 //页面固定
    }
  },
  methods: {
    headerClick (headerindex) {
      this.headerchoose = headerindex
    },
    tabClick (index) {
      this.eady()
      this.currentTab = index
    },
    switchTab (e) {
      console.log(e.mp.detail.current)
      this.eady()
      this.currentTab = e.mp.detail.current
    },
    eady () {
      const _this = this
      const query = wx.createSelectorQuery()
      query.selectAll('.tabbar').boundingClientRect()
      query.exec(function (res) {
        var num = 0
        for (var i=0;i<_this.currentTab;i++) {
          num+=res[0][i].width
        }
        _this.scrollLeft = Math.ceil(num)
      })
    },
    // 获取节点高度
    getHeight (e) {
      const _this = this
      // console.log(e.scrollTop)
      var query = wx.createSelectorQuery()
      query.select('.modcontent').boundingClientRect(function(res) {
        // console.log(res[0].top)
        if (e.scrollTop>res.top) {
          _this.isFixed = true
          _this.scrolltop = _this.top + 34
        } else {
          _this.isFixed = false
        }
      }).exec()
    },
    getTop () {
      const _this = this
      wx.getSystemInfo({
        success: (res) => {
          _this.top = res.statusBarHeight + 46
        }
      })
    }
  },
  components: {
    Card,
    CardHeader
  },
  onLoad () {
    this.getTop()
  },
  onShow () {
  },
  created () {
  },
  onPageScroll (e) {
    this.getHeight(e)
  }
}
</script>

<style scoped>
  .headerType{
    height: 30px;width: 100%;padding-top:8px;background: white;position: fixed;z-index: 999999999999999999999999
  }
  /*.header1{*/
    /*height: 30px;width: 100%;background: white;position: fixed;z-index: 999999999999999999999999*/
  /*}*/
  .headertabs{
    width: 70%;
    height: 100%;
    margin: 0 auto;
    /*background: pink;*/
    display: flex;
  }
  .headertabs .item_tab{
    flex: 1;
    text-align: center;
    letter-spacing: 1px;
    line-height: 30px;
    position: relative;
  }
  .headertabs .item_tab .line{
    width: 70%;
    height: 100%;
    position: absolute;
    left: 50%;
    bottom: 1px;
    margin-left: -35%;
    -webkit-font-smoothing: antialiased;
  }
  .active{
    color: #FF0038!important;
    border-bottom: 3px solid #FF0038!important;
  }
  /*搜索框*/
  .search{
    padding-left: 12px;
    padding-right: 12px;
    background: white;
    padding-top: 16px;
    padding-bottom: 15px;
    position: relative;
  }
  .search input{
    width: 100%;
    height: 32px;
    background: #F3F4F5;
    border-radius: 50px;
    text-align: center;
    color: #999999;
    font-size: 14px;
    letter-spacing: 1px;
  }
  .search img{
    width: 14px;
    height: 14px;
    position: absolute;
    top: 50%;
    margin-top: -7px;
    left: 25%;
  }
  .sliderimg{
    height: 125px;
    width: 100%;
    border-radius:5px;
    padding-bottom: 10px;
  }
  /*广播*/
  .vioce{
    height: 23px;
    padding-left: 12px;
    margin-top: 15px;
    overflow: hidden;
    position: relative;
  }
  .vioce ul{
    position: absolute;
  }
  .vioce ul li{
    letter-spacing: 1px;
    color: #FF0038;
    font-size: 16px;
    height: 23px;
    line-height: 23px;
  }
  .vioce ul{
    -webkit-animation: slider 4s linear infinite;
  }
  @-webkit-keyframes slider{
    5% {top: 0px;}
    15% {top: -23px;}
    30% {top: -46px;}
    45% {top: -69px;}
    60% {top: -69px;}
    75% {top: -46px;}
    90% {top: -23px;}
    100% {top: 0px;}
  }
  .vioce ul li span{
    font-weight: bold;
    padding-left: 10px;
  }
  .vioce img{
    height: 23px;
    position: absolute;
    /*z-index: 9999999999;*/
  }
  /*数据列表*/
  .top{
    width: 100%;
    text-align: center;
    /*line-height: 42px;*/
    white-space: nowrap;
    background: #fff;
    margin-top: 20px;
    border-bottom: 1px solid #EBEBEB;
    border-radius: 10px 10px 0 0;
    /*margin-left: 90px;*/
  }
  .tabbar{
    padding: 0px 12px;
    height: 45px;
    font-size: 16px;
    line-height: 45px;
    padding-bottom: 3px!important;
    /*height: 42px;*/
    display: inline-block;
    color: #999999;
    position: relative;
    letter-spacing: 1px;
    /*font-weight: bold;*/
  }
  .tabbar .line{
    position: absolute;
    width: 30px;
    height: 3px;
    background: #FF0038;
    bottom:0px;
    left: 50%;
    margin-left: -15px;
  }
  .activetab{
    color: #FF0038!important;
    font-weight: bold;
  }
  /*价格销量选择*/
  .choosetype{
    width: 100%;
    height: 41px;
    background: white;
    display: flex;
    line-height: 41px;
  }
  .choosetype div{
    flex: 1;
    text-align: center;
    letter-spacing: 1px;
    color: #333333;
    font-size: 14px;
    position: relative;
  }
  .choosetype div img{
    position: absolute;
    top: 50%;
    margin-top: -6px;
    margin-left: 10px;
  }
  .fixedpost{
    position: fixed!important;
    width: 100%!important;
    z-index: 9999999999!important;
    margin-top: 0px!important;
    border-radius: 0px!important;
  }
  .slide-image{
    height: 100%;
    width: 100%;
  }

  .swipercontent{
    width: 100%;
    display: flex;
    flex-wrap: wrap;
  }
  .swipercontent li{
    width: 50%;
    height: 279px;
    /*background: pink;*/
    position: relative;
    margin-top: 10px;
  }
  .swipercontent li .imgbg{
    width: 90%;
    height: 279px;
    background: white;
    margin: 0 auto;
    border-radius: 10px;
  }
  .swipercontent li .imgbg img{
    width: 100%;
    height: 170px;
    border-radius: 10px 10px 0px 0px;
  }
  .discon{
    width: 90%;
    height: 109px;
    /*background: red;*/
    position: absolute;
    bottom: 0px;
    left: 50%;
    margin-left: -45%;
    border-radius: 0px 0px 10px 10px;
  }
  .discon .headerimg{
    height: 15px;
    width: 15px;
    vertical-align: middle;
    float: left;
    padding-left: 5px;
  }
  .discon .name{
    color: #333333;
    font-size: 14px;
    letter-spacing: 1px;
    padding-left: 5px;
    vertical-align: middle;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 1;
    overflow: hidden;
  }
  .taobaoprice{
    letter-spacing: 1px;
    color: #CCCCCC;
    font-size: 12px;
  }
</style>
