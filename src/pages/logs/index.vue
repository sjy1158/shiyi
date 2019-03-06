<template>
  <div>
    <div class="firstcontent">
      <header class="contentbg">
        <img src="http://192.168.2.23/Maskbg.png" alt="" style="width: 100%;height: 180px;">
        <!--自定义header-->
        <div class="location" :style="{height:height+'px',lineHeight:(height+15)+'px'}">
          <img src="/static/logs/location.png" alt="" style="width: 14px;height: 20px;" class="locationimg">
          <span style="margin-left: 32px;letter-spacing: 1px" class="localtext">本地生活</span>
          <input type="text" placeholder="搜索">
        </div>
        <div class="place" :style="{top:height+'px'}">
          <div>杭州</div>
          <div style="width: 18px;height: 3px;border-radius: 5px;background: white;margin: 10px auto"></div>
          <div>多云 7-16°C</div>
        </div>
        <!--&lt;!&ndash;列表数据&ndash;&gt;-->
        <scroll-view scroll-x="true" class="top" :scroll-left="scrollLeft" scroll-with-animation="true">
          <div class="tabbarname" :class="activeNav==index?'activeNav':''" :key="index" v-for="(item,index) in navList" @click="tabbarClick(index)">
            {{item.name}}
          </div>
        </scroll-view>
        <!--自定义headerending-->
      </header>

      <!--<div style="height: 800px;width: 100%;background: gray;position: relative;z-index: 99">-->
        <!--<div></div>-->
      <!--</div>-->
    </div>

    <!--<div style="height: 800px;width: 100%;background: rgba(255,255,255,0);position: relative">-->

      <!--<div style="width: 100%;height: 500px;position: absolute;top: 200px;background: white"></div>-->
    <!--</div>-->
    <Card @fetch-index="clickIndexNav" :selectNavIndex="selectNavIndex"></Card>
  </div>
</template>

<script>
  import Card from '@/components/card'
export default {
  data () {
    return {
      selectNavIndex: 1,
      // 分类滚动
      height: 0,//初始化高度
      scrollLeft: 0,//小分类滚动距离
      activeNav: 0,
      navList: [{
        name: '推荐'
      },{
        name: '宝龙城'
      },{
        name: '万象城'
      },{
        name: '龙湖滨江天街'
      },{
        name: '华润万家'
      },{
        name: '宝龙城'
      },{
        name: '万象城'
      },{
        name: '龙湖滨江天街'
      },{
        name: '华润万家'
      }]
    }
  },
  methods: {
    tabbarClick (index) {
      this.activeNav = index
      this.eady()
    },
    eady () {
      const _this = this
      const query = wx.createSelectorQuery()
      query.selectAll('.tabbarname').boundingClientRect()
      query.exec(function (res) {
        var num = 0
        for (var i=0;i<_this.activeNav;i++) {
          num+=res[0][i].width
        }
        _this.scrollLeft = Math.ceil(num) - 30
      })
    },
  },
  components: {
    Card
  },
  onLoad () {
    const _this = this
    wx.getSystemInfo({
      success: (res) => {
        console.log(res)
        _this.height = res.statusBarHeight + 46
      }
    })
  },
  created () {
  }
}
</script>

<style>
  .firstcontent{
    height: 416px;
    width: 100%;
    top: 0px;
    background-image:url("http://192.168.2.23/localbg.png");
    background-size: 100% 100%;
    background-repeat: no-repeat;
    background-attachment:fixed;
  }
  /*头部*/
  .contentbg{
    position: fixed;
    top: 0px;
    height: 206px;
    width: 100%;
    z-index: 100;
    background: rgba(255,255,255,0);
  }
  .contentbg .loaclbg{
    height: 100%;
    width: 100%;
  }
  .location{
    width: 100%;
    /*background: pink;*/
    position: absolute;
    top: 0px;
  }
  .locationimg{
    position: absolute;
    top:50%;
    left: 13px;
    vertical-align: middle;
    /*margin-top: -10px;*/
  }
  .localtext{
    color: #FFFFFF;
    font-size: 18px;
    vertical-align: middle;
  }
  .location input{
    width: 121px;
    height: 32px;
    position: absolute;
    top: 65%;
    margin-top: -16px;
    background: rgba(255,255,255,0.5);
    letter-spacing: 1px;
    color: #999999;
    font-size: 14px;
    text-align: center;
    left: 50%;
    margin-left: -60.5px;
    border-radius: 50px;
  }
  .place{
    width: 100%;
    height: 100px;
    /*background: pink;*/
    position: absolute;
    text-align: center;
  }
  .place div{
    color: white;
  }
  .place div:first-child{
    font-size: 36px;
    letter-spacing: 1px;
    margin-top: 7px;
  }
  .place div:nth-child(3){
    color: #FFFFFF;
    font-size: 12px;
    letter-spacing: 1px;
  }
  /*tabbar小分类*/
  .top{
    width: 100%;
    text-align: center;
    white-space: nowrap;
    /*background: #fff;*/
    /*border-bottom: 1px solid #EBEBEB;*/
    position: absolute;
    bottom: 0px;
  }
  .tabbarname{
    font-weight: bold;
    color: #FFFFFF;
    padding: 0px 12px;
    height: 22px;
    font-size: 16px;
    line-height: 22px;
    padding-bottom: 3px!important;
    /*height: 42px;*/
    display: inline-block;
    position: relative;
    letter-spacing: 1px;
    /*font-weight: bold;*/
  }
  /*选择到的样式*/
  .activeNav{
    font-size: 23px!important;
    font-weight: bold;
  }
</style>
