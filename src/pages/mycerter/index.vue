<template>
  <div style="background: #F3F4F5;position: relative;height: 100%;width: 100%;">
    <div class="mod1" :style="{height:height+'px'}">
      <div class="mod1header" :style="{height: height + 'px',lineHeight: lineHeight + 'px'}">
        券十一
      </div>
    </div>

    <div class="mod2" :style="{marginTop:height+'px'}">
      <div class="mod2header" :style="{height:(216-height)+'px'}">
        <!--头部头像-->
        <div class="headerimg">
          <!--头像部分-->
          <div class="touxiangcontent">
            <div class="touxiang">
              <img src="http://192.168.2.23/Maskbg.png" alt="">
            </div>
          </div>
          <!--头像endding-->

          <div class="nickname" style="color: white;margin-left: 10px;">
            <p>
              <span>Kaxim</span>
              <img src="/static/mycenter/huangguan.png" alt="" style="width: 20px;height: 15px;margin-left: 5px;">
              <span style="margin-left: 5px;font-size: 12px;">VIP</span>
            </p>
            <p style="margin-top: 7px;">
              <span style="font-size: 14px;">邀请码：AF21C46D</span>
              <span style="padding: 1px 5px;border: 1px solid white;font-size: 14px;border-radius: 50px;letter-spacing: 2px;margin-left: 17px;">复制</span>
            </p>
          </div>

          <img src="/static/mycenter/bangding.png" alt="" style="width: 76px;height: 25px;position: absolute;right: 0px;">
          <!--昵称ending-->
        </div>

        <div class="price">
          <div class="contentprice" style="color: white">
            <span style="font-size: 14px;vertical-align: middle;padding-top: 8px;">账户余额</span>
            <span style="font-size: 24px;vertical-align: middle;padding-left: 13px;">¥3.468.66</span>
            <div style="margin-top:3px;background: white;letter-spacing: 5px;color: #FF0038;font-size: 14px;border-radius: 50px;vertical-align: middle;width: 75px;height: 25px;float: right;text-align: center;line-height: 25px;">提现</div>
          </div>
        </div>
        <!--头部头像ending-->
      </div>
    </div>

    <div class="mod3">
      <div class="mod3content">
        <div style="width: 3px;height: 28px;background: #EBEBEB;position: absolute;left: 50%;margin-left: -1.5px;top: 50%;margin-top: -14px;"></div>
        <div>
          <span>本月预估奖励</span>
          <!--<img src="/" alt="">-->
        </div>
        <div>
          ¥3.468.66
        </div>
      </div>
    </div>

    <div class="mod4">
      <div class="mod4content">
        <div style="padding-left: 15px;padding-right: 15px;">
          <div style="width: 100%;height: 40px;border-bottom: 1px solid #EBEBEB;line-height: 40px;color: #666666;font-size: 14px;letter-spacing: 1px;">订单管理</div>
        </div>
        <div class="tabcontent">
          <div>
            <img src="/static/mycenter/Oval.png" alt="">
            <p>本地生活</p>
          </div>
          <div>
            <img src="/static/mycenter/Oval2.png" alt="">
            <p>拼多多</p>
          </div>
          <div>
            <img src="/static/mycenter/Oval3.png" alt="">
            <p>京东</p>
          </div>
          <div>
            <img src="/static/mycenter/Oval4.png" alt="">
            <p>蘑菇街</p>
          </div>
        </div>
      </div>
    </div>

    <div class="mod5">
      <ul>
        <li>
          <img src="/static/mycenter/yqr.png" alt="">
          <span>我的邀请人</span>
        </li>
        <li>
          <img src="/static/mycenter/kf.png" alt="">
          <span>在线客服</span>
        </li>
      </ul>
    </div>

    <div class="mod5" style="margin-bottom: 70px;">
      <ul>
        <li>
          <img src="/static/mycenter/bb.png" alt="">
          <span>当前版本</span>
        </li>
      </ul>
    </div>

    <Card @fetch-index="clickIndexNav" :selectNavIndex="selectNavIndex"></Card>
  </div>
</template>

<script>
  import Card from '@/components/card'
export default {
  data () {
    return {
      selectNavIndex: 2,
      height: 0, //设置头部高度
      lineHeight: 0
    }
  },
  components: {
    Card
  },
  methods: {
    getHeader () {
      const _this = this
      wx.getSystemInfo({
        success: (res) => {
          _this.height = res.statusBarHeight + 46
          _this.lineHeight = _this.height + res.statusBarHeight
        }
      })
    }
  },
  created () {
  },
  onLoad () {
    this.getHeader()
  }
}
</script>

<style>
  .mod1{
    width: 100%;
    position: fixed;
    top: 0px;
    Z-index: 99999999;
    background:-webkit-linear-gradient(left,#FF0038,#FF436C);/* Safari 5.1 - 6.0 */
    background:-o-linear-gradient(left,#FF0038,#FF436C);/* Opera 11.1 - 12.0 */
    background:-moz-linear-gradient(left,#FF0038,#FF436C);/* Firefox 3.6 - 15 */
    background:linear-gradient(to left,#FF0038,#FF436C);/* 标准*/
  }
  .mod1 .mod1header{
    width: 100%;
    /*background: black;*/
    position: fixed;
    top: 0px;
    color: white;
    text-align: center;
    letter-spacing: 1px;
  }
  .mod2{
    width: 100%;
    height: auto;
    margin-top: 66px;
  }
  .mod2 .mod2header{
    width: 100%;
    background:-webkit-linear-gradient(left,#FF0038,#FF436C);/* Safari 5.1 - 6.0 */
    background:-o-linear-gradient(left,#FF0038,#FF436C);/* Opera 11.1 - 12.0 */
    background:-moz-linear-gradient(left,#FF0038,#FF436C);/* Firefox 3.6 - 15 */
    background:linear-gradient(to left,#FF0038,#FF436C);/* 标准*/
  }
  .mod2 .headerimg{
    height:60px;
    width: 100%;
    position: relative;
    /*background: pink;*/
  }
  .mod2 .touxiangcontent{
    width: 60px;
    height: 60px;
    background: rgba(255,255,255,0);
    border-radius: 50%;
    margin-left: 13px;
    border: 2px solid white;
    float: left;
  }
  .mod2 .touxiangcontent .touxiang{
    height: 56px;
    width: 56px;
    background: white;
    border-radius: 50%;
    margin-top: 3px!important;
    margin-left: 3px;
  }
  .mod2 .touxiangcontent .touxiang img{
    height: 100%;
    width: 100%;
    border-radius: 50%;
  }
  .nickname {
    height: 100%;
    width: 60%;
    /*background: green;*/
    float: left;
  }

  .price{
    margin-top: 17px;
    padding-left: 21px;
    padding-right: 21px;
  }
  .contentprice{
    width: 100%;
    height: 33px;
    /*background: pink;*/
  }
  .mod3{
    padding-left: 11px;
    padding-right: 11px;
  }
  .mod3 .mod3content{
    width: 100%;
    height: 49px;
    border-radius: 10px;
    background: white;
    margin-top: -20px;
    display: flex;
    position: relative;
  }
  .mod3 .mod3content div{
    flex: 1;
    text-align: center;
    line-height: 49px;
  }
  .mod3 .mod3content div:nth-child(2){
    font-size: 14px;
    color: #333333;
    letter-spacing: 1px;
  }
  .mod3 .mod3content div:nth-child(3) {
    color: #FF0038;
    font-size: 21px;
    letter-spacing: 1px;
  }
  .mod4{
    padding-left: 11px;
    padding-right: 11px;
    margin-top: 10px;
  }
  .mod4 .mod4content{
    height: 151px;
    width: 100%;
    background: white;
    border-radius: 10px;
  }
  .tabcontent{
    display: flex;
  }
  .tabcontent div{
    flex: 1;
    text-align: center;
    color: #333333;
    font-size: 14px;
    letter-spacing: 1px;
  }
  .tabcontent div img{
    width: 35px;
    height: 35px;
    border-radius: 50%;
    margin-top: 20px;
  }
  .tabcontent div p{
    margin-top: 10px;
  }
  .mod5{
    padding-left: 17px;
    background: white;
    height: auto;
    margin-top: 10px;
  }
  .mod5 ul{
    height: auto;
    width: 100%;
  }
  .mod5 ul li{
    height: 60px;
    width: 100%;
    line-height: 60px;
    border-bottom: 1px solid #EBEBEB;
  }
  .mod5 ul li img{
    height: 20px;
    width: 20px;
    vertical-align: middle;
  }
  .mod5 ul li span{
    margin-left: 8px;
    vertical-align: middle;
    color: #333333;
    font-size: 14px;
    letter-spacing: 1px;
  }
</style>
